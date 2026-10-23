The important thing to look at here is the `GOPROXY` setting, which contains a comma-separated list of module mirrors. By default it has the following value:

```
GOPROXY="https://proxy.golang.org,direct"
```

The URL `https://proxy.golang.org` that we see here points to a *module mirror* maintained by the Go team at Google, containing copies of the source code from tens of thousands of open-source Go packages.

Whenever you fetch a package using the `go` command — either with `go get` or one of the `go mod *` commands — it will first attempt to retrieve the source code from this mirror.

If the mirror already has a stored copy of the source code for the required package and version number, then it will return this code immediately in a zip file. Otherwise, if it’s not already stored, then the mirror will attempt to fetch the code from the authoritative repository, proxy it onwards to you, and store it for future use.

If the mirror can’t fetch the code at all, then it will return an error response and the `go` tool will fall back to fetching a copy directly from the authoritative repository (thanks to the `direct` directive in the `GOPROXY` setting).

Using a module mirror as the first fetch location has a few benefits: