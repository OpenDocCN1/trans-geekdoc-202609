# Write the test first

Let's extend our test further to extract the next line from the file, the description. Up until making it pass should now feel comfortable and familiar.

```
```go
func TestNewBlogPosts(t *testing.T) {
    const (
        firstBody = `Title: Post 1
Description: Description 1`
        secondBody = `Title: Post 2
Description: Description 2`
    )

    fs := fstest.MapFS{
        "hello world.md":  {Data: []byte(firstBody)},
        "hello-world2.md": {Data: []byte(secondBody)},
    }

    // rest of test code cut for brevity
    assertPost(t, posts[0], blogposts.Post{
        Title:       "Post 1",
        Description: "Description 1",
    })
}
```
```

# Try to run the test

./blogpost_test.go:47:58: unknown field 'Description' in struct literal of type blogposts.Post

# Write the minimal amount of code for the test to run and check the failing test output