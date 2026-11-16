```
File: cmd/web/templates_test.go
package main
import (
	"testing"
	"time"
)
func TestHumanDate(t *testing.T) {
	// Initialize a new time.Time object and pass it to the humanDate function.
	tm := time.Date(2024, 3, 17, 10, 15, 0, 0, time.UTC)
	hd := humanDate(tm)

	// Check that the output from the humanDate function is in the format we
	// expect. If it isn't what we expect, use the t.Errorf() function to
	// indicate that the test has failed and log the expected and actual
	// values.
	if hd != "17 Mar 2024 at 10:15" {
		t.Errorf("got %q; want %q", hd, "17 Mar 2024 at 10:15")
	}
}
```

This pattern is the basic one that you’ll use for nearly all tests that you write in Go. The important things to take away are:

+   - The test is just regular Go code, which calls the humanDate() function and checks that the result matches what we expect.
+   - Your unit tests are contained in a normal Go function with the signature func(*testing.T).
+   - To be a valid unit test, the name of this function must begin with the word Test. Typically this is then followed by the name of the function, method or type that you’re testing to help make it obvious at a glance what is being tested.
+   - You can use the t.Errorf() function to mark a test as failed and log a descriptive message about the failure. It’s important to note that calling t.Errorf() doesn’t stop execution of your test — after you call it Go will continue executing any remaining test code as normal.

Let’s try this out. Save the file, then use the go test command to run all the tests in our cmd/web package like so:

```
$ go test ./cmd/web
ok snippetbox.alexedwards.net/cmd/web 0.005s
```

So, this is good stuff. The ok in this output indicates that all tests in the package (for now, only our TestHumanDate() test) passed without any problems.