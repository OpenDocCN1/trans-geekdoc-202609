# Listing 9.5

```
func main() {
    fmt.Print("vector[int] : \")
    vGenInt := vector(10, -1)
    i, err := vGenInt.last()
    if i < 0 {
        fmt.Print("negative integer: \")
    }
    fmt.Printf("value: %d error: %v\n", i, err)

    fmt.Print("vector[string] : \")
    vGenStr := vector("A", "B", string([]byte(0xff)))
    s, err := vGenStr.last()
    if !utf8.ValidString(s) {
        fmt.Print("non-valid string: \")
    }
    fmt.Printf("value: %q error: %v\n", s, err)
}
```

```
Output:
vector[int] : negative integer: -1 error: <nil>
vector[string] : non-valid string: value: "\xff" error: <nil>
```

This is how to construct a value of generic type with an underlying type of int when I will set the values in the vector at construction. An important aspect of this code is the construction calls.

# Listing 9.6

```
// Zero Value Construction
var vGenInt vector[int]
var vGenStr vector[string]

// Non-Zero Value Construction
vGenInt := vector(10, -1)
vGenStr := vector("A", "B", string([]byte(0xff)))
```

When it comes to constructing these generic types to their zero value, it's not possible for the compiler to infer the type. However, in cases where there is initialization during construction, the compiler can infer the type.

There is an aspect of the spec that focuses on the construction of a generic type to its zero value state.

# Listing 9.7

```
type vector[T any] []T

func (v vector[T]) last() (T, error) {
    var zero T
    if len(v) == 0 {
        return zero, errors.New("empty")
    }
    return v[len(v)-1], nil
}
```

I need to focus on the method declaration for the last method and how the method