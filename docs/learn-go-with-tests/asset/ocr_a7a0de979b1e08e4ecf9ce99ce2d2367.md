Arrays have a *fixed capacity* which you define when you declare the variable. We can initialize an array in two ways:

+   - `[N]type{value1, value2, ..., valueN}` e.g. `numbers := [5]int{1, 2, 3, 4, 5}`
+   - `[...]type{value1, value2, ..., valueN}` e.g. `numbers := [...]int{1, 2, 3, 4, 5}`

It is sometimes useful to also print the inputs to the function in the error message. Here, we are using the `%v` placeholder to print the "default" format, which works well for arrays.

[Read more about the format strings](Read more about the format strings)

# ## Try to run the test

If you had initialized `go mod` with `go mod init main` you will be presented with an error `_testmain.go:13:2: cannot import "main"`. This is because according to common practice, package main will only contain integration of other packages and not unit-testable code and hence Go will not allow you to import a package with name `main`.

To fix this, you can rename the main module in `go.mod` to any other name.

Once the above error is fixed, if you run `go test` the compiler will fail with the familiar `./sum_test.go:10:15: undefined: Sum` error. Now we can proceed with writing the actual method to be tested.

# ## Write the minimal amount of code for the test to run and check the failing test output

In `sum.go`