
## 12.8 Finite State Machines

Finite state machines (FSMs) and regular expressions are ubiquitous elements of programming. As chapter 4.7 explains, state machines are one way to think about world programs. Conversely, exercise 109 shows how to design world programs that implement an FSM and check whether a player presses a specific series of keystrokes.

As you may also recall, a finite state machine is equivalent to a regular expression. Hence, computer scientists tend to say that an FSM accepts the keystrokes that match a particular regular expression, like this one

```
a (b|c) * d
```

from exercise 109. If you wanted a program that recognizes a different pattern, say,

```
a (b|c) * a
```

you would just modify the existing program appropriately. The two programs would resemble each other, and if you were to repeat this exercise for several different regular expressions, you would end up with a whole bunch of similar-looking programs.

A natural idea is to look for a general solution, that is, a world program that consumes a data representation of an FSM and recognizes whether a player presses a matching sequence of keys. This section presents the design of just such a world program, though a greatly simplified one. In particular, the FSMs come without initial or final states, and the matching ignores the actual keystrokes; instead the transition from one state to another takes place whenever any key is pressed. Furthermore, we require that the states are color strings. That way, the FSM-interpreting program can simply display the current state as a color.

Note on Design Choices. Here is another attempt to generalize:

Sample Problem: Design a program that interprets a given FSM on a specific list of KeyEvents. That is, the program consumes a data representation of an FSM and a string. Its result is #true if the string matches the regular expression that corresponds to the FSM; otherwise it is #false.

As it turns out, however, you **cannot design** this program with the principles of the first two parts. Indeed, solving this problem has to wait until chapter 30; see exercise 476. End

The simplified problem statement dictates a number of points, including the need for a data definition for the representation of FSMs, the nature of its states, and their appearance as an image. Figure 82 collects this information. It starts with a data definition for FSMs. As you can see, an FSM is just a list of Transitions. We must use a list because we want our world program to work with any FSM and that means a finite, but arbitrarily large, number of states. Each Transition combines two states in a structure: the current state and the next state, that is, the one that the machine transitions to when the player presses a key. The final part of the data definition says that a state is just the name of a color.

```
;; An FSM is one of:
;; -- '()
;; -- (cons Transition FSM)
(define-struct transition [current next])
;; A Transition is a structure:
;; (make-transition FSM-State FSM-State)
;; FSM-State is a Color.
;; interpretation An FSM represents the transitions that a
;; finite state machine can take from one state to another
;; in reaction to keystrokes
```

Figure 82: Representing and interpreting finite state machines in general

### Exercise 226. Design state=?, an equality predicate for states.

Since this definition is complex, we follow the design recipe and create an example:

```scheme
(define fsm-traffic
  (list (make-transition "red" "green")
        (make-transition "green" "yellow")
        (make-transition "yellow" "red")))
```

You probably guessed that this transition table describes a traffic light. Its first transition tells us that the traffic light jumps from "red" to "green", the second one represents the transition from "green" to "yellow", and the last one is for "yellow" to "red".

### Exercise 227. The BW Machine is an FSM that flips from black to white and back to black for every key event. Formulate a data representation for the BW Machine.

Clearly, the solution to our problem is a world program:

```scheme
; FSM -> ???
; match the keys pressed with the given FSM
(define (simulate an-fsm)
  (big-bang ...
    [to-draw ...]
    [on-key ...]))
```

It is supposed to consume a FSM, but we have no clue what the program is to produce. We call the program simulate because it acts like the given FSM in response to a player's keystrokes.

Let's follow the design recipe for world programs anyway to see how far it takes us. It tells us to differentiate between those things in the “real world” that change and those that remain the same. While the simulate function consumes an instance of FSM, we also know that this FSM does not change. What changes is the current state of the machine.

This analysis suggests the following data definition

```scheme
; A SimulationState.v1 is an FSM-State.
```

According to the design recipe for world programs, this data definition completes the main function:

