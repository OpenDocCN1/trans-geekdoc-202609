we could stub out the database later by writing a fake UserReader implementation that pretends to read and write from a database, and then use that when testing our validation layer. The code might look something like the code below.

```
var testUser User
type testUserReader struct { }

func (testUserReader) ByID(id uint) (*User, error) {
	if id <= 10 {
		return testUser, nil
}
	return nil, ErrNotFound
}
```

Now when we write tests we would use this UserReader implementation instead of the real one. This is fairly simplistic example, but stubbing out code for tests like this is very helpful when writing maintainable tests in a larger application.

# Box 12.5. When should I use interfaces?

Knowing when to use an interface for these purposes isn’t always obvious. This can be especially confusing if you are coming from a language where you often define many interfaces upfront.

While I can’t give you any specific formula for determining when you should use an interface, what I can tell you is that interfaces in Go are very different from other languages and are fairly easy to add in later. As a result, I typically recommend starting with a struct, and then converting it into an interface later when you see enough evidence that an interface would be easier to use.