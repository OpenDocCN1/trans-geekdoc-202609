```
$ go test -v ./cmd/web
=== RUN   TestHumanDate
--- RUN   TestHumanDate/UTC
--- RUN   TestHumanDate/Empty
--- RUN   TestHumanDate/CET
templates_test.go:44: got '01 Jan 0001 at 00:00'; want ""
--- RUN   TestHumanDate/CET
templates_test.go:44: got '17 Mar 2024 at 10:15'; want '17 Mar 2024 at 09:15'
--- FAIL: TestHumanDate (0.00s)
    --- PASS: TestHumanDate/UTC (0.00s)
    --- FAIL: TestHumanDate/Empty (0.00s)
    --- FAIL: TestHumanDate/CET (0.00s)
FAIL
FAIL
FAIL	 snipptbox.alexedwards.net/cmd/web   0.003s
FAIL
```

So here we can see the individual output for each of our sub-tests. As you might have guessed, our first test case passed but the Empty and CET tests both failed. Notice how — for the failed test cases — we get the relevant failure message and filename and line number in the output?

Let's head back to our humanDate() function and update it to fix these two problems:

```
File: cmd/web/templates.go

package main

...

func humanDate(t time.Time) string {
	// Return the empty string if time has the zero value.
	if t.IsZero() {
		return ""
	}

	// Convert the time to UTC before formatting it.
	return t.UTC().Format("02 Jan 2006 at 15:04")
}

...
```

And when you re-run the tests everything should now pass.

```
$ go test -v ./cmd/web
=== RUN   TestHumanDate
=== RUN   TestHumanDate/UTC
=== RUN   TestHumanDate/Empty
=== RUN   TestHumanDate/CET
--- PASS: TestHumanDate (0.00s)
    --- PASS: TestHumanDate/UTC (0.00s)
    --- PASS: TestHumanDate/Empty (0.00s)
    --- PASS: TestHumanDate/CET (0.00s)
PASS
ok	 snipptbox.alexedwards.net/cmd/web   0.003s
```