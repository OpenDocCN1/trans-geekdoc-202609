
an-fsm)

According to the design recipe, the handler must consume a state of the world and a KeyEvent, and it must produce the next state of the world. This articulation of the signature in plain words also guides the design of examples. Here are the first two:

```
(check-expect
(find-next-state (make-fs fsm-traffic "red") "n")
(make-fs fsm-traffic "green"))
(check-expect
(find-next-state (make-fs fsm-traffic "red") "a")
(make-fs fsm-traffic "green"))
```

The examples say that when the current state combines the fsm-traffic machine and its "red" state, the result combines the same FSM with "green", regardless of whether the player hit "n" or "a" on the keyboard. Here is one more example:

```
(check-expect
(find-next-state (make-fs fsm-traffic "green") "q")
(make-fs fsm-traffic "yellow"))
```

Interpret the example before reading on. Can you think of another one?

Since the function consumes a structure, we write down a template for structures processing:

```
(define (find-next-state an-fsm ke)
(... (fs-fsm an-fsm) .. (fs-current an-fsm) ...))
```

Furthermore, because the desired result is a SimulationState.v2, we can refine the template with the addition of an appropriate constructor:

```
(define (find-next-state an-fsm ke)
(make-fs
... (fs-fsm an-fsm) ... (fs-current an-fsm) ...))
```

The examples suggest that the extracted FSM becomes the first component of
the new SimulationState.v2 and that the function really just needs to compute the
next state from the current one and the list of Transitions that make up the given
FSM. Because the latter is arbitrarily long, we make up a wish—a find function
that traverses the list to look for a Transition whose current state is (fs-current an-fsm)—and finish the definition:

```
(define (find-next-state an-fsm ke)
(make-fs
(fs-fsm an-fsm)
(find (fs-fsm an-fsm) (fs-current an-fsm))))
```

Here is the formulation of the new wish:

```
; FSM FSM-State -> FSM-State
; finds the state representing current in transitions
; and retrieves the next field
(check-expect (find fsm-traffic "red") "green")
(check-expect (find fsm-traffic "green") "yellow")
(check-error (find fsm-traffic "black")
"not found: black")
(define (find transitions current)
  current)
```

The examples are derived from the examples for find-next-state.

Stop! Develop some additional examples, then tackle the exercises.

## Exercise 228. Complete the design of find.

Once the auxiliary functions are tested, use simulate to play with fsm-traffic and the BW Machine from exercise 227.

Our simulation program is intentionally quite restrictive. In particular, you
cannot use it to represent FSMs that transition from one state to another
depending on which key a player presses. Given the systematic design, though,
you can extend the program with such capabilities.

## Exercise 229. Here is a revised data definition for Transition:

```
(define-struct ktransition [current key next])

; A Transition.v2 is a structure:
;   (make-ktransition FSM-State KeyEvent FSM-State)
```

Represent the FSM from Transition.v2s; ignore errors and final states.

Modify the design of simulate so that it deals with keystrokes in the appropriate manner now. Follow the design recipe, starting with the adaptation of the data examples.

Use the revised program to simulate a run of the FSM from exercise 109 on the following sequence of keystrokes: "a", "b", "b", "c", and "d".

Finite state machines do come with initial and final states. When a program that “runs” an FSM reaches a final state, it should stop. The final exercise revises the data representation of FSMs one more time to introduce these ideas.

## Exercise 230. Consider the following data representation for FSMs:

```
(define-struct fsm [initial transitions final])
(define-struct transition [current key next])
; An FSM.v2 is a structure:
;   (make-fsm FSM-State LOT FSM-State)
; A LOT is one of:
; -- '()
; -- (cons Transition.v3 LOT)
; A Transition.v3 is a structure:
;   (make-transition FSM-State KeyEvent FSM-State)
```

Represent the FSM from exercise 109 in this context.

Design the function fsm-simulate, which accepts an FSM.v2 and runs it on a player’s keystrokes. If the sequence of keystrokes forces the FSM.v2 to reach a final state, fsm-simulate stops. Hint The function uses the initial field of the given fsm structure to track the current state.

Note on Iterative Refinement These last two projects introduce the notion of “design by iterative refinement.” The basic idea is that the first program implements only a fraction of the desired behavior, the next one a bit more, and so on. Eventually you end up with a program that exhibits all of the desired behavior, or at least enough of it to satisfy a customer. For more details, see chapter 20. End

## 13 Summary

This second part of the book is about the design of programs that deal with arbitrarily large data. As you can easily imagine, software is particularly useful when it is used on information that comes without prespecified size limits, meaning “arbitrarily large data” is a critical step on your way to becoming a real programmer. In this spirit, we suggest that you take away three lessons:

- 1. This part **refines the design recipe** to deal with self-references and cross-references in data definitions. The occurrence of the former calls for the design of recursive functions, and the occurrence of the latter calls for auxiliary functions.

- 2. Complex problems call for a **decomposition** into separate problems. When you decompose a problem, you need two pieces: functions that solve the separate problems and data definitions that compose these separate solutions into a single one. To ensure that the composition works after you have spent time on the separate programs, you need to formulate your “wishes” together with the required data definitions.

A decomposition-composition design is especially useful when the problem statement implicitly or explicitly mentions auxiliary tasks, when the coding step for a function calls for a traversal of an(other) arbitrarily large piece of data, and—perhaps surprisingly—when a general problem is somewhat easier to solve than the specific one described in the problem statement.

- 3. **Pragmatics matter.** If you wish to design big-bang programs, you need to understand its various clauses and what they accomplish. Or, if your task is to design programs that solve mathematical problems, you had better make sure you know which mathematical operations the chosen language and its libraries offer.

While this part mostly focuses on lists as a good example of arbitrarily large data —because they are practically useful in languages such as Haskell, Lisp, ML, Racket, and Scheme—the ideas apply to all kinds of such data: files, file folders, databases, and the like.

Part IV continues the exploration of “large” structured data and demonstrates how the design recipe scales to the most complex kind of data. In the meantime, the next part takes care of an important worry you should have at this point, namely, that a programmer’s work is all about creating the same kind of programs over and over and over again.

## INTERMEZZO 2: QUOTE, UNQUOTE

Lists play an important role in our book as well as in Racket, the basis of our teaching languages. For the design of programs, it is critical to understand how lists are constructed from first principles; it informs the creation of our programs. Routine work with lists calls for a compact notation, however, like the `list` function introduced in chapter 11.1.

*Be sure to set your language level to BSL+ or up.*

Since the late 1950s, Lisp-style languages have come with an even more powerful pair of list-creation tools: quotation and anti-quotation. Many programming languages support them now, and the PHP web page design language injected the idea into the commercial world.

This intermezzo gives you a taste of this quotation mechanism. It also introduces *symbols*, a form of data that is intimately tied to quotation. While this introduction is informal and uses simplistic examples, the rest of the book illustrates the power of the idea with near-realistic variants. Come back to this intermezzo if any of these examples cause you trouble.

### Quote

*Quotation* is a short-hand mechanism for writing down a large list easily. Roughly speaking, a list constructed with the `list` function can be constructed even more concisely by quoting lists. Conversely, a quoted list abbreviates a construction with `list`.

Technically, quote is a keyword for a compound sentence in the spirit of intermezzo 1 and it is used like this: `(quote (1 2 3))`. DrRacket translates this expression to `(list 1 2 3)`. At this point, you may wonder why we call quote
