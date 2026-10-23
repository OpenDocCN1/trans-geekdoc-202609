> **Remember:** Boolean command-line flags *without a value* are interpreted as having the value `true`. So running our application with `-version` is the same as running it with `-version=true`.

# Including the build time

Let’s extend this further, so that the `-version` flag forces our application to print out the version number *and* the exact time that the executable binary was built. Similar to this:

```
$ ./bin/api -version
Version:      1.0.0
Build time:   2021-02-15T13:54:14+01:00
```

This is a really interesting change, because the build time is a completely dynamic value and *outside the control of our application code*. We don’t know the build time *in advance* of calling `go build`, and therefore it’s not something that we can define in our source code in the normal way.

To make this work, we’ll need to use a special feature of `go build` — the `-X` linker flag which allows you to assign or ‘burn-in’ a value to a variable when running `go build`. Specifically, we’ll generate a string containing the current date and time in our makefile, and then ‘burn this in’ to the binary as part of our `make build/api` rule.

I’ll demonstrate.