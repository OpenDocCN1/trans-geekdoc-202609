# Example 13.14: Go functions with arguments called from C.

```
package main

/*
#include <stdio.h>
extern int goFunction(int number);

static inline inline void cFunction(int number) {
	printf("cFunction will call goFunction with %d\n", number);
	int x = goFunction(number);
	printf("goFunction returned %d\n", x);
}
*/
import "C"
import "fmt"

// call function with parameters
func main() {
	ccFunction(42)
}

//export func goFunction(number int32) int32 {
	fmt.Println("goFunction was called with", number)
	return number * 2
}
```

# 13.5.3 Functions with functions as arguments

For the previous cases, there is not too much engineering to be done. We must be sure to expose the Go function and to set data types. Things are different when the arguments of the function to be called are pointers to functions. This is common when defining callback functions. When a Go function is exposed to C, Cgo generates a stub for this function. This is a problem because Go pointers to functions may vary and are not directly visible to C. A gateway function must be provided.

We show how this can be done through an example. To better understand the data flow and involved components we see Figure 13.1.