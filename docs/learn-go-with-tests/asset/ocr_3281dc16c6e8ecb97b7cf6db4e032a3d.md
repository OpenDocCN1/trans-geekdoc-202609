```
Tags: tdd, go
---
Hello
World`
    secondBody = `Title: Post 2
Description: Description 2
Tags: rust, borrow-checker
---
B
L
M`
)
```

Add to our assertion like the others

```
assertPost(t, posts[0], blogposts.Post{
    Title:       "Post 1",
    Description: "Description 1",
    Tags:        []string{"tdd", "go"},
    Body: `Hello
World`,
})
```

# Try to run the test

```
./blogpost_test.go:60:3: unknown field 'Body' in struct literal of type blogposts.Post
```

As we'd expect.

# Write the minimal amount of code for the test to run and check the failing test output

Add Body to Post and the test should fail.