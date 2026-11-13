Let's finally translate the examples into tests:

```
(check-expect (depth "red") 1)
(check-expect
 (depth
  (make-layer "yellow" (make-layer "green" "red")))
 3)
```

If you run these in DrRacket, you will see that their evaluation touches all pieces
of the definition of depth.

**Exercise 154.** Design the function colors. It consumes a Russian doll and
produces a string of all colors, separated by a comma and a space. Thus our
example should produce

```
"yellow, green, red"
```

**Exercise 155.** Design the function inner, which consumes an RD and
produces the (color of the) innermost doll. Use DrRacket’s stepper to evaluate
(inner rd) for your favorite rd.