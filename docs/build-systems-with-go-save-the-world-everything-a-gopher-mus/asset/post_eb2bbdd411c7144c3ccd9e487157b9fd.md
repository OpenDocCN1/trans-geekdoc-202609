
# Example 13.14: Go functions with arguments called from C.

```go
package main

/*
#include <stdio.h>
extern int goFunction(int number);

static inline void cFunction(int number) {
	printf("cFunction will call goFunction with %d\n", number);
	int x = goFunction(number);
	printf("goFunction returned %d\n", x);
}
*/
import "C"
import "fmt"

// call function with parameters
func main() {
	cFunction(42)
}

//export goFunction(number int32) int32 {
	fmt.Println("goFunction was called with", number)
	return number * 2
}
```

# 13.5.3 Functions with functions as arguments

For the previous cases, there is not too much engineering to be done. We must be sure to expose the Go function and to set data types. Things are different when the arguments of the function to be called are pointers to functions. This is common when defining callback functions. When a Go function is exposed to C, Cgo generates a stub for this function. This is a problem because Go pointers to functions may vary and are not directly visible to C. A gateway function must be provided.

We show how this can be done through an example. To better understand the data flow and involved components we see Figure 13.1.

![](img/c7dcb4df7215ed1d3fb76d25373be6c7_178_0.png)

Figure 13.1: Arguments and functions used to call a function with functions as arguments from C.

In our example, we have a pure C program implemented in clibrary.c. It has a function called a_callback_func that receives a pointer to a function. By default, it will call the function with parameter 42. Notice that the function to be called is not a Go function. Actually, it is a gateway function implemented in the C preamble of the file cfuncs.go. The gateway function, goFunction_cgo, which was initially passed by parameter to our pure C program, has access to the target goFunction fully implemented in Go.

For our example, we initially define a pure C program with a function that expects a pointer to a function with an integer argument. As it is usually in C, we define the header and the corresponding implementation in files clibrary.h and clibrary.c like shown in Examples 13.15 and 13.16 respectively. By default a_callback_func will call the provided function with argument 42.

Example 13.5: Cgo function pointers (clibrary.h)

```c
#ifndef CLIBRARY_H
#define LIBRARY_H
typedef void (*callback_f)(int);
void a_callback(callback_f);
#endif
```

Example 13.6: Cgo function pointers (clibrary.c)

```c
#include "clibrary.h"
#include <stdio.h>

void a_callback_func(callback_f f) {
    printf("C_callback_func calls a Go gateway function\n");
    printf("argument 42\n");
    f(42);
}
```

As shown in Chapter, if we compile our C program into a library this can be linked to a C preamble. Example 13.17: contains the code for the main.go file. Observe that the C preamble needs cgo directives to include the library from the compilation of our C program. Additionally, the preamble defines the goFunction_cgo which is our gateway function.

The C go package has access to a_callback_func because we have already included the corresponding C header file. When calling this function from Go, we use a pointer to the gateway function goFunction_cgo to explicitly cast the C type callback_f. In this way, our C library can find a target. Now we only have to implement our gateway function.

# Example 13.17: Cgo function pointers (go)

```go
package main

import (
    "fmt"
    "unsafe"
)

/*
#cgo CFLAGS: -I .
#cgo LDFLAGS: -L .
#include "library.h"
*/
func goFunction_cgo(int number)

func main() {
    fmt.Println("Go main calls a_callback_func")
    C.a_callback_func((C.callback_f)(unsafe.Pointer(C.goFunction_cgo)))
}

//export goFunction
func goFunction(int number) {
    fmt.Println("goFunction was finally called with:", number)
}
```

The gateway function is implemented in the cfuncs.go file like shown in Example 13.18. We simply call goFunction from the C preamble. Remember that this function is available because it uses the export statement.

# Example 13.18: Cgo function pointers (cfunc)

```go
package main

/*
#include <stdio.h>
void goCgo(int number) {
    printf("goFunction_cgo with number %d\n",number);
    void goFunction(int);
    goFunction(number);
}
*/

import "C"
```

The following lines, compile the C code into a library and build the corresponding executable file.

```
gcc -c library.c
ar cr liblibrary.a library.go
go build .go
```

After these commands finish, the executable cfuncs will run the program. The printed messages give an idea of the followed execution workflow.

Go main() calls a_callback_func
C a_callback_func calls a Go gateway function
with argument 42
goFunction_cgo with number 42
GoFunction was finally called with 42

# 13.6 SUMMARY

This Chapter discusses how Go programs can interact with C. We have covered how to call functions, exchange structs, and how to manage data types between both languages. Additionally, we have explored the potential issues that may arise when mixing the Go memory model with C pointers. Using Cgo unveils a large potential in terms of the number of existing libraries your Go program can use.

# # Part II
Building systems

![](img/c7dcb4df7215ed1d3fb76d25373be6c7_181_0.png)

Image by Egon Elbre (@egonelbre)

# CHAPTER 14
PROTOCOL BUFFERS

Nowadays systems are distributed. Formats such as XML, JSON (see Chapter 8) are commonly used because they are easy to parse. However, they are not efficient in terms of message size. To mitigate these problems, Google developed protocol buffers 3 as a language-neutral mechanism. Protocol buffers is available for various languages including Go.

This Chapter introduces protocol buffers, explains what they are, how they are built, and how they help us define messages.

# 14.1 THE PROTO FILE

The definition of messages in protocol buffers (PB from now on) is independent of the programming language. The protocol file is interpreted by the protoc tool which generates the code for every language. This is an abstraction mechanism that releases the developer from complexities of defining low level data transfer.

```go
package user
// ...
type User struct {
// ...
  UserId string 'protobuf:bytes,1'
  Email string 'protobuf:bytes,2'
}
// ...
```

```proto
syntax = "proto3";
package user;

option go_package="github.com/juanmanuel-tirado/savetheworldwithgo/12_protocolbuffers/pb/example_01/user";
message User {
  string user_id = 1;
  string email = 2;
}
```

```go
// ...
import "user"
// ...
u := user.User {
  Email: "john@gmail.com",
  UserId: "John"
}
```

# 14.1: Steps to define and use protocol buffer.

14.1 depicts the steps carried out to define and use entities defined with PB. This is represented as an iterative cycle where the changes in PB entities require recompilations of the serialization mechanisms, which may require changes in the final code using these entities. This detaches serialization mechanisms from the logic of the program.
