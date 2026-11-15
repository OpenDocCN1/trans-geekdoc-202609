⁵Details about the successor function are found in the *Function & Abstraction* and *Repetition & Recursion* chapters. ↩

With two applications, the result of the former becomes the input of the latter.

```
(3 (λy.y 2 *))(λx.x 1 +) → 7
```

Figure 12.1 shows the abstract-syntax tree, where λ is the abstraction operator and eval is the application operator.