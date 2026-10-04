Finally, Example 13.10 shows how to instantiate a C struct from Go. This is like a regular Go struct. The only consideration is to use compatible data types. In this case, we have to declare a C string and convert the integer to a C compatible format. One question may arise is whether the variable should be released or not. This is a simple exercise for the reader to be tested. The answer depends on whether this struct is under the control of the garbage collector or not.

# Example 13.10: Instantiating C structs in Go.

```
package main

#include <stdlib.h>
typed struct {
	char *name;
	int id;
} User;

import "C"
import "fmt"
import "unsafe"

func main() {
	name := C.CString("John")

defer C.free(unsafe.Pointer(name))
	x := C.User{name: name, id: C.int(1234)}
	fmt.Println(C.GoString(x.name), x.id)
	// Should we release x?
	//C.free(unsafe.Pointer(&x))
}
```

![](bbox=[0.816, 0.301, 0.879, 0.366])

# 13.4 LINKING LIBRARIES

Accessing external libraries is one of the most powerful features of Cgo. This makes it possible to use a large variety of already existing solutions. The Cgo preamble admits pseudo #cgo directives to indicate the compiler what libraries and headers to use.

The preamble is an example of what instructions can be given to the compiler. Refer to the documentation for a complete list of available directives30. If you are familiar with C compilation directives, you have probably recognized the flags to link libraries (-lpng) or other compilation flags (-DPNG_DEBUG=1).

```
/*
#cgo LDFLAGS: -L/libfolder -lpng
#cgo CFLAGS:-I/headersfolder -DPNG_DEBUG=1
#cgo amd64 386 CFLAGS:-DX6=1
```