```
... (local ((define names ...)
  (define sorted ...)
  (define concat+spaces
    (local (; String String -> String
            (define (helper s t)
              (string-append " " s t))))
    (foldr helper "" sorted))))
  concat+spaces) ...
```

It consists of exactly three definitions, suggesting it takes three computation steps. The third definition consists of a local expression on the right-hand side, which expresses that helper is really just needed for the third step.

Whether you want to express relationships among the pieces of a program with such precision depends on two constraints: the programming language and how long the code is expected to live. Some languages cannot even express the idea that helper is useful for the third step only. Then again, you need to balance the time it takes to create the program and the expectation that you or someone needs to revisit it and comprehend the code again. The preference of the Racket team is to err on the side of future developers because the team members know that no program is ever finished and all programs will need fixing. End

Figure 99 presents a second example. The organization of this function definition informs the reader that sort-cmp calls on two auxiliary functions: isort and insert. By locality, it becomes obvious that the adjective “sorted” in the purpose statement of insert refers to isort. In other words, insert is useful in this context only; a programmer should not try to use it elsewhere, out of context. While this constraint is already important in the original definition of the sort-cmp function, a local expression expresses it as part of the program.