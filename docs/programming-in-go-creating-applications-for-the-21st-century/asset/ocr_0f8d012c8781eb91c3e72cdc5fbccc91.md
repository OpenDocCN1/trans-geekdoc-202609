# 1.5. Stack-Custom Types with Methods

tion or method using append() (as opposed to simply changing one of its existing items), then we must either pass the slice by pointer, return the slice (and set the original slice to the function or method's return value), since append() some-times returns a different slice reference than the one it passed.

The Stack type uses a slice for its representation and therefore Stack values can be used with functions that operate on a slice, such as append() and len(). Nonetheless, Stack values are in their own right, distinct from their representation, they must be passed by pointer if we want to modify them.

```
func (stack Stack) Top() (interface{}, error) {
	if len(stack) == 0 {
		return nil, errors.New("can't Top() an empty stack")
	}
	return stack[len(stack)-1], nil
}
```

Stack.Top() returns the item at the top of the stack (the item that added last) and a nil error; or a nil item and a non-nil error value, if the stack is empty. The stack receiver is passed by value since the stack isn't modified.

The error type is an interface type ($6.3, ► 265) which specifies a single method, Error() string. In general, Go's library functions return an error as their last (or) return value to indicate success (where error is nil) or failure. Here, we have made our Stack type work like a standard library type by creating a new error using the package's errors.New() function.

Go uses nil for zero pointers (and for zero references); there is no pointer to nothing and for references that refer to nothing.* Such pointers should be used only in conditions or assignments; methods should not normally be called on them.

Constructors are never called implicitly in Go. Instead Go guarantees that when a value is created it is always initialized to its zero value. For example, numbers are initialized to 0, strings to the empty string, pointers to nil, and the fields inside structs are similarly initialized. There is no uninitialized data in Go, thus eliminating a major source of errors that afflicts many other programming languages. If the zero value isn't suitable we can write a construction function—and call it explicitly—as we here to prevent values of a type being created without using a constructor function, as we will see in Chapter 6.

> * Go's nil is in effect the same as NULL or 0 in C and C++, in Java, and nil in Objective-C.