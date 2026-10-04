```
}

14
15 func goFunction() {
16 	fmt.Println("goFunction was called")
17 }
```

This code will not work because goFunction is not exposed to C. This can be fixed with the reserved word export followed by the function name just before the function. This makes the compiler copy the function definition to the _c_export_h header. Unfortunately, there is a restriction that forces us to not include any function definition in the C preamble. Functions must be defined in a separate file or using function modifiers as we see. This because functions defined in the preamble are also copied to C headers and this results in the same function defined twice which triggers a linking error.

Considering these restrictions we can set our code to correctly expose functions to be called from C. We differentiate three cases based on the arguments of the Go function to be called.

# 13.5.1 Go functions without arguments

Example 13.13 shows a working solution for the previous example. First, in the preamble we define the goFunction() as an extern function to make it fully visible. The implementation of this function is available in our Go program. The compiler will link this function with the Go implementation we have declared the //exportFunction statement.

> 13.13: Go function without arguments called from C.

```
1 package main
2
3 /*
4 #include <stdio.h>
5 extern void goFunction();
6
7 static inline void CFunction() {
8 	printf("CFunction will call goFunction\n");
9 	goFunction();
10 }
11 //
12 import "C"
13 import "fmt"
14
15 // call function with no parameters
16 func main() {
17 
18 	CFunction()
19 }
20
21 //export goFunction
22 func goFunction() {
23 	fmt.Println("goFunction was called")
```

![](bbox=[0.576, 0.715, 0.659, 0.882])