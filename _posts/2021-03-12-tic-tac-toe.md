---
title: 'A game of TicTacToe
'
last_modified_at: 2021-03-12T10:30:02-05:00
categories:
  - patterns-and-syntax
  - methodology
tags:
  - project
  - ingrid
comments_id: 8
classes: wide
---

TicTacToe (OXO) is a relatively simple game to describe intentionally. A board is drawn up as a 3x3 grid of squares. Two players, X and O, take turns to draw their respective marks into the empty squares, one at a time until a horizontal, vertical, or diagonal line of three X’s or three O’s is detected. Player X takes the first turn. The winner is the first player to get a full line.

Program development is an iterative process. This is especially true for team-driven development. A first pass iteration to capture the high-level intentions might translate this entry statement into Ingrid thus:

```javascript
TicTacToe {
  board is grid(3x3)
  turn is X
  fullLine is XXX or OOO
  winner
    is X after fullLine = XXX
    is O after fullLine = OOO
}
```

Development will iterate on this level of detail until full team agreement is reached. As a diligent member of team-me, I readily agree that it captures the overall intent of the application, if not the actual gameplay which is surely the core intent. So I know that this code will evolve.

Ok, time to iterate on gameplay. Player X draws an ‘X’ on the board. We’ll instigate this by clicking on the board and using that generated event to draw the mark in the clicked square. In Ingrid we need to enter the current player’s mark after the player has clicked on the board.

```javascript
TicTacToe {
  // replaced: board is grid(3x3)
  board is grid(3x3)
    is turn after click

  turn is X
  fullLine is XXX or OOO
  winner
    is X after fullLine = XXX
    is O after fullLine = OOO
}
```

`Turn` started off with player X’s mark, so an **X** is drawn on the board in the square just clicked by player `X`. Now we need to switch to the other player. This is after the current player has clicked on the board and after the board has been updated.

```javascript
TicTacToe {
  board is grid(3x3)
    is turn after click

  turn is X
    // added:
    is O after board and turn=X
    is X after board and turn=O

  fullLine is XXX or OOO
  winner
    is X after fullLine = XXX
    is O after fullLine = OOO
}
```

And so, `turn` now holds player O’s mark, and the gameplay continues; O, X, O,... At each turn, we should ensure that the selected square is empty. We can fix that. Probably should have caught this in the previous iteration but never mind.

```javascript
TicTacToe {
  board is grid(3x3)
    // replaced: is turn after click
    is turn after click and square.empty

  turn is X
    is O after board and turn=X
    is X after board and turn=O

  fullLine is XXX or OOO
  winner
    is X after fullLine = XXX
    is O after fullLine = OOO
}
```

Gameplay comes to a close when a full line is detected. But how might that be achieved? If we find it difficult to express intentionally, that’s a good indication that we need to consider the problem from the design stance. So far we have been able to express intentionality from the high-level perspective of the intentional stance. Third-party agreement has been established and maintained throughout the iterative development process (this is true for team-me at least).

Having a design stance perspective is just another way of saying that we need more up-front design. The initial game description at the head of this article is from the design stance, albeit in documented text form rather than Ingrid syntax, and from this we established high-level intentionality through early iteration. As stated in the design, a full line is any horizontal, vertical, or diagonal line of three X squares or three O squares. Squares belong to the board, and the board is a grid, and then the buck stops: what is a grid? What does it do and how does it do it? As a team, we could have discussed and explored this detail as part of the initial design stance. Or perhaps we already have a grid whose intentionality aligns with our requirements and that’s the grid that we are referring to. Or perhaps we chose to defer this design step allowing us to plan its development independently. That does seem to be where we are at right now.

All of these very different scenarios are decisions taken from the design stance, but each of them is represented in source code intentionally: `board is grid`. Ingrid allows, actually encourages, this degree of uncertainty. To Ingrid, a grid is just another intentionality like any other, and it applies the intentional stance to rationalize it this way:

- I understand that grid is a selector
- I understand that grid has selector intentionality (at least)
- Therefore I am able to rationalize grid

