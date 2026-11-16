```
File: cmd/web/handlers_test.go

package main

...

func TestUserSignup(t *testing.T) {
	// Create the application struct containing our mocked dependencies and set
	// up the test server for running an end-to-end test.
	app := newTestApplication(t)
	ts := newTestServer(t, app.routes())
	defer ts.Close()

	// Make a GET /user/signup request and then extract the CSRF token from the
	// response body.
	_, body := ts.get(t, "/user/signup")
	csrfToken := extractCSRFToken(t, body)

	// Log the CSRF token value in our test output using the t.Logf() function.
	// The t.Logf() function works in the same way as fmt.Printf(), but writes
	// the provided message to the test output.
	t.Logf("CSRF token is: %q", csrfToken)
}
```

Importantly, you must run tests using the `-v` flag (to enable verbose output) in order to see any output from the `t.Logf()` function.

Let's go ahead and do that now:

```
$ go test -v -run="TestUserSignup" ./cmd/web/
=== RUN   TestUserSignup
--- handlers_test.go:81: CSRF token is: "C92tcpQpLn6aiUaf8XAonwy+YjcVnyaAa0vfkdL6vJqoNSbgaTtdBRC61PfMoGP2ojv+sZI8dSUikah3mFR
=== PASS: TestUserSignup (0.01s)
PASS
ok      snippetbox.alexedwards.net/cmd/web        0.010s
```

OK, that looks like it's working. The test is running without any problems and printing out the CSRF token that we've extracted from the response body HTML.

> **Note:** If you run this test for a second time immediately afterwards, without changing anything in the `cmd/web` package, you'll get the same CSRF token in the test output _because the test results have been cached_.

# Testing post requests

Now let's head back to our `cmd/web/testutils_test.go` file and create a new `postForm()` method on our `testServer` type, which we can use to send a `POST` request to our test server