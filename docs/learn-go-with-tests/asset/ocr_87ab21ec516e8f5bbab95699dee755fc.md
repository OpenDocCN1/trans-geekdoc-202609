```
type Line struct {
    X1 float64 `xml:"x1,attr"`
    Y1 float64 `xml:"y1,attr"`
    X2 float64 `xml:"x2,attr"`
    Y2 float64 `xml:"y2,attr"`
}
```

Here I've

+   - Made the important parts of the struct named types -- the `Line` and the `Circle`
+   - Turned the numeric attributes into `float64`s instead of `string`s.
+   - Deleted unused attributes like `Style` and `Text`
+   - Renamed `Svg` to `SVG` because it's *the right thing to do*.

This will let us assert more precisely on the line we're looking for:

```
func TestSVGWriterAtMidnight(t *testing.T) {
    tm := time.Date(1337, time.January, 1, 0, 0, 0, 0, time.UTC)
    b := bytes.Buffer{}

    clockface.SVGWriter(&b, tm)

    svg := SVG{}

    xml.Unmarshal(b.Bytes(), &svg)

    want := Line{150, 150, 150, 60}

    for _, line := range svg.Line {
        if line == want {
            return
        }
    }

    t.Errorf("Expected to find the second hand line %+v, in the s")
}
```

Finally we can take a leaf out of the unit tests' tables, and we can write a helper function `containsLine(line Line, lines []Line) bool`