It should fail, complaining it doesn't have the string we expect, as we're not rendering the description and tags.

# Write enough code to make it pass

Try and do this yourself rather than copying the code. What you should find is that making this test pass is a bit annoying! When I tried, my first attempt got this error

```
=== RUN   TestRenderer
=== RUN   TestRenderer/it_converts_a_single_post_into_HTML
    renderer_test.go:32: got '<h1>hello world</h1><p>This is a description</p><ul><li>go</li><li>tdd</li></ul>' want '<h1>hello world</h1>
    <p>This is a description</p>
    Tags: <ul><li>go</li><li></li></ul>'
```

New lines! Who cares? Well, our test does, because it's matching on an exact string value. Should it? I removed the newlines for now just to get the test passing.

```
```go
func Render(w io.Writer, p Post) error {
    _, err := fmt.Fprintf(w, "<h1>%s</h1><p>%s</p>", p.Title, p.I
    if err != nil {
        return err
    }

    _, err = fmt.Fprint(w, "Tags: <ul>")
    if err != nil {
        return err
    }

    for _, tag := range p.Tags {
        _, err = fmt.Fprintf(w, "<li>%s</li>", tag)
        if err != nil {
            return err
        }
    }

    _, err = fmt.Fprint(w, "</ul>")
}
```
```