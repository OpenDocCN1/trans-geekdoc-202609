```
/*
#include <stdio.h>
// This is a comment
void func_in_c() {
    printf("printed with C code\n");
}

import "C"
import "fmt"
func main() {
    C.func_in_c()
    fmt.Println("printed with Go code")
}
```

The pseudopackage c makes accessible all the functions, structs, and variables from linked C code. To invoke our function we only have to invoke it like c.func_in_c().

> You may find interesting that there are other Go compilers apart from the one maintained by Google. For example, gcgcop [5] is maintained by GNU under a General Public License and GopherJS [7] compiles Go into pure Javascript.

# 13.2 EXCHANGING VARIABLES

When exchanging variables between Go and C, we must be aware that data types may not be defined in the same way. For example, the Go int type can be 32 or 64 bits depending on the architecture. However, C typed variables are 16 or 32 bits long. Obviously, types must match between both languages to work correctly. Fortunately, the c pseudopackage offers functions to deal with these situations.

Example 13.3 defines a C function that sums two integers passed by argument. If the function is called using native Go integers as parameters, the compilation will fail with a message like cannot use a (type int) as type _ctype_int in argument to _Cfunc_sum. Using C int we can convert from Go native int to C to follow the signature of the target function.

Example 13.3: C function with arguments called from Go.

```
package main

int sum(int a, int b) {
    return a + b
}

import "C"
import "fmt"
```

![](bbox=[0.813, 0.787, 0.867, 0.813])