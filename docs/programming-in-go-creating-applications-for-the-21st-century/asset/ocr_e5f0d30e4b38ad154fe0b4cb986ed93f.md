# 226 Chapter 5. Procedural Programming

A closure is created using the same syntax as for a normal function, but with one difference: The closure has no name (so the keyword func is immediately followed by an opening parenthesis). To use of a closure we normally assign it to a variable or put it in a data structure (such as a map or slice).

We have already seen several examples of closures—for example, when we defer or go statements with anonymous functions these are closures. We also created closures in other contexts, for example, the makeReplacerFunc() used in the anonymous example ($1.6, 29), and when we passed anonymous functions to the strings.FieldsFunc() and the strings.Map() functions in Chapter 3 ($3.6.1, 107), and the createCounter(207) and logPanics(218) functions quoted earlier in this chapter. Nonetheless, we will review a few examples here.

One use of closures is to provide a wrapper function that defines one or more of the arguments for the wrapped function. For example

```
addPG := func(name string) string { return name + ".png" }
addJPG := func(name string) string { return name + ".jpg" }
fmt.Println(addPG("filename"), addJPG("filename"))
```

```
filename.png filename.jpg
```

Both addPG and addJPG are variables that hold references to anonymous functions (i.e., closures). Such references can be called just like normal named functions as the code snippet illustrates.

In practice, when we want to create many similar functions, rather than making each one individually, we often use a factory function, that is, a function that returns a function. If there is a factory function that returns functions that add a suffix to a filename—but only if the suffix is not present.

```
func MakeAddSuffix(suffix string) func(string) string {
	return func(name string) string {
		if strings.HasSuffix(name, suffix) {
			return name + suffix
	}
		return name
	}
}
```