```
; Node Node SimpleGraph -> Boolean
; is there a path from origin to destination in sg
(check-expect (path-exists? 'A 'E a-sg) #true
 (check-expect (path-exists? 'A 'F a-sg) #false)
(define (path-exists? origin destination sg)
 (cond
  [(symbol=? origin destination) #t]
  [else (path-exists? (neighbor origin sg)
                  destination
                  sg)])))
; Node SimpleGraph -> Node
; determine the node that is connected to a-node in sg
(check-expect (neighbor 'A a-sg) 'B)
(check-error (neighbor 'G a-sg) "neighbor: not a node")
(define (neighbor a-node sg)
 (cond
  [(empty? sg) (error "neighbor: not a node")]
  [else (if (symbol=? (first (first sg)) a-node)
          (second (first sg))
          (neighbor a-node (rest sg)))]))
```

Figure 180: Finding a path in a simple graph

Take another look at figure 179. In this simple graph there is no path from C to D. The connection that leaves C passes right by D and instead goes to E. So let’s look at a hand-evaluation:

```
(path-exists? 'C 'D '((A B) ... (F F)))
== (path-exists? 'E 'D '((A B) ... (F F)))
== (path-exists? 'B 'D '((A B) ... (F F)))
== (path-exists? 'C 'D '((A B) ... (F F)))
```

It confirms that as the function recurs, it calls itself with the exact same arguments again and again. In other words, the evaluation never stops.

Our problem with path-exists? is again a loss of “knowledge,” similar to that of relative->absolute above. Like relative->absolute, the design of path-exists? uses a recipe and assumes that recursive calls are independent of their context. In the case of path-exists? this means, in particular, that the function doesn’t “know” whether a previous application in the current chain of recursions received the exact same arguments.

The solution to this design problem follows the pattern of the preceding