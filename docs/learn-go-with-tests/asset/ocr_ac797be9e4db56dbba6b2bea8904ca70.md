# test output

We need to define walk

```
func walk(x interface{}, fn func(input string)) {
}
```

Try and run the test again

```
=== RUN   TestWalk
--- FAIL: TestWalk (0.00s)
    reflection_test.go:19: wrong number of function calls, got 0 want 1
FAIL
```

# Write enough code to make it pass

We can call the spy with any string to make this pass.

```
func walk(x interface{}, fn func(input string)) {
    fn("I still can't believe South Korea beat Germany 2-0 to pu
}
```

The test should now be passing. The next thing we'll need to do is make a more specific assertion on what our fn is being called with.

# Write the test first

Add the following to the existing test to check the string passed to fn is correct

```
if got[0] != expected {
    t.Errorf("got %q, want %q", got[0], expected)
}
```