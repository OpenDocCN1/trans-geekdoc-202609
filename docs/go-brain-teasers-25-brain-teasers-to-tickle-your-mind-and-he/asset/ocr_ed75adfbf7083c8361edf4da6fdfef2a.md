This code will not compile.

nil is not a type but a reserved word. A variable initialized to nil must have a type. If, for example, you’ll change the assignment to var n *int = nil, the code will compile since now n has a type.

Here are some places where nil is used:

+   The zero value for map, slice and chan is nil.

+   You can’t compare slices or maps using ==, you can only compare them to nil [4].

+   Sending to or receiving from a nil channel will block forever. You can use this to avoid a busy wait.