```scheme
(define (simulate.v1 fsm0)
  (big-bang initial-state
    [to-draw render-state.v1]
    [on-key find-next-state.v1]))
```

and implies a wish list with two entries:

```scheme
; SimulationState.v1 -> Image
; renders a world state as an image
(define (render-state.v1 s)
  empty-image)

; SimulationState.v1 KeyEvent -> SimulationState.v1
; finds the next state from ke and cs
(define (find-next-state.v1 cs ke)
  cs)
```

The sketch raises two questions. First, there is the issue of how the very first SimulationState.v1 is determined. Currently, the chosen state, initial-state, is marked in grey to warn you about the issue. Second, the second entry on the wish list must cause some consternation:

How can find-next-state possibly find the next state when all it is given is the current state and a keystroke?

This question rings especially true because, according to the simplified problem statement, the exact nature of the keystroke is irrelevant; the FSM transitions to the next state regardless of which key is pressed.

What this second issue exposes is **a fundamental limitation of BSL+**. To appreciate this limitation, we start with a work-around. Basically, the analysis demands that the find-next-state function receives not only the current state but also the FSM so that it can search the list of transitions and pick the next state. In other words, the state of the world must include both the current state of the FSM and the FSM itself:

```scheme
(define-struct fs [fsm current])
; A SimulationState.v2 is a structure:
;   (make-fs FSM FSM-State)
```

> Alonzo Church and Alan Turing, the first two computer scientists, proved in the 1930s that all programming languages can compute certain functions on numbers. Hence, they argued that all programming languages were equal. The first author of this book disagrees. He distinguishes languages according to **how** they allow programmers to express solutions.

According to the world design recipe, this change also means that the key-event handler must return this combination:

```scheme
; SimulationState.v2 -> Image
; renders a world state as an image
(define (render-state.v2 s)
  empty-image)
```

```scheme
; SimulationState.v2 KeyEvent -> SimulationState.v2
; finds the next state from ke and cs
(define (find-next-state.v2 cs ke)
  cs)
```

Finally, the main function must now consume two arguments: the FSM and its first state. After all, the various FSMs that simulate consumes come with all kinds of states; we cannot assume that all of them have the same initial state. Here is the revised function header:

```scheme
; FSM FSM-State -> SimulationState.v2
; match the keys pressed with the given FSM
(define (simulate.v2 an-fsm s0)
  (big-bang (make-fs an-fsm s0)
       [to-draw state-as-colored-square]
       [on-key find-next-state]))
```

Let's return to the example of the traffic-light FSM. For this machine, it would be best to apply simulate to the machine and "red":

```scheme
(simulate.v2 fsm-traffic "red")
```

Stop! Why do you think "red" is good for traffic lights?

> Engineers call "red" the safe state.

Note on Expressive Power. Given the work-around, we can now explain the limitation of BSL. Even though the given FSM does not change during the course of the simulation, its description must become a part of the world’s state. Ideally, the program should express that the description of the FSM remains constant, but instead the program must treat the FSM as part of the ever-changing state. The reader of a program cannot deduce this fact from the first piece of big-bang alone.

The next part of the book resolves this conundrum with the introduction of a new programming language and a specific linguistic construct: ISL and local definitions. For details, see chapter 16.3. End

At this point, we can turn to the wish list and work through its entries, one at a time. The first one, the design of state-as-colored-square, is so straightforward that we simply provide the complete definition:

```scheme
; SimulationState.v2 -> Image
; renders current world state as a colored square

(check-expect (state-as-colored-square
               (make-fs fsm-traffic "red"))
             (square 100 "solid" "red"))

(define (state-as-colored-square an-fsm)
  (square 100 "solid" (fs-current an-fsm)))
```

In contrast, the design of the key-event handler deserves some discussion.

Recall the header material:

```scheme
; SimulationState.v2 KeyEvent -> SimulationState.v2
; finds the next state from ke and cs
(define (find-next-state an-fsm current)
```
