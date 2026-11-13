```
```scheme
(define (missile-or-not? v)
  (cond
    [(boolean? v) ...]
    [(posn? v) (... (posn-x v) ... (posn-y v) ...)]
    [else #false]))
```
```

All other cases are summarized via an else line that produces #false.

Given the template, the definition of missile-or-not? is a simple matter of thinking through each case:

```
```scheme
(define (missile-or-not? v)
  (cond
    [(boolean? v) (boolean=? #false v)]
    [(posn? v) #true]
    [else #false]))
```
```

Only #false is a legitimate MissileOrNot; #true isn't. We express this idea with (boolean=? #false v), but (false? v) would also do:

```
```scheme
(define (missile-or-not? v)
  (cond
    [(false? v) #true]
    [(posn? v) #true]
    [else #false]))
```
```

Naturally all elements of Posn are also members of MissileOrNot, which explains the #true in the second line.

**Exercise 112.** Reformulate the predicate now using an or expression. ‡

**Exercise 113.** Design predicates for the following data definitions from the preceding section: SIGS, Coordinate (VAnimal. ‡

To wrap up, let us mention key-event? and mouse-event? as two important predicates that you may wish to use in your world programs. They check the expected property, but you should check out their documentation to make sure you understand what they compute.