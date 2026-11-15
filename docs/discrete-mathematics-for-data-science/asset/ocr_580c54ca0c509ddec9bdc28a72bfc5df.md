# 3 Evaluate.

# Beta reduction example (two arguments):

1 2 (λx.λy.x y +)   Identify first argument and variable for binding.
2 (λx.λy.1 y +)     Bind 1 to x.
2 (λy.1 y +)        Strip λx head.
2 (λy.1 y +)        Identify first argument and variable for binding.
(λy.1 2 +)          Bind 2 to y.
1 2 +               Strip λy head.
3                   Evaluate.

# Beta reduction example (two arguments):

(λz.z) 2 (y
λx.λy.x)   Identify first argument and variable for binding.
2 (y λx.λy.
(λz.z))    Bind (λz.z) to x.
2 (y λy.(λz.z)) Strip λx head.
2 (y λy.(λz.z)) Identify first argument and variable for binding.
(2 λy.(λz.z))   Bind 2 to y.
2 (λz.z)        Strip λy head.
2 (λz.z)        Identify first argument and variable for binding.
(λz.2)          Bind 2 to z.
λz.2            Strip λz head.