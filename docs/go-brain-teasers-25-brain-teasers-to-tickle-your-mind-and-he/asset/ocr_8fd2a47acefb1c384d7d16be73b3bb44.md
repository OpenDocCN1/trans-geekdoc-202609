This code will print: error: <nil>

The if statement in line 19 says that err != nil, but err prints out as <nil>. Further more err in line 14 is not initialized, meaning it has the zero value for a pointer - which is nil.

If you'll look at src/runtime/runtime2.go you'll see the following definition:

```
type iface struct {
    tab    *itab
    data   unsafe.Pointer
}
```

+   - itab describes the interface

+   - data is a pointer to the value that implements the interface

An interface is considered nil only if both itab and data are nil, which is not the case here.

The solution is **always** to use variables of type error when returning errors.
In this case change line 14 to `var err error`.