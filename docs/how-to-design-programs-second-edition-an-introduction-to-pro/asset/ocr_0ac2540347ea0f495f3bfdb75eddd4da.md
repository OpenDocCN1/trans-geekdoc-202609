```
(define (==> x y)
(or (not x) y))
```

Use the stepper to determine the value of (==> #true #false).■

# **Exercise 25.** Take a look at this attempt to solve exercise 17:

```
(define (image-classify img)
(cond
 [(>= (image-height img) (image-width img)) "tall"]
 [(= (image-height img) (image-width img)) "square"]
 [(<= (image-height img) (image-width img)) "wide"]))
```

Does stepping through an application suggest a fix?■

# **Exercise 26.** What do you expect as the value of this program:

```
(define (string-insert s i)
 (string-append (substring s 0 i)
 "_"
 (substring s i)))

(string-insert "helloworld" 6)
```

Confirm your expectation with DrRacket and its stepper.■