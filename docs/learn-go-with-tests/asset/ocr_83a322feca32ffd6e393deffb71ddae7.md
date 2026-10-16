# On testing 3rd-party libraries

Note. Be careful not to worry too much about explicitly testing how a 3rd party library behaves in unit tests.

Writing tests against code you don't control is wasteful and adds maintenance overhead. Sometimes you may wish to use dependency injection to control a dependency and mock its behaviour for a test.

In this case though, I view converting the markdown into HTML as implementation detail of rendering, and our approval tests should give us enough confidence.

# Render index

The next bit of functionality we're going to do is rendering an Index, listing the posts as a HTML ordered list.

We're expanding upon our API, so we'll put our TDD hat back on.

# Write the test first

On the face of it an index page seems simple, but writing the test still prompts us to make some design choices

```
t.Run("it renders an index of posts", func(t *testing.T) {
    buf := bytes.Buffer{}
    posts := []blogrenderer.Post{{Title: "Hello World"}, {Title:

    if err := postRenderer.RenderIndex(&buf, posts); err != nil
        t.Fatal(err)
    }

    got := buf.String()
    want := `<ol><li><a href="/post/hello-world">Hello World</a>`

    if got != want {
```