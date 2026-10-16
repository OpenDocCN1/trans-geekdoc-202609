[{X1:150 Y1:150 X2:150 Y2:60}]

We'd better start building some other clock hands, Much in the same way as we produced the tests for the second hand, we can iterate to produce the following set of tests. Again we'll comment out our acceptance test while we get this working:

```
func TestMinutesInRadians(t *testing.T) {
    cases := []struct {
        time  time.Time
        angle float64
    }{
        {simpleTime(0, 30, 0), math.Pi},
    }

    for _, c := range cases {
        t.Run(testName(c.time), func(t *testing.T) {
            got := minutesInRadians(c.time)
            if got != c.angle {
                t.Fatalf("Wanted %v radians, but got %v", c.angle
```

# Try to run the test

./clockface_test.go:59:11: undefined: minutesInRadians

# Write the minimal amount of code for the test to run and check the failing test output

```
func minutesInRadians(t time.Time) float64 {
    return math.Pi
}
```

# Repeat for new requirements