# 5.1. Statement Basics

This code snippet shows how the := operator can create "shadow" variables. In this snippet, inside the loop the a and b variables shadow variables from the outer scope, and while legal, this is almost certainly a programming error. On the other hand, there is only c variable (from the outer scope), so its usage is correct and as intended. Variables that shadow other variables can be very convenient, as we will see shortly, but careless use can cause problems.

As we will discuss later in the chapter, we can write return statements in functions that have one or more named return values, without specifying any return values. In such cases, the returned values will be the named return values, which are initialized with their zero values on entry to the function, and we can change by assigning them in the body of the function.

```
func shadow(err error) { // THIS FUNCTION WILL NOT COMPILE!
x, err := check(1) // x is created; err is assigned to
if err != nil {
    return err // correctly returned
}
if y, err := check(2); err != nil // y and inner err are created
    return // inner err shadows outer err so nil is wrongly returned!
} else {
    fmt.Println(ny)
}
return nil
}
```

In the shadow() function's first statement the x variable is created and assigned to, since it is already declared as the shadow() function's return value. This works because the := operator must create at least one nonblank variable and that condition is met. So, if err is not nil, it is correctly returned.

An if's simple statement, the optional statement that follows the if and precedes the condition, starts a new scope ($5.2.1,►). both the y and the err variables are created, the latter being a shadow variable. If the err is not nil it is returned (i.e., the err declared as the shadow() function's return value), which is nil since that was the value assigned by the call to check(1), whereas the call to check(2) was assigned to the shadowing inner err.

Fortunately, this shadow problem is much like a phantom, since the compiler will stop with an error message if we use a bare return when any return variables have been shadowed. So, this function will not compile as it stands.

One easy solution is to add a line to the start of the function that declares the variables (e.g., var x, y int or, y:=0), and change := to = for the check(1) and