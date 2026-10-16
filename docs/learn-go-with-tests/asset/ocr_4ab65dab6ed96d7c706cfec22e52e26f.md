# Structs, methods & interfaces

You can find all the code for this chapter here

Suppose that we need some geometry code to calculate the perimeter of a rectangle given a height and width. We can write a `Perimeter(width float64, height float64)` function, where `float64` is for floating-point numbers like `123.45`.

The TDD cycle should be pretty familiar to you by now.

# Write the test first

```
func TestPerimeter(t *testing.T) {
    got := Perimeter(10.0, 10.0)
    want := 40.0

    if got != want {
        t.Errorf("got %.2f want %.2f", got, want)
    }
}
```

Notice the new format string? The `f` is for our `float64` and the `.2` means print 2 decimal places.

# Try to run the test

```
./shapes_test.go:6:9: undefined: Perimeter
```

# Write the minimal amount of code for the test to run and check the failing