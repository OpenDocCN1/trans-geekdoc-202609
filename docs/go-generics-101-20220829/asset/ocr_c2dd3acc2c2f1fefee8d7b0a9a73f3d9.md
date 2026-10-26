By the current specification (Go 1.19), for a type parameter involved assignment,

+   - if the destination type is a type parameter and the source value is an untyped value, then the assignment is valid only if the untyped value is assignable to each type in the type set of the destination type parameter.
+   - if the destination type is a type parameter but the source type is an ordinary type, then the assignment is valid only if the source ordinary type is unnamed and its values is assignable to each type in the type set of the destination type parameter.
+   - if the source type is a type parameter but the destination type is an ordinary type, then the assignment is valid only if the destination ordinary type is unnamed and values of each type in the type set of the source type parameter are assignable to the destination ordinary type.
+   - if both of the destination type and the source type are type parameters, then the assignment is invalid.

From the rules, we could get that type value of a named type can not be assigned to another named type.

In the following code snippet, there are four invalid assignments.

```
func dat[T ~int | ~float64, S *int | []bool]() {
    var _ T = 123 // okay
    var _ S = nil // okay
}
```

```
func zum[T []byte](x []byte) {
    var t T = x // okay
    type Bytes []byte
    var y Bytes = x // okay (both are ordinary types)
    x = t // okay
    x = y // okay

    // Both are named types.
    t = y // error
    y = t // error

    // To make the above two assignments valid,
    // the sources in then must be converted.
    t = T(y)     // okay
    y = Bytes(t) // okay
}
```

```
func pet[A, B []byte](x A, y B){
    // Both are type parameters.
    x = y // error: cannot use y as type A in assignment
    y = x // error: cannot use x as type B in assignment
}
```

It is unclear whether or not the assignment rules will be relaxed in future Go versions. It looks the posibility is small.