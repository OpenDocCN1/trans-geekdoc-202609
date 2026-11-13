liner:

```
; [List-of IR] Number -> Boolean
(define (find l th)
 (filter (lambda (ir) (<= (ir-price ir) th)) l))
```

The first two sections focus the mechanics of lambda; the remaining ones use lambda for instantiating abstractions, for testing and specifying, and for representing infinite data.