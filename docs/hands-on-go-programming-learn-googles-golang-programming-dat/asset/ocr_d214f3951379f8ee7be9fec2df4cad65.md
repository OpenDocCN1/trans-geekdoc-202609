```
```go
return strings.Join(element, "_")
}

func main() {

// pass a slice in variadic function
element := []string{"GO", "language", "book"}
fmt.Println(join(element...))
}
```
```

The following will be the output for the above program:

```
GO_language_book
```

Let’s look at another program:

# Program 2.8

```
```go
//Select single argument from all arguments of variadic function

package main

import "fmt"

func main() {
variadicExample("IT", "Finance", "HR", "Recruitement", "Payroll")
}

func variadicExample(x ...string) {
fmt.Println(x[1])
```
```