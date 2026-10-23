when running `go build`. Alternatively, you could use `go clean` to purge the cache:

```
$ go build -a -o=/bin/foo ./cmd/foo      # Force all packages to be rebuilt
$ go clean -cache                      # Remove everything from the build cache
```

> **Note:** If you ever run `go build` on a non-`main` package, the build output will be stored in the build cache so it can be reused, but no executable will be produced.