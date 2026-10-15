in the actual value. Program 10.3 modifies the value of *a and it will reflect in variable x as well.

# Program 10.3

```
```go
package main

import "fmt"

func main() {
 x := 15
 a := &x
 fmt.Println("Value of x(before modification):", x)
 fmt.Println("Value of *a:(before modification):", *a)
 *a = 20
 fmt.Println("Value of x(After modification):", x)
 fmt.Println("Value of *a:(After modification):", *a)
}
```
```

The following will be the output for the above program:

Value of x(before modification): 15
Value of *a:(before modification): 15
Value of x(After modification): 20
Value of *a:(After modification): 20

The built-in function new() can be used to create a pointer:

# Program 10.4

```
```go
package main
```
```