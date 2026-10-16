We finally have a compiling program but it is not meeting our requirements according to the test.

Let's make the test pass by using the name argument and concatenate it with Hello,

```
func Hello(name string) string {
    return "Hello, " + name
}
```

When you run the tests they should now pass. Normally as part of the TDD cycle we should now *refactor*.

# A note on source control

At this point, if you are using source control (which you should!) I would commit the code as it is. We have working software backed by a test.

I *wouldn't* push to master though, because I plan to refactor next. It is nice to commit at this point in case you somehow get into a mess with refactoring - you can always go back to the working version.

There's not a lot to refactor here, but we can introduce another language feature, *constants*.

# Constants

Constants are defined like so

```
const englishHelloPrefix = "Hello, "
```

We can now refactor our code

```
const englishHelloPrefix = "Hello, "
```

```
func Hello(name string) string {
```