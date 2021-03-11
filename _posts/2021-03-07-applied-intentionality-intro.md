---
title: 'Applied Intentionality - a new kind of Ai'
last_modified_at: 2021-03-11T16:20:02-05:00
categories:
  - ai
tags:
  - Ai
  - project
comments_id: 3
classes: wide
---

Applied Intentionality is the practical consideration of intentionality as it applies to machines and to the software that controls them. By allowing that machines have rational intentionality, we supplement the need to program them directly and open a channel of negotiation that existing and future AI technology can recognize and adapt to.

AI research has a lot to say and learn about how best to talk to machines. AI needs to talk, it needs to act, and it needs to have an opinion if it is to do useful work in the realm of human experience. And, since we have spent the last 60 or so years talking down to machines, constraining the very act of communication in an effort to avoid any ambiguity whatsoever, we have made little progress towards pragmatic communication. The central idea of this research program is to talk up to machines, to allow them intentionality, and to determine their behaviour by semantically filling in the gaps between what we have taught them to understand, and what we require them to do. The research projects outlined here explore this basic premise from different but interlocking perspectives.

In this article, Applied Intentionality is abbreviated as Ai to avoid confusion with AI, the recognized abbreviation of Artificial Intelligence.

## Tobe

Tobe is a machine language that aims to establish reliable communication between man and machine. It’s based on the premise that if all communication is undertaken in the third person, then information can always be constructed around the copular [to be](http://theseriousandthefrivolous.blogspot.com/2013/04/the-verb-to-be-in-different-languages.html). This is just a starting point for language disambiguation. But it allows for a deterministic system to know where to look for ancillary information even if it has no notion of what that information means. This kind of understanding is a common theme running through all of the research projects listed here.

Creating a machine language like Tobe is not a new idea. There is a lot of [prior](https://en.wikipedia.org/wiki/Attempto_Controlled_English) [art](https://en.wikipedia.org/wiki/ClearTalk) to be found under the umbrella of (controlled languages)[https://en.wikipedia.org/wiki/Controlled_natural_language]. This [one](https://en.wikipedia.org/wiki/E-Prime) is a particular favourite. But Tobe needs to be a fresh start so that it bends to the needs of Ai, and not the other way around. To begin with, Tobe is linguistic but language agnostic. It is designed so that it can be expressed in a host language but imposes its own syntax and semantic framework for statement construction. This will usually result in unnatural and verbose phrasing. In English for example, a simple instruction to count from 1 to 10 might be phrased:

` {party} is instructed will count is from 1 is to 10`

Which, even being generous, sounds a bit pidgin. For this reason, I use an imaginary dialect of Tobe called Tobe-en which allows me to apply whatever surface structure comes most naturally to the intention under scrutiny. When I write

count from 1 to 10

I invoke the deeper structure of pure Tobe. However, whether it be Tobe or Tobe-en, spoken or not, for machines to engage in a Tobe dialogue, there has to be an application somewhere in the mix, and that distinctive capability is reserved for Kalvin.

## Kalvin

Kalvin is a system-level application that uses a [non-deterministic classifier](https://www.jmlr.org/papers/volume10/delcoz09a/delcoz09a.pdf) approach to generate significant information that can be rationalized and applied in a granular context:

```
It's a dog
It's my dog!
It's Bengie and he’s holding his lead in his mouth!
What does this mean? (What could be the significance of all this?)
```

That’s the kind of problem Kalvin aims to solve, and that last line hints at the way it goes about it. It's the same kind of problem as:

```
It's a Web page.
It's my web page about Bengie!
When you click on “walkies”, it emits a barking sound!
What does this mean?
```

It's really just a matter of granularity but to Kalvin, these are problems of equal difficulty. In each case, the information is linguistic and typically context-sparse. Kalvin must apply the correct context, or at least an appropriate one, to arrive at the bigger picture. The work behind all of this is relatable to the disciplines of [ontology alignment](https://en.wikipedia.org/wiki/Ontology_alignment) and [semantic integration](https://en.wikipedia.org/wiki/Semantic_integration) but uses instead a reentrantly discoverable topology to represent intentional/semantic relationships.

Kalvin can’t actually speak Tobe yet. The objective is to have Kalvin learn Tobe through the manipulation and organization of its own internal knowledge representation. Early days. But it does have an API that can be used to read and write information directly from and to its processing channel. The kind of information that is exchanged through this API is a structure called a KLine (in homage to Marvin Minsky and his seminal work on theoretical [memory representation](http://courses.csail.mit.edu/6.803/pdf/aim-516.pdf), but bearing only a slight resemblance to that original concept). And the tool available to encode and decode KLines into a human readable format is called KalvinScript.

## KalvinScript (KS)

KalvinScript is a very lightly structured scripting system that encodes and decodes KLines. KS looks a lot like a programming language, except that it must always be remembered that Kalvin is not a compiler, or even a state machine in the usual sense. Kalvin has internal state (because it is an application) but this is a very private and volatile state, and not really conducive to overt rationalization. On the other hand, Kalvin’s API exposes its preference for significant input/output in simplistic linguistic terms. We can understand what is going on inside of Kalvin’s head by paying attention to the script:

```
(Mary had a little lamb - anything in brackets is a comment btw)
?MHALL => $SVO >
M = S(ubject)
	H = V(verb)
  ALL = O(bject) >
	  A = $D(et)
	  L = $M(od)
	  L = O
```

This little test script is not a definition of linguistic syntax (I know, it looks like it might be, what with subjects, objects, and verbs - that’s SVO right?). Actually, the script is laying out some context for future dialogue. It specifically states that Mary is the subject, Had is the verb, and so on. But this is a contextual interpretation. If Kalvin has no notion of SVO, then it has no notion of linguistic syntax order. The script is simply setting the scene. If we ask Kalvin: what did Mary have? Then the system would answer a little lamb without really understanding why it knows. Elsewhere on this site, I’ll often use the phrase a system knows what it knows, but it stops there. A system doesn't know what it doesn’t know, but it does know that it doesn’t know. (This kind of reasoning is based on a branch of logic called [autoepistemic logic](https://en.wikipedia.org/wiki/Autoepistemic_logic)).

## Ingrid

And then there was Ingrid - a true programming language that looks like a cross between KalvinScript and Tobe. In truth, Ingrid is the oldest development effort of all those listed here. It started off as a theoretical idealized language to investigate such questions as:

What is the minimum amount of coded information required to construct a fully functioning application?
How would the missing information be composed or otherwise aggregated into the solution?
How would such a solution, sans boilerplate, fare in a different domain?
And most importantly, how literate can the syntax be and still support all of the above?

Many decades of thought behind this, but only coded into an operational compiler very recently. Ingrid is a hot-bed test-bed for pragmatic application of Ai in a programmatic context.

Ingrid is stabilizing, but not ready for general programming tasks. Which is a pity, because it has some very unique features that build on the idea of agreed intentionality. At its core, Ingrid supports AI through its ultra-simple syntax - that looks a lot like Tobe in shackles - and its pragmatic ability to shape-shift and invent new syntax to capture challenging intentional patterns:

```
TicTacToe is grid {
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

Ingrid might be called an Intentional Language, I probably do refer to it in this way from time to time, but its heritage is not aligned with the earlier efforts of [Charles Simonyi](https://en.wikipedia.org/wiki/Intentional_programming). It has very much more to do with [IST](https://ase.tufts.edu/cogstud/dennett/papers/intentionalsystems.pdf) and Daniel Dennett's philosophical arguments concerning the [Intentional Stance](https://en.wikipedia.org/wiki/Intentional_stance). Hence the quote on the front page of this site links that philosophical idea to the concrete notion of Semantic Markers, which are an early Ai attempt to build a bridge capable of handling a two-way interchange of information between man and machine.

## Semantic Markers (SMs)

SMs evolved from the idea of Ingrid’s linguistic rather than semantic composability.
They are explicit, intentional units or patterns of syntax that do not in themselves generate useful behaviour, but instead mark off the semantic context that would be required to implement that behaviour.

Simple token based SMs align with more established principles of abstraction. The Ingrid statement:

`TicTacToe is {a kind of} grid`

brings the expected behaviour into lexical context, and, it is argued, establishes agreement over the intentionality of the statement. Similar abstractions in other languages would therefore qualify as tokenized SMs, but more convoluted pattern or feature derived SMs would be harder to identify outside of a language specifically designed to operate at this level of granularity. Nevertheless, these kinds of markers do occur in other languages. It's just that they do not directly target humans for interactive consideration:

```
// the React import statement + the presence of JSX is a marker
// for the Babel compiler to transpile this file into pure js
import React from “react”;
return props => <pre>{JSON.stringify(props)}</pre>;
```

If markers fail to be recognized by third-party participants, where ‘participant’ represents anybody developing, reviewing, or curating the code, then it also fails to be semantic. It’s just another bit of code; part of a bigger semantic picture. This is the point at which all Applied Intentionality research and development comes together. In the world of Ai, machines are another kind of participant and can be taught to engage in the same activities of developing, reviewing, and curating as human participants. They may excel at some activities and fall short of human efforts in other areas, but one aspect they already have an unquestionable advantage over us is pattern recognition. A soon to be initiated SM research project will focus on the learnability of SM recognition on a large corpus of Github open-source software, categorized and trained on a variable set of parameters including language, library, keywords, number of issues, number of dependencies, etc.

In summary, and in light of the ongoing developments through this research, Applied Intentionality, Ai, is the kind of AI that integrates with existing codebases, empowers people to talk to machines in a language that negotiates rather than instructs, allows that machines do have independent intentionality, and yet recognizes that intentional software is, in essence, the same as any other software.
