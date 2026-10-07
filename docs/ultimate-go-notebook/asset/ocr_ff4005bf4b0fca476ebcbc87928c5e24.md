![](bbox=[0.095, 0.053, 0.88, 0.411])

 caller would get a stack address from the frame below and integrity would be lost. Once control goes back to the calling function, the memory on the stack where the user value exists is reusable again. The moment the calling function makes another function call, a new frame is sliced and the memory will be overridden, destroying the shared value.

This is why I think about the stack being self cleaning. Zero value initialization helps every frame that I need to be cleaned without the use of the GC. The stack is self cleaning since a frame is taken and initialized for the execution of each function call. The stack is cleaned during function calls and not on returns because the compiler doesn't know if memory on the stack will be needed again.

Escape analysis decides if a value is constructed on the stack (the default) or the heap (the escape). With the stays function, I'm passing a copy of the value back to the caller, it's safe to keep the value on the stack. With the escapeToHeap function, I'm passing a copy of the value's address back to the caller (sharing up stack) so it's not safe to keep the value on the stack.

There are lots of little details related to the escape analysis, to learn more read the post in chapter 14 titled. Escape Analysis Mechanics.

Note: As of version 1.17, Go changed the ABI (application binary interface) to implement a new way of passing function input and output arguments registers instead of memory on the stack. This is enabled for Linux, MacOS, and

36