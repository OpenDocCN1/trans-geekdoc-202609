math package! If a full turn of a circle is 2π radians, we know that halfway round should just be π radians. math.Pi provides us with a value for π.

# Try to run the test

```
./clockface_test.go:12:9: undefined: secondsInRadians
```

# Write the minimal amount of code for the test to run and check the failing test output

```
func secondsInRadians(t time.Time) float64 {
    return 0
}
```

```
clockface_test.go:15: Wanted 3.141592653589793 radians, but got 0
```

# Write enough code to make it pass

```
func secondsInRadians(t time.Time) float64 {
    return math.Pi
}
```

```
PASS
ok      clockface  0.011s
```

# Refactor

Nothing needs refactoring yet

# Repeat for new requirements

Now we can extend the test to cover a few more scenarios. I'm going to skip forward a bit and show some already refactored test code - it should be clear enough how I got where I want to.