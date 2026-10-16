
```
y := math.Cos(angle)

    return Point{x, y}
}

PASS
ok      clockface  0.009s
```

## Refactor

We've definitely got a bit of repetition in the minuteHandPoint and secondHandPoint - I know because we just copied and pasted one to make the other. Let's DRY it out with a function.

```
func angleToPoint(angle float64) Point {
    x := math.Sin(angle)
    y := math.Cos(angle)

    return Point{x, y}
}
```

and we can rewrite minuteHandPoint and secondHandPoint as one liners:

```
func minuteHandPoint(t time.Time) Point {
    return angleToPoint(minutesInRadians(t))
}
```

```
func secondHandPoint(t time.Time) Point {
    return angleToPoint(secondsInRadians(t))
}
```

PASS
ok      clockface  0.007s

Now we can uncomment the acceptance test and get to work drawing the minute hand.

## Write enough code to make it pass

![](img/570fb0b5bd524332c8e0fb9e37d716fb_304_0.png)

## Refactor

Let's remove the duplication from the secondHand and minuteHand functions, putting all of that scale, flip and translate logic all in one place.

```
func secondHand(w io.Writer, t time.Time) {
    p := makeHand(secondHandPoint(t), secondHandLength)
    fmt.Fprintf(w, `<line x1="150" y1="150" x2="%.3f" y2="%.3f" ;
```
```
}
func minuteHand(w io.Writer, t time.Time) {
    p := makeHand(minuteHandPoint(t), minuteHandLength)
    fmt.Fprintf(w, `<line x1="150" y1="150" x2="%.3f" y2="%.3f" `;
}

func makeHand(p Point, length float64) Point {
    p = Point{p.X * length, p.Y * length}
    p = Point{p.X, -p.Y}
    return Point{p.X + clockCentreX, p.Y + clockCentreY}
}
```

PASS
ok      clockface  0.007s

This is where we're up to now.

There... now it's just the hour hand to do!

## Write the test first

```
func TestSVGWriterHourHand(t *testing.T) {
    cases := []struct {
        time time.Time
        line Line
    }{
        {
            simpleTime(6, 0, 0),
            Line{150, 150, 150, 200},
        },
    }

    for _, c := range cases {
        t.Run(testName(c.time), func(t *testing.T) {
            b := bytes.Buffer{}
            clockface.SVGWriter(&b, c.time)

            svg := SVG{}
            xml.Unmarshal(b.Bytes(), &svg)
```
```
if !containsLine(c.line, svg.Line) {
    t.Errorf("Expected to find the hour hand line %+")
}
})
}
}
```

## Try to run the test

clockface_acceptance_test.go:113: Expected to find the hour hand line {X1:150 Y1:150 X2:150 Y2:200}, in the SVG lines [{X1:150 Y1:150 X2:150 Y2:60} {X1:150 Y1:150 X2:150 Y2:70}]

Again, let's comment this one out until we've got the some coverage with the lower level tests:

## Write the test first

```
func TestHoursInRadians(t *testing.T) {
    cases := []struct {
        time  time.Time
        angle float64
    }{
        {simpleTime(6, 0, 0), math.Pi},
    }

    for _, c := range cases {
        t.Run(testName(c.time), func(t *testing.T) {
            got := hoursInRadians(c.time)
            if got != c.angle {
                t.Fatalf("Wanted %v radians, but got %v", c.angle
            }
        })
    }
}
```

## Try to run the test

./clockface_test.go:97:11: undefined: hoursInRadians

## Write the minimal amount of code for the test to run and check the failing test output

```
```go
func hoursInRadians(t time.Time) float64 {
	return math.Pi
}
```
```

PASS
ok	clockface	0.007s

## Repeat for new requirements

```
```go
func TestHoursInRadians(t *testing.T) {
	cases := [][]struct {
		time time.Time
		angle float64
	}{
		{simpleTime(6, 0, 0), math.Pi},
		{simpleTime(0, 0, 0), 0},
	}

	for _, c := range cases {
		t.Run(testName(c.time), func(t *testing.T) {
			got := hoursInRadians(c.time)
			if got != c.angle {
				t.Fatalf("Wanted %v radians, but got %v", c.angle)
			}
		})
	}
}
```
```

## Try to run the test

clockface_test.go:100: Wanted 0 radians, but got 3.141592653589793

## Write enough code to make it pass

```
~~~go
func hoursInRadians(t time.Time) float64 {
    return (math.Pi / (6 / float64(t.Hour())))
}
~~~
```

## Repeat for new requirements

```
~~~go
func TestHoursInRadians(t *testing.T) {
    cases := []struct {
        time  time.Time
        angle float64
    }{
        {simpleTime(6, 0, 0), math.Pi},
        {simpleTime(0, 0, 0), 0},
        {simpleTime(21, 0, 0), math.Pi * 1.5},
    }

    for _, c := range cases {
        t.Run(testName(c.time), func(t *testing.T) {
            got := hoursInRadians(c.time)
            if got != c.angle {
                t.Fatalf("Wanted %v radians, but got %v", c.angle
            }
        })
    }
}
~~~
```

## Try to run the test

```
~~~text
clockface_test.go:101: Wanted 4.71238898038469 radians, but got
10.995574287564276
~~~
```

## Write enough code to make it pass

```
~~~go
func hoursInRadians(t time.Time) float64 {
    return (math.Pi / (6 / (float64(t.Hour() % 12))))
}
~~~
```

Remember, this is not a 24-hour clock; we have to use the remainder operator to get the remainder of the current hour divided by 12.

```
PASS
ok	tests/math/v10/clockface	github.com/gypsydave5/learn-go-with-
0.008s
```

## Write the test first

Now let's try to move the hour hand around the clockface based on the minutes and the seconds that have passed.

```
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
            if got != c.angle {
                t.Fatalf("Wanted %v radians, but got %v", c.angle
            }
        })
    }
}
```

## Try to run the test

```
clockface_test.go:102: Wanted 0.013089969389957472 radians, but got 0
```

## Write enough code to make it pass

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
}
    })
}
}
```

PASS
ok	clockface	0.007s

## Refactor

If we're going to use `roughlyEqualFloat64` in *one* of our radians tests, we should probably use it for *all* of them. That's a nice and simple refactor, which will leave things [looking like this]().

## Hour Hand Point

Right, it's time to calculate where the hour hand point is going to go by working out the unit vector.

## Write the test first

```
```go
func TestHourHandPoint(t *testing.T) {
    cases := []struct {
        time  time.Time
        point Point
    }{
        {simpleTime(6, 0, 0), Point{0, -1}},
        {simpleTime(21, 0, 0), Point{-1, 0}},
    }

    for _, c := range cases {
        t.Run(testName(c.time), func(t *testing.T) {
            got := hourHandPoint(c.time)
            if !roughlyEqualPoint(got, c.point) {
                t.Fatalf("Wanted %v Point, but got %v", c.point,
            }
        })
    }
```
```
