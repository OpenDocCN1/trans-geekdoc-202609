# 4.3 Array initialization

If an array is not initialized explicitly, the default value array will be zero. An array can be initialized in Go with pre-defined values using an array literal.

An array literal contains the number of elements it will hold in square brackets, followed by the type of its elements. This is followed by a list of initial values separated by commas of each element inside the curly braces. There is no need to define all elements of an array.

Let's look at the following program:

# Program 4-3

```
```go
// Go program to explain array initialization

package main

import "fmt"

func main() {
 a := [5]int{2, 4, 6, 8, 10} // Initialized with values
 var b [5]int = [5]int{1, 3} // Partial assignment

 fmt.Println("Array a:", a)
```
```