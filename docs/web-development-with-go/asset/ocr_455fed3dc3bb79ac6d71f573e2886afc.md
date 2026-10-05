# 16.6. CONFIGURING OUR APPLICATION

Moving forward we will need to run and build our application by providing all of the source files in our main package as arguments, but we will also be able to provide all of these variables via configurations!

```
$ go run *.go
```

This tells us code that we need to build multiple Go files, not just main.go, when building and running our program.

# Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/16.6.1

Changes - book.usegolang.com/16.6.1-diff

# 16.6.2 Using functional options

We need a way to provide config variables to our services when building them. Whenever we setup our UserService, we want to provide it with things like the password pepper and an HMAC secret key, but our current code design doesn't allow for that.

One way to do this is to add all in as arguments to the NewServices function wrote, but by doing this we will quickly end up with a long list of arguments required for the functions.

```
// And this list will only grow in size!
func NewServices(dialect, connectionInfo, pepper, hmacKey string,
logMode bool) (*Services, error) {
```