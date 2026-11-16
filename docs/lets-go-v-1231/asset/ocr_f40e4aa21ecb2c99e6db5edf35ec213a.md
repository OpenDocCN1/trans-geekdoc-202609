# # Mocking dependencies

Now that we've explained some general patterns for testing your web application, in this chapter we're going to get a bit more serious and write some tests for our GET /snippet/view/{id} route.

But first, let's talk about dependencies.

Throughout this project we've injected dependencies into our handlers via the application struct, which currently looks like this:

```
```go
type application struct {
	logger			*slog.Logger
	snippets		*models.SnippetModel
	users			*models.UserModel
	templateCache	map[string]*template.Template
	formDecoder		*form.Decoder
	sessionManager	*scs.SessionManager
}
```
```

When testing, it sometimes makes sense to mock these dependencies instead of using exactly the same ones that you do in your production application.

For example, in the previous chapter we mocked the logger dependency with a logger that write messages to io.Discard, instead of the os.Stdout and stream like we do in our production application:

```
```go
func newTestApplication(t *testing.T) *application {
	return &application{
		logger: slog.New(slog.NewTextHandler(io.Discard, nil)),
	}
}
```
```

The reason for mocking this and writing to io.Discard is to avoid clogging up our test output with unnecessary log messages when we run go test -v (with verbose mode enabled).