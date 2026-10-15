x[4] = 50

Let's look at the following code:

# Program 4.10

//Go program to iterate over an array using range

```
```go
package main

import "fmt"

func main() {
 x := [...]int{10, 20, 30, 40, 50}
 for index, value := range x {
 fmt.Printf("x[%d] = %d\n", index, value)
 }
}
```
```

The following will be the output for the above program:

```
x[0] = 10
x[1] = 20
x[2] = 30
x[3] = 40
x[4] = 50
```

If you are not interested in the index, we can just assign it to the blank identifier as shown below: