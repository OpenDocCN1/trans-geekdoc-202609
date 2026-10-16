Yeah, I guess I screwed up. This feels wrong. Let's try to recover with a more SVG-centric test.

What are our options? Well, we could try testing that the characters spewing out of the SVGWriter contain things that look like the sort of SVG tag we're expecting for a particular time. For instance:

```
```go
func TestSVGWriterAtMidnight(t *testing.T) {
    tm := time.Date(1337, time.January, 1, 0, 0, 0, 0, time.UTC)

    var b strings.Builder
    clockface.SVGWriter(&b, tm)
    got := b.String()

    want := `<line x1="150" y1="150" x2="150" y2="60"`

    if !strings.Contains(got, want) {
        t.Errorf("Expected to find the second hand %v, in the SVG
    }
}
```
```

But is this really an improvement?

Not only will it still pass if I don't produce a valid SVG (as it's only testing that a string appears in the output), but it will also fail if I make the smallest, unimportant change to that string - if I add an extra space between the attributes, for instance.

The biggest smell is that I'm testing a data structure - XML - by looking at its representation as a series of characters - as a string. This is never, ever a good idea as it produces problems just like the ones I outline above: a test that's both too fragile and not sensitive enough. A test that's testing the wrong thing!

So the only solution is to test the output as XML. And to do that we'll need to parse it.

# Parsing XML