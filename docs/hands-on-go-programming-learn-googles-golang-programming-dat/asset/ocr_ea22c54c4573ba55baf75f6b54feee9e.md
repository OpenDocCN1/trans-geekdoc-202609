```
```go
a := 20
b := true
```
```

When Go finds the := assignment syntax, it understands that a new variable needs to be declared with an initial value. But you cannot use this syntax to assign a value to a pre-defined variable. The variable type is deduced from the value. For example, a value of 20 indicates an int and a value of true tells Go that the type should be Boolean.