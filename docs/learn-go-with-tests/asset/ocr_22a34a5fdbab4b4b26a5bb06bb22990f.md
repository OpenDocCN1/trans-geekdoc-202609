documentation.

```
// Add takes two integers and returns the sum of them.
func Add(x, y int) int {
    return x + y
}
```

# Examples

If you really want to go the extra mile you can make examples. You will find a lot of examples in the documentation of the standard library.

Often code examples that can be found outside the codebase, such as a readme file often become out of date and incorrect compared to the actual code because they don't get checked.

Go examples are executed just like tests so you can be confident examples reflect what the code actually does.

Examples are compiled (and optionally executed) as part of a package's test suite.

As with typical tests, examples are functions that reside in a package's _test.go files. Add the following ExampleAdd function to the adder_test.go file.

```
func ExampleAdd() {
    sum := Add(1, 5)
    fmt.Println(sum)
    // Output: 6
}
```

(If your editor doesn't automatically import packages for you, the compilation step will fail because you will be missing import "fmt" in adder_test.go. It is strongly recommended you research how to have these kind of errors fixed for you automatically in whatever editor you are using.)