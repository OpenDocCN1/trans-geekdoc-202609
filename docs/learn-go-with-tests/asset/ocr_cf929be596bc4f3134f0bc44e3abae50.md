```
want := "I"

    if got != want {
        t.Errorf("got %q, want %q", got, want)
    }
}
```

If you've got this far in the book this is hopefully feeling very boring and routine to you. That's a good thing.

# Try to run the test

```
./numeral_test.go:6:9: undefined: ConvertToRoman
```

Let the compiler guide the way

# Write the minimal amount of code for the test to run and check the failing test output

Create our function but don't make the test pass yet, always make sure the tests fails how you expect

```
func ConvertToRoman (arabic int) string {
    return ""
}
```

It should run now

```
=== RUN   TestRomanNumerals
--- FAIL: TestRomanNumerals (0.00s)
    numeral_test.go:10: got '', want 'I'
FAIL
```

# Write enough code to make it pass