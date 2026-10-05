# 4.1. Values, Pointers, and Reference Types

```
func swapAndProduct2(x, y int) (int, int, int) {
    if x > y {
        x, y = y, x
    }
    return x, y, x * y
}
```

This version of the function is perhaps clearer than the first one; but without pointers it has the disadvantage that it cannot perform the swap in-place.

In C and C++ it is common to have functions which accept a pointer to a Boolean that is used to indicate success or failure. This can easily be done in Go by including a *bool in a function's signature; but it is much more convenient to return a Boolean success flag (or best of all, an error value), as the last (or only) return value, which is standard practice in Go.

In the code snippets so far, we have used the & operator to take the address of function parameters or local variables. Thanks to Go's automatic memory management this is always safe, so long as a pointer refers to a variable, that will be kept in memory. This is why it is safe to return pointers to locals created inside functions in Go (something that is a disastrous error in C and C++ for nonstatic variables).

In situations where we want to pass around modifiable values of nonreference types or to pass values of large types efficiently, we can use pointers. Go provides two syntaxes for creating variables and at the same time acquiring pointers to them, one using the built-in new() function and the other using the address of operator. We will look at both syntaxes, and at how to create a plain struct value, for comparison.

```
type composer struct {
    name string
    birthYear int
}
```

Given this struct definition we can create composer values or we can create pointers to composer values, and in either case we can take advantage of Go's support for struct initialization when when we use braces.

```
antonio := composer("Antônio Teixeira", 1707) // composer value
agnes := new(composer) // pointer to composer
agnes.name, agnes.birthYear = "Agnes Zimmermann", 1845
julia := composer{} // pointer to composer
julia.name, julia.birthYear = "Julia Howe", 1819
augusta := composer("Augusta Holmès", 1847) // pointer to composer
```