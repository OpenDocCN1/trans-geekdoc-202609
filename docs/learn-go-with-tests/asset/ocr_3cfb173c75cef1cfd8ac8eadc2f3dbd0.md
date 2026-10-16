# Repeat for new requirements

So we've got the first part covered here - we know what angle the second hand will be pointing at in radians. Now we need to work out the coordinates.

Again, let's keep this as simple as possible and only work with the unit circle; the circle with a radius of 1. This means that our hands will all have a length of one but, on the bright side, it means that the maths will be easy for us to swallow.

# Write the test first

```
func TestSecondHandVector(t *testing.T) {
    cases := []struct {
        time time.Time
        point Point
    }{
        {simpleTime(0, 0, 30), Point{0, -1}},
    }

    for _, c := range cases {
        t.Run(testName(c.time), func(t *testing.T) {
            got := secondHandPoint(c.time)
            if got != c.point {
                t.Fatalf("Wanted %v Point, but got %v", c.point,
            }
        })
    }
}
```

# Try to run the test

./clockface_test.go:40:11: undefined: secondHandPoint

# Write the minimal amount of code for the test to run and check the failing test output