As team-me lead developer, I get to choose which scenario is most appropriate, and I’ve chosen the middle one: grid is an existing Ingrid component that conveniently fits our purpose. I will describe its intentionality now so that we can move on, but it will involve a little bit of retrospective engineering to bring our prevailing intentionality into line with the way grid actually works.

A grid consists of cells, aligned in rows and columns. Each cell is addressed through spreadsheet-like selectors A1, B3, etc, and cell groups through A1..C3, A..C, etc. This intentionality is reflected in the refactored source code, and it allows us to express the gameplay in a more _spreadsheet-like_ manner:

```javascript
// replaced: TicTacToe {
TicTacToe is grid {
  board:A1..C3 {
    cell is turn after click and empty
  }
  A4 is ‘player:’ C4 == turn
  A5 is ‘winner:’ C5 == winner

  turn is X
    is O after board and turn=X
    is X after board and turn=O

  // replaced: fullLine is XXX or OOO
  // winner
  //  is X after fullLine = XXX
  //  is O after fullLine = OOO
  fullLine* == turn,turn,turn
  winner is turn after fullLine =
    board.row(1,2,3)
    or board.col(A,B,C)
    or board.cells(A1,B2,C3)
    or board.cells(A3,B2,C1)
}
```

This shifts the idea of a grid up to the application. TicTacToe is now a `grid`, and it has a reserved board area for gameplay and a running state of play underneath. The winner is whoever gets a full line first.

Standard Ingrid syntax is designed to express intentionality without making any strong claims about the way it actually works. It is a lean and consistent syntax that sometimes - unfortunately - obscures the very intentions it is set down to represent. It is a curious feature of the language that using standard syntax is discouraged wherever it compromises a shared understanding of intentionality. Standard syntax is called level-0 syntax and is the level at which compilers and interpreters translate intentions into executable code. TicTacToe is mostly level-0 syntax, but some level-1 and even level-2 syntax has cropped up in the spirit of intentionality. And so I will briefly expand on them here because each represents a pragmatic approach to Ingrid system development and highlights how a team might choose to work with and apply intentionality.

- The line `fullLine* == turn,turn,turn` is level-1 syntax.
- The line with `A1..C3` is level-2 syntax.

Ingrid provides level-1 syntax out of the box. Level-1 is syntax sugar for some level-0 constructions that potentially obscure intentionality through verbosity and operational noise. The TicTacToe statement `fullLine* == turn,turn,turn` is level-1 sugar for `fullLine* is turn,turn,turn after turn`. Both statements express, and code, the same intent: collate the current value of turn three times after the next turn, but this developer deemed the level-0 version slightly too distracting. In a real project, level-1 syntax might be considered the minimum competency expected of each team member. This low entry bar has many advantages but it is by no means mandatory. An experienced team could adopt a methodology that expresses all surface intentionality at level-0 whilst engaging the full semantic power of the language to abstract implementational boilerplate. For example, the level-1 `fullLine*` statement still has a problem with the way it expresses intentionality for anybody not conversant with Ingrid’s terse quantifier syntax. A level-0 intention could abstract this detail so that a clearer fullLine is turn,turn,turn can be implied with the cost of such rationalization diverted into the underlying implementation of fullLine.

The syntax `A1..C3` denotes a range operator, in this case it's a spreadsheet shorthand for A1, A2, A3, B1, and so on up to C3. But Ingrid does not support the range operator at level-0. This syntax has been introduced by the grid component at level-2. In situations such as this, a third-party observer (that’s anybody reading the source) must apply the intentional stance in order to rationalize such a statement in the context of prevailing intentionality. Grid wants to behave like a spreadsheet, and we have spreadsheet-like intentions. If that already works for you, then you have usefully extended the target domain to _behave like a grid_. This is the cost of level-2 intentionality, it introduces new behavior into the domain. You have to understand grid behaviour and agree that it is the right fit for TicTacToe. Otherwise it’s iteration time. Show me how _you_ think a grid should behave.
