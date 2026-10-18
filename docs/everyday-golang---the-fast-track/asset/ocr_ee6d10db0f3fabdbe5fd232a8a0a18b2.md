The fourth option we’ll look at is what I would use if I wanted to ship something like a React.js front-end along with a HTTP server or API written in Go.

```
```go
import "embed"

// frontend holds our static web server content.
//go:embed image/* template/*
//go:embed public/index.html
//go:embed css/*
var frontend embed.FS
```
```

Now you can simply link the embed.FS to a custom HTTP middleware or handler and serve the files to users from a specific route or path. You’ll learn more about HTTP servers later in the book, however this is the example given in the Go documentation:

```
```go
http.Handle("/public/",
	http.StripPrefix("/public/",
		http.FileServer(http.FS(frontend))))
```
```

Your API could be bound to the path /api/v1/ and then any static content you have embedded would be served from /public/.