# 5.7 Multi-dimensional Slice

The multi-dimensional slice is just like the multidimensional array, except that the slice does not contain the size. Let’s look at the following example:

# Program 5.10

// Go program to create and access multi-dimensional slice

```
package main

import "fmt"

func main() {
// Creating multi-dimensional slice
s1 := [][]int{{10, 20},
{40, 80},
{50, 100},
{200, 400},
}

// Accessing multi-dimensional slice
fmt.Println("Slice 1 :", s1)

// Creating multi-dimensional slice
s2 := [][]string{
```