
“enough” equality for our angles. But there’s a simple way we can get the accuracy back: we rearrange the equation so that we’re no longer dividing down and then multiplying up. We can do it all by just dividing.

So instead of

```text
numberOfSeconds * π / 30
```

we can write

```text
π / (30 / numberOfSeconds)
```

which is equivalent.

In Go:

```go
func secondsInRadians(t time.Time) float64 {
    return math.Pi / (30 / float64(t.Second()))
}
```

And we get a pass.

```text
PASS
ok      clockface      0.005s
```

It should all look something like this.

## A note on dividing by zero

Computers often don't like dividing by zero because infinity is a bit strange.

In Go, if you try to explicitly divide by zero, you will get a compilation error.

```go
package main

import (
    "fmt"
)

func main() {
    fmt.Println(10.0 / 0.0) // fails to compile
}
```

Obviously, the compiler can't always predict that you'll divide by zero, such as with our `t.Second()`.

### Try this

```go
func main() {
    fmt.Println(10.0 / zero())
}

func zero() float64 {
    return 0.0
}
```

It will print `+Inf` (infinity). Dividing by `+Inf` seems to result in zero, and we can see this with the following:

```go
package main

import (
    "fmt"
    "math"
)

func main() {
    fmt.Println(secondsInRadians())
}

func zero() float64 {
    return 0.0
}

func secondsInRadians() float64 {
    return math.Pi / (30 / float64(zero()))
}
```

## Repeat for new requirements

So we've got the first part covered here—we know what angle the second hand will be pointing at in radians. Now we need to work out the coordinates.

Again, let's keep this as simple as possible and only work with the unit circle: the circle with a radius of 1. This means that our hands will all have a length of one, but on the bright side, it means that the maths will be easy for us to swallow.

## Write the test first

```go
func TestSecondHandVector(t *testing.T) {
    cases := []struct {
        time  time.Time
        point Point
    }{
        {simpleTime(0, 0, 30), Point{0, -1}},
    }

    for _, c := range cases {
        t.Run(testName(c.time), func(t *testing.T) {
            got := secondHandPoint(c.time)
            if got != c.point {
                t.Fatalf("Wanted %v Point, but got %v", c.point, got)
            }
        })
    }
}
```

## Try to run the test

```text
./clockface_test.go:40:11: undefined: secondHandPoint
```

## Write the minimal amount of code for the test to run and check the failing test output

```go
func secondHandPoint(t time.Time) Point {
    return Point{}
}
```

```text
clockface_test.go:42: Wanted {0 -1} Point, but got {0 0}
```

## Write enough code to make it pass

```go
func secondHandPoint(t time.Time) Point {
    return Point{0, -1}
}
```

```text
PASS
ok      clockface   0.007s
```

## Repeat for new requirements

```go
func TestSecondHandPoint(t *testing.T) {
    cases := []struct {
        time  time.Time
        point Point
    }{
        {simpleTime(0, 0, 30), Point{0, -1}},
        {simpleTime(0, 0, 45), Point{-1, 0}},
    }

    for _, c := range cases {
        t.Run(testName(c.time), func(t *testing.T) {
            got := secondHandPoint(c.time)
            if got != c.point {
                t.Fatalf("Wanted %v Point, but got %v", c.point, got)
            }
        })
    }
}
```

### Try to run the test

```text
clockface_test.go:43: Wanted {-1 0} Point, but got {0 -1}
```

## Write enough code to make it pass

Remember our unit circle picture?

![](img/570fb0b5bd524332c8e0fb9e37d716fb_280_0.png)

Also recall that we want to measure the angle from 12 o'clock, which is the Y axis, instead of from the X axis, which would mean measuring the angle between the second hand and 3 o'clock.

![](img/570fb0b5bd524332c8e0fb9e37d716fb_281_0.png)

We now want the equation that produces X and Y. Let's write it into seconds:

```go
func secondHandPoint(t time.Time) Point {
    angle := secondsInRadians(t)
    x := math.Sin(angle)
    y := math.Cos(angle)

    return Point{x, y}
}
```

## Now we get

```text
clockface_test.go:43: Wanted {0 -1} Point, but got {1.2246467991473515e-16 -1}

clockface_test.go:43: Wanted {-1 0} Point, but got {-1 -1.8369701987210272e-16}
```

