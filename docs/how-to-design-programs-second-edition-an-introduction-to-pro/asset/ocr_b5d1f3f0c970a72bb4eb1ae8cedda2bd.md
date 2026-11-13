```
; Xexpr.v3 String -> String
; retrieves the value of the "content" attribute
; from a 'meta element that has attribute "itemprop"
; with value s
(check-expect
  (get '(meta ((content "+1") (itemprop "F"))) "F")
  "+1")

(define (get x s)
  (local ((define result (get-xexpr x s)))
    (if (string? result)
      result
      (error "not found")))))
```

It assumes the existence of get-xexpr, a function that searches an arbitrary Xexpr.v3 for the desired attribute and produces [Maybe String].

Formulate test cases that look for other values than "F" and that force get to signal an error.

Design get-xexpr. Derive functional examples for this function from those for get. Generalize these examples so that you are confident get-xexpr can traverse an arbitrary Xexpr.v3. Finally, formulate a test that uses the web data saved in exercise 385.