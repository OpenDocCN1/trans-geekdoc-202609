# 1.2.2 Short variable declaration

In Go, you can declare variables in the following two ways:

Using var keyword

Using a short declaration operator

The short variable declaration operator is used to declare and initialize the local variables inside a function. It narrows the scope of the variable.

Using a short declaration operator, variables are declared without specifying the type. The type of variable is determined by the type of expression on the right-hand side of the := operator.

Syntax of short variable declaration operator:

```
variable_name := expression or value
```

Examples:

```
a := 10
```

```
x, y := 100, 200
```

```
p, q, r := 150, 250, 300
```