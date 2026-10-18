```
x := 5
 y := 5

want := 10
got := sum(x, y)
if want != got {
    t.Logf("Testing a sum of: %d %d", x, y)
    t.Errorf("Sum was incorrect want: %d, but got: %d", want, got)
}
}
```

Then run go test ./ to run all the tests in the current package:

```
go test ./

--- FAIL: Test_sum (0.00s)
    /home/alex/go/src/github.com/alexellis/sum-testing/main_test.go:12: Testing a sum of: 5 5
    /home/alex/go/src/github.com/alexellis/sum-testing/main_test.go:13: Sum was incorrect
      want: 10, but got: 11
```

Notice the following about the unit test:

+   - The only parameter to the test method is: t *testing.T
+   - It begins with the word Test followed by a word or phrase, either with an underscore, or the function under test.
+   - The t variable is used to signal a failure.
+   - t.Log can be used to provide debug information for any test
+   - The file must be saved in a file named something_test.go such as: addition_test.go

Let's fix the test, edit the code in sum so that it doesn't add a rogue 1 to any number and run the tests again:

```
go test ./
ok      github.com/alexellis/sum-testing    0.001s
```

There are two ways to launch tests for a package. These methods work for unit tests and integration tests alike.

1) Within the same directory as the test:

```
go test
```

Or with a given path:

```
go test ./pkg/parser
```

*This picks up any files matching packagename_test.go*

or

2) By fully-qualified package name

```
go test github.com/alexellis/golangbasics1
```

You can run this from whatever folder you like.

You can add an additional test by using a unique name.

```
package main

import "testing"

func Test_sum_odd_numbers(t *testing.T) {
```