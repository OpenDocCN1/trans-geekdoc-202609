Again, a bit of thinking is now required. We need to move the hour hand along a little bit for both the minutes and the seconds. Luckily we have an angle already to hand for the minutes and the seconds - the one returned by minutesInRadians. We can reuse it!

So the only question is by what factor to reduce the size of that angle. One full turn is one hour for the minute hand, but for the hour hand it's twelve hours. So we just divide the angle returned by minutesInRadians by twelve:

```
```go
func hoursInRadians(t time.Time) float64 {
    return (minutesInRadians(t) / 12) +
        (math.Pi / (6 / float64(t.Hour()%12)))
}
```
```

and behold:

clockface_test.go:104: Wanted 0.013089969389957472 radians, but got 0.01308996938995747

Floating point arithmetic strikes again.

Let's update our test to use roughlyEqualFloat64 for the comparison of the angles.

```
```go
func TestHoursInRadians(t *testing.T) {
    cases := []struct {
        time  time.Time
        angle float64
    }{
        {simpleTime(6, 0, 0), math.Pi},
        {simpleTime(0, 0, 0), 0},
        {simpleTime(21, 0, 0), math.Pi * 1.5},
        {simpleTime(0, 1, 30), math.Pi / ((6 * 60 * 60) / 90)},
    }

    for _, c := range cases {
        t.Run(testName(c.time), func(t *testing.T) {
            got := hoursInRadians(c.time)
            if !roughlyEqualFloat64(got, c.angle) {
                t.Fatalf("Wanted %v radians, but got %v", c.angle
```
```