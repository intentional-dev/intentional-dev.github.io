---
title: 'Ingrid for spreadsheet engineers'
last_modified_at: 2021-03-12T10:00:02-05:00
categories:
  - patterns-and-syntax
  - methodology
tags:
  - project
  - ingrid
comments_id: 7
classes: wide
---

All Ingrid statements have basically the same shape. They all start with a selector and end with a list of intentions. Selectors act a bit like cells and intentions act a bit like formulas. And this is where the notion of a spreadsheet methodology begins to form.

```javascript
A1 is 10
B1 == A1 * 2
```

If we need to print B1 in red, then we express this intentionally.

```javascript
A1 is 10
B1 == A1 * 2 is red
```

And if we only want it to be red when it is negative we would use:

```javascript
A1 is -10
B1 == A1 * 2 is red after B1 < 0
```

If we want the user to input the value at A1, we have to say so.

```javascript
A1 is input
B1 == A1 * 2 is red after B1 < 0
```

If we have a function that takes a value, we send a message to the function.

```javascript
A1 is input
B1 == maybeDebit(A1 * 2)

maybeDebit(amt:)
  is amt
  is red if amt < 0 else black
```

But selectors aren't really cells and intentions aren't really formulas. It’s just that they're designed to behave as if they were cells and formulae when rationalized from an intentional perspective. Which is to say: if it looks like a spreadsheet, then it's reasonable to assume that it behaves like one.

## Intentional programming

Ingrid’s spreadsheet methodology provides a baseline for increasingly complex problem domains, and the language provides some powerful syntax and built-in mechanisms for extending the scope of applied intentionality. For example, the rationality behind the spreadsheet methodology in the previous example can be strengthened by wrapping the code in a _spreadsheet_.

```javascript
spreadsheet {
  A1 is input
  B1 == maybeDebit(A1 * 2)

  maybeDebit(amt:)
    is amt
    is red if amt < 0 else black
}
```

This is rationality in the service of intentional programming. It does not constrain or test your assumptions explicitly but rather directs your observations and conclusions to an intentional goal. But this new methodology only works if it gains understanding and agreement between the parties. The `spreadsheet` intention might be supplied by a 3rd party library. In which case, the developer, the other party, would be obliged to refer to its documentation. Or, it might be developed in-house. In this case, understanding and agreement would emerge through iterative development. Ingrid supports empty intentions - `spreadsheet` can start empty and the compiler won’t complain - but they have intentionality nonetheless because they are established or evolutionary concepts in a shared understanding of the domain. Ingrid is designed to capture (and express) intentionality first and then implement it.
