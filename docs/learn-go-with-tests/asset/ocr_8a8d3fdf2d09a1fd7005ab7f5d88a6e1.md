```
if got != want {
    t.Errorf("got %.2f want %.2f", got, want)
}
}
```

```
func TestArea(t *testing.T) {
    rectangle := Rectangle{12.0, 6.0}
    got := Area(rectangle)
    want := 72.0

    if got != want {
        t.Errorf("got %.2f want %.2f", got, want)
    }
}
```

Remember to run your tests before attempting to fix. The tests should show a helpful error like

```
./shapes_test.go:7:18:  not enough arguments in call to Perimeter
    have (Rectangle)
    want (float64, float64)
```

You can access the fields of a struct with the syntax of myStruct.field.

Change the two functions to fix the test.

```
func Perimeter(rectangle Rectangle) float64 {
    return 2 * (rectangle.Width + rectangle.Height)
}
```

```
func Area(rectangle Rectangle) float64 {
    return rectangle.Width * rectangle.Height
}
```

I hope you'll agree that passing a Rectangle to a function conveys our intent more clearly, but there are more benefits of using structs that we will cover later.

Our next requirement is to write an Area function for circles.