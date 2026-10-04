```
16      }
17 }
18 fmt.Println("Closed something normally")
19 }
20
21 func main() {
22 defer fmt.Println("closed main")
23
24 something()
25 fmt.Println("Main was finished")
26 }
```

#  2.9 INIT FUNCTIONS

Now that we understand what variables, functions, and imports we can better understand how Go starts a program execution. We have mentioned that every program in Go must have a main package with a main function to be executed. However, this imposes some limitations for certain solutions such as libraries. We imagine importing a library into our code. A library is not designed to be executed, it only offers data structures, methods, functions, etc. Libraries probably do not even have a main package. If this library requires some configuration before invoked (initialize variables, detect the operating system, etc.) there must be a way to run this configuration without a main function.

Go defines init functions that are executed once per package. When we import a package the Go runtime follows this:

+   1. Initialize imported packages recursively.
2. Initialize and assign values to variables.
3. Execute init functions.

The output from Example 2.21 shows how the initialization follows the order described above. The setter function is invoked first, followed by init, and the main function.

Example 2.21: Go runtime initialization order.

```
1 package main
2
3 import "fmt"
4
5 var x = xSetter()
6
7 func xSetter() int {
8 fmt.Println("xSetter")
9 return 42
10 }
11
12 func init() {
13 fmt.Println("Init function")
14 }
```

![](bbox=[0.765, 0.703, 0.87, 0.788])