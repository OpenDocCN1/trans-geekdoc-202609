Since we know that SL describes lists of S-expr, we can use map to simplify for-sl. See figure 121 for the result. While the original program says that for-sexp is applied to every item on sl, its revised definition expresses the same idea more succinctly with map.

```
(define (substitute sexp old new)
  (local (; S-expr -> S-expr
          (define (for-sexp sexp)
            (cond
             [(atom? sexp) (for-atom sexp)]
             [else (for-sl sexp)]))
          ; SL -> S-expr
          (define (for-sl sl)
            (map for-sexp sl))
          ; Atom -> S-expr
          (define (for-atom at)
            (cond
             [(number? at) at]
             [(string? at) at]
             [(symbol? at) (if (equal? at old) new at)])))
  (for-sexp sexp)))
```

# Figure 121: Program simplification, step 1

For the second simplification step, we need to remind you that equal? compares two arbitrary values. With this in mind, the third local function becomes a one-liner. Figure 122 displays this second simplification.