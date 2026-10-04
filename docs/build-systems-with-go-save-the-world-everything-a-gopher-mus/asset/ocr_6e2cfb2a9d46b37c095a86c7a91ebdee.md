![](bbox=[0.126, 0.093, 0.874, 0.403])

Figure 13.1: Arguments and functions used to call a function with functions as arguments from C.

In our example, we have a pure C program implemented in clibrary.c. It has a function called a_callback_func that receives a pointer to a function. By default, it will call the function with parameter 42. Notice that the function to be called is not a Go function. Actually, it is a gateway function implemented in the C preamble of the file cfuncs.go. The gateway function, goFunction_cgo, which was initially passed by parameter to our pure C program, has access to the target goFunction fully implemented in Go.

For our example, we initially define a pure C program with a function that expects a pointer to a function with an integer argument. As it is usually in C, we define the header and the corresponding implementation in files clibrary.h and clibrary.c like shown in Examples 13.15 and 13.16 respectively. By default a_callback_func will call the provided function with argument 42.

Example 13.5: Cgo function pointers (clibrary.h)

```
#ifndef CLIBRARY_H
#define LIBRARY_H
typed void (*callback_f)(int);
void a_callback(callback_f);
#endif
```

Example 13.6: Cgo function pointers (clibrary.c)

```
#include "clibrary.h"
2
#include <stdio.h>
```