Wait, what (again)? Looks like we've been cursed by the floats once more—both of those unexpected numbers are infinitesimal, way down at the 16th decimal place. So again, we can either choose to try to increase precision or just say that they're roughly equal and get on with our lives.

One option to increase the accuracy of these angles would be to use the rational type `Rat` from the `math/big` package. But given the objective is to draw an SVG and not land on the moon, I think we can live with a bit of fuzziness.

```go
func TestSecondHandPoint(t *testing.T) {
    cases := []struct {
        time  time.Time
        point Point
    }{
        {simpleTime(0, 0, 30), Point{0, -1}},
        {simpleTime(0, 0, 45), Point{-1, 0}},
    }

    for _, c := range cases {
        t.Run(testName(c.time), func(t *testing.T) {
            got := secondHandPoint(c.time)
            if !roughlyEqualPoint(got, c.point) {
                t.Fatalf("Wanted %v Point, but got %v", c.point, got)
            }
        })
    }
}
```

```go
func roughlyEqualFloat64(a, b float64) bool {
    const equalityThreshold = 1e-7
    return math.Abs(a-b) < equalityThreshold
}
```

```go
func roughlyEqualPoint(a, b Point) bool {
    return roughlyEqualFloat64(a.X, b.X) &&
        roughlyEqualFloat64(a.Y, b.Y)
}
```

We've defined two functions to define approximate equality between two Points—they'll work if the X and Y elements are within 0.0000001 of each other. That's still pretty accurate.

And now we get:

```text
PASS
ok      clockface   0.007s
```

## Refactor

I'm still pretty happy with this.

Here's what it looks like now.

## Repeat for new requirements

Well, saying “new” isn't entirely accurate—really, what we can do now is get that acceptance test passing! Let's remind ourselves of what it looks like:

```go
func TestSecondHandAt30Seconds(t *testing.T) {
    tm := time.Date(1337, time.January, 1, 0, 0, 30, 0, time.UTC)

    want := clockface.Point{X: 150, Y: 150 + 90}
    got := clockface.SecondHand(tm)

    if got != want {
        t.Errorf("Got %v, wanted %v", got, want)
    }
}
```

### Try to run the test

```text
clockface_acceptance_test.go:28: Got {150 60}, wanted {150 240}
```

## Write enough code to make it pass

We need to do three things to convert our unit vector into a point on the SVG:

- Scale it to the length of the hand.
- Flip it over the X axis to account for the SVG having an origin in the top-left-hand corner.
- Translate it to the right position (so that it's coming from an origin of (150,150)).

Fun times!

```go
// SecondHand is the unit vector of the second hand of an analogue clock
// represented as a Point.
func SecondHand(t time.Time) Point {
    p := secondHandPoint(t)
    p = Point{p.X * 90, p.Y * 90}    // scale
    p = Point{p.X, -p.Y}             // flip
    p = Point{p.X + 150, p.Y + 150} // translate
    return p
}
```

Scale, flip, and translate in exactly that order. Hooray, maths!

```text
PASS
ok      clockface  0.007s
```

## Refactor

There's a few magic numbers here that should get pulled out as constants, so let's do that.

```go
const secondHandLength = 90
const clockCentreX = 150
const clockCentreY = 150
```

```go
// SecondHand is the unit vector of the second hand of an analogue clock
// represented as a Point.
func SecondHand(t time.Time) Point {
    p := secondHandPoint(t)
    p = Point{p.X * secondHandLength, p.Y * secondHandLength}
    p = Point{p.X, -p.Y}
    p = Point{p.X + clockCentreX, p.Y + clockCentreY} // translate
    return p
}
```

## Draw the clock

Well... the second hand, anyway...

Let's do this thing—because there's nothing worse than not delivering some value when it's just sitting there waiting to get out into the world to dazzle people. Let's draw a second hand!

We're going to stick a new directory under our main clockface package directory, called (confusingly) `clockface`. In there, we'll put the main package that will create the binary that will build an SVG:

```text
|-- clockface
|   |-- main.go
|-- clockface.go
|-- clockface_acceptance_test.go
|-- clockface_test.go
```

Inside `main.go`, you'll start with this code, but change the import for the clockface package to point at your own version:

```go
package main

import (
    "fmt"
    "io"
    "os"
    "time"

    "github.com/quii/learn-go-with-tests/math/clockface" // REPL.
)

func main() {
    t := time.Now()
```
