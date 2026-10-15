# 5.5 _Zero-value slice_

Nil slice does not contain any element in it. So, the capacity and the length of this slice is 0. Nil slice does not contain an array reference. Let’s look at the following example:

# Program 5.8

```
```go
// Go program to create zero value slice

package main

import "fmt"

func main() {
// Creating a zero value slice
var my_slice []string
fmt.Printf("Length of Slice = %d\n", len(my_slice))
fmt.Printf("Capacity of Slice = %d", cap(my_slice))
}
```
```

The following will be the output for the above program:

```
```text
Length of Slice = 0
Capacity of Slice = 0
```
```