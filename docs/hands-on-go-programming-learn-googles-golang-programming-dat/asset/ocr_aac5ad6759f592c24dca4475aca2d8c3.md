main.main()
/Users/prithvipalsingh/go/src/workspace/main.go:7 +0x1f
exit status 2

In Program we have declared the pointer array but we have not assigned the address of the any array. When we run, it panics because we tried to get the zeroth element of the pointer array but there is no underlying array that exists.

# Declaration using := operator

Program 10.12 creates the pointer array using the := operator:

# Program 10.12

```
```go
package main

import "fmt"

func main() {
var arr2 = [5]int{1, 2, 3, 4, 5}
arr1 := &arr2
fmt.Println("Zeroth element of arr1:", arr1[0])
}
```
```

The following will be the output for the above program:

Zeroth element of arr1: 1