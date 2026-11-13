We chose add-3-to-1 as the name for the local function because the name tells you what it computes. It adds 3 to the x-coordinate of one Posn.

You may now think that using abstractions is hard. Keep in mind, though, that this first example spells out every single detail and that it does so because we wish to teach you how to pick the proper abstraction. Let’s take a look at a second example a bit more quickly:

**Sample Problem** Design a function that eliminates all Posns with y-coordinates larger than 100 from some given list.

The first two steps of the design recipe yield this:

```
; [List-of Posn] -> [List-of Posn]
; eliminates Posns whose y-coordinate is > 100
(check-expect
 (keep-good (list (make-posn 0 110) (make-posn 0 60)))
 (list (make-posn 0 60)))

(define (keep-good lop) '())
```

By now you may have guessed that this function is like filter, whose purpose is to separate the “good” from the “bad.”

With local thrown in, the next step is also straightforward:

```
(define (keep-good lop)
 (local (; Posn -> Boolean
         ; should this Posn stay on the list
         (define (good? p) #true))
 (filter good? lop)))
```

The local function definition introduces the helper function needed for filter, and the body of the local expression applies filter to this local function and the given list. The local function is called good? because filter retains all those items of lop for which good? produces #true.

Before you read on, analyze the signature of filter and keep-good and determine why the helper function consumes individual Posns and produces Booleans.