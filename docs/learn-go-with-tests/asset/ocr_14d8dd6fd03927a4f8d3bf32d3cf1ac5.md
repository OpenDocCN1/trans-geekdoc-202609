clockface_test.go:24: Wanted 0 radians, but got 3.141592653589793

clockface_test.go:24: Wanted 4.71238898038469 radians, but got 3.141592653589793

Time to implement all of that maths stuff we were talking about above:

```
```go
func secondsInRadians(t time.Time) float64 {
    return float64(t.Second()) * (math.Pi / 30)
}
```
```

One second is (2π / 60) radians... cancel out the 2 and we get π/30 radians. Multiply that by the number of seconds (as a float64) and we should now have all the tests passing...

clockface_test.go:24: Wanted 3.141592653589793 radians, but got 3.1415926535897936

Wait, what?

# Floats are horrible

Floating point arithmetic is notoriously_inaccurate. Computers can only really handle integers, and rational numbers to some extent. Decimal numbers start to become inaccurate, especially when we factor them up and down as we are in the secondsInRadians function. By dividing math.Pi by 30 and then by multiplying it by 30 we've ended up with a number that's no longer the same as math.Pi.

There are two ways around this:

+   1. Live with it
+   2. Refactor our function by refactoring our equation

Now (1) may not seem all that appealing, but it's often the only way to make floating point equality work. Being inaccurate by some infinitesimal fraction is frankly not going to matter for the purposes of drawing a clockface, so we could write a function that defines a 'close