---
title: 'Ingrid as an intentional language'
last_modified_at: 2021-03-12T08:52:02-05:00
categories:
  - patterns-and-syntax
  - methodology
tags:
  - project
  - ingrid
comments_id: 6
classes: wide
---

```javascript
Ingrid is
  a very simple idea
  += a very simple syntax
  == a very complex language
```

Ingrid is a new kind of programming language that weaves programmable intentionality into a succinct spreadsheet methodology to create a powerful, expressive, and fun development experience.

## It starts with a very simple idea

...and an old one: capture high-level intentionality in a declarative style and let the system work out how to implement it. We have HTML and CSS and countless kinds of YAML-inspired declarative tools that do the heavy lifting behind simple declarative instructions. The key to each of these languages is a consistent syntax in a tightly focused domain that allows you just enough freedom to get the job done.

## It has a very simple syntax

Ingrid syntax expresses two intertwined ideas: selectors and intentions. Selectors select intentions and intentions select selectors. This circular arrangement promotes a very succinct description of programmed intentionality.

Two statements, two intentions, and two selectors:

```javascript
    A1 is 10
    B1 == A1 * 5
```

This is a very small Ingrid application. Intentionality is expressed through a spreadsheet-like syntax and this works very well - when all of your problems are spreadsheet shaped.

Historically, people have used spreadsheets to solve a whole range of problems that are not so obviously spreadsheet-oriented. And yet this simple `cell == formula` arrangement has proved very adept at capturing this kind of mismatched intentionality at the expense of cumulative complexity. But Ingrid is not a spreadsheet language. It is a general-purpose programming language that happens to use this methodology as a basis for programming intentionality.

## A very complex language

General-purpose programming languages deal with complexity through abstraction. Each has its own take on how to deliver abstraction, and each levies its own kind of tax on the inevitable [abstraction leakage](https://en.wikipedia.org/wiki/Leaky_abstraction). Ingrid handles abstraction through selectors and intentions and levies its own tax in the form of granular intentionality.

In order to maximize Ingrid productivity, one needs to understand the concepts of granular intentionality, semantic markers, and rationalized agreement. These are not necessarily complicated arguments in themselves, but they do require a bit of grounding in common sense and objectivity, and no doubt, an open mind towards a new approach to problem-solving in the eternal quest for the [silver bullet](https://en.wikipedia.org/wiki/No_Silver_Bullet).

## Experimental

Ingrid is part of an ongoing [intentional-dev](http://intentional-dev.com) research program and as such is not anywhere near ready for production. But it _is_ kind of fun to play around with some of the ideas of applied intentionality such as rationalization, agreement, and semantic markers.

## Selectors and intentions

Selectors and intentions are the building blocks of applied intentionality. Here are some selectors, and here are some intentions. Does intentionality arise from the intentions themselves, or from the selectors? What do you think?

```javascript
A1 is 10
B1 is console.log(A1 * 5) // 50
```

## Rational behavior

You can rationalize about something you do not fully understand and still come to a useful conclusion. What is the intention of the following code? Does it exhibit expected behavior?

```javascript
spreadsheet {
  A1 is 10
  B1 == A1 * 5
}
```

## Agreement

The converse of rational behavior is of course irrational behavior. But that phrase has many connotations that are not appropriate to software development. In the constrained terminology of applied intentionality, there is only rationalization. A failure to rationalize an intentionality is simply a failure to reach agreement. Agreement with the owner of the software, or the developer, or even agreement throughout the team, is established in Ingrid through correlated agreement at the code level.

You'll need to do a bit of rationalizing of your own before we can reach agreement over what this code is doing.

```javascript
TicTacToe is spreadsheet {
  board:A1..C3 {
    cell is turn after click and empty
  }
  A4 is ‘player:’ C4 == turn
  A5 is ‘winner:’ C5 == winner

  turn is X
    is O after board and turn=X
    is X after board and turn=O

  fullLine* == turn,turn,turn

  winner is turn after fullLine =
   board.row(1,2,3)
    or board.col(A,B,C)
    or board.cells(A1,B2,C3)
    or board.cells(A3,B2,C1)
}
```

## Semantic markers

Ingrid code is the application of agreed intentionality. And when agreement has not been established, then the code is not finished. But what happens when agreement over intentionality has already been reached before all of the code has been delivered? Is the code finished in this next example?

```javascript
todo is html {
  body {
    header {
      input#todo is "" after list, cancel
      button#ok
      button#cancel
    }

    main {
      list
        += item(todo) after ok
        += item after update
        -= item after remove

      #items == select(list, filter)

      item {
        input
        button#update
        button#remove
      }
    }

    footer {
      #done == count(list, done)
      #todo == list.count - done
      checkbox#filter is done, todo
    }
  }
}
```

There is nowhere near enough surface detail to run this application in a browser and yet here it is, presented as a complete and operational web page application. This is all down to semantic markers (an aspect of applied intentionality still very much in flux).

Semantic markers (SMs) are recognizable patterns of coded intentionality that are semantically related to some third-party context. They are difficult to pin down because they could quite literally be anything. The whole application might be a semantic marker from the perspective of, say, somebody responsible for updating a source code repository.

The relevant SMs in this example include HTML markers. Third-parties relevant to this example include code reviewers with an HTML perspective, and the browser (suitably primed with a preloaded context). Both kinds of third-party will identify these SMs as relating to something like the following:

```
html/body html/body/header
html/body/header/input#todo
html/body/main
html/body/footer
...
```

Each of these kinds of intentionalities, marked by SMs establishes a semantic relationship between the code and a context and it captures a special kind of operational intentionality. The idea here is that SMs hold enough detail in context, code, and semantic grounding, for third-parties to fill in the missing parts.

## In conclusion

The examples of applied intentionality presented here highlight Ingrid's continued development towards a goal of AI augmented development. The ideal of third-party intentionality is for at least one of those parties to be AI generated, and to be trained to recognize and respond to semantic markers through the delivery of appropriately integrated code.

Just to round things off, Ingrid doesn't absolutely depend on semantically tipped off, artificially generated third-parties to fill in the boilerplate. It provides a granular abstraction mechanism that can be used to generate intentionally viable syntax. This is where all of the dirty code goes when you don't want it to muddy the surface intentionality. Strictly speaking, granular abstraction is just another kind of semantic marker where the [third-party context is provided by the language itself](), but you might simply prefer to think of it this way: Ingrid supports modules.

The following design level code could be included in any distribution where the browser is not expected to recognize the intentionality of the previous little todo app. I know, _how likely is that?_

```javascript
// design - probably in another module

item is tag item(input:value)

#items is tag section#items*

list is tag list*

select*(list*, filter:)
  is list if list.state = filter

count(list*, filter:)
  +=1 if list.state = filter
```
