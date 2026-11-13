an-fsm)

According to the design recipe, the handler must consume a state of the world and a KeyEvent, and it must produce the next state of the world. This articulation of the signature in plain words also guides the design of examples. Here are the first two:

```
(check-expect
(find-next-state (make-fs fsm-traffic "red") "n")
(make-fs fsm-traffic "green"))
(check-expect
(find-next-state (make-fs fsm-traffic "red") "a")
(make-fs fsm-traffic "green")))
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