
```
File: cmd/web/handlers_test.go

package main

import (
	"bytes"
	"io"
	"log/slog" // New import
	"net/http"
	"net/http/httptest"
	"testing"

	"snippetbox.alexedwards.net/internal/assert"
)

func TestPing(t *testing.T) {
	// Create a new instance of our application struct. For now, this just
	// contains a structured logger (which discards anything written to it).
	app := &application{
		logger: slog.New(slog.NewTextHandler(io.Discard, nil)),
	}

	// We then use the httptest.NewTLSServer() function to create a new test
	// server, passing in the value returned from our app.routes() method as
	// the handler for the server. This starts up a HTTP server which listens on a
	// randomly-chosen port of your local machine for the duration of the test.
	// Notice that we defer a call to ts.Close() so that the server is shutdown
	// when the test finishes.
	ts := httptest.NewTLSServer(app.routes())
	defer ts.Close()

	// The network address that the test server is listening on is contained in
	// the ts.URL field. We can use this along with the ts.Client().Get() method
	// to make a GET /ping request against the test server. This returns a
	// http.Response struct containing the response.
	rs, err := ts.Client().Get(ts.URL + "/ping")
	if err != nil {
		t.Fatal(err)
	}

	// We can then check the value of the response status code and body using
	// the same pattern as before.
	assert.Equal(t, rs.StatusCode, http.StatusOK)

	defer rs.Body.Close()
	body, err := io.ReadAll(rs.Body)
	if err != nil {
		t.Fatal(err)
	}
	body = bytes.TrimSpace(body)

	assert.Equal(t, string(body), "OK")
}
```

There are a few things about this code to point out and discuss.

- When we call `httptest.NewTLSServer()` to initialize the test server we need to pass in a `http.Handler` as the parameter — and this handler is called each time the test server receives a HTTPS request. In our case, we’ve passed in the return value from our `app.routes()` method, meaning that a request to the test server will use all our real application routes, middleware and handlers.

This is a big upside of the work that we did earlier in the book to isolate all our application routing in the `app.routes()` method.

- If you’re testing a HTTP (not HTTPS) server you should use the `httptest.NewServer()` function to create the test server instead.

- The `ts.Client()` method returns the test server client — which has the type `http.Client` — and we should always use this client to send requests to the test server. It’s possible to configure the client to tweak its behavior, and we’ll explain how to do that at the end of this chapter.

- You might be wondering why we have set the `logger` field of our application struct, but none of the other fields. The reason for this is that the logger is needed by the `logRequest` and `recoverPanic` middlewares, which are used by our application on every route. Trying to run this test without setting these the two dependencies will result in a panic.

Anyway, let’s try out the new test:

```
$ go test ./cmd/web/
--- FAIL: TestPing (0.00s)
    handlers_test.go:41: got 404; want 200
    handlers_test.go:51: got: Not Found; want: OK
FAIL
FAIL    snippetbox.alexedwards.net/cmd/web    0.007s
```

If you’re following along, you should get a failure at this point.

We can see from the test output that the response from our GET /ping request has a 404 status code, rather than the 200 we expected. And that’s because we haven’t actually registered a GET /ping route with our router yet.

Let’s fix that now:

```
File: cmd/web/routes.go

package main

...

func (app *application) routes() http.Handler {
    mux := http.NewServeMux()

    mux.Handle("GET /static/", http.FileServerFS(ui.Files))

    // Add a new GET /ping route.
    mux.HandleFunc("GET /ping", ping)

    dynamic := alice.New(app.sessionManager.LoadAndSave, noSurf, app.authenticate)

    mux.Handle("GET /{$}", dynamic.ThenFunc(app.home))
    mux.Handle("GET /snippet/view/{id}", dynamic.ThenFunc(app.snippetView))
    mux.Handle("GET /user/signup", dynamic.ThenFunc(app.userSignup))
    mux.Handle("POST /user/signup", dynamic.ThenFunc(app.userSignupPost))
    mux.Handle("GET /user/login", dynamic.ThenFunc(app.userLogin))
    mux.Handle("POST /user/login", dynamic.ThenFunc(app.userLoginPost))

    protected := dynamic.Append(app.requireAuthentication)

    mux.Handle("GET /snippet/create", protected.ThenFunc(app.snippetCreate))
    mux.Handle("POST /snippet/create", protected.ThenFunc(app.snippetCreatePost))
    mux.Handle("POST /user/logout", protected.ThenFunc(app.userLogoutPost))

    standard := alice.New(app.recoverPanic, app.logRequest, commonHeaders)

    return standard.Then(mux)
}
```

And if you run the tests again everything should now pass.

```
$ go test ./cmd/web/
ok  snippetbox.alexedwards.net/cmd/web  0.008s
```

## Using test helpers

Our TestPing test is now working nicely. But there's a good opportunity to break out some of this code into helper functions, which we can reuse as we add more end-to-end tests to our project.

There's no hard-and-fast rules about where to put helper methods for tests. If a helper is only used in a specific `*_test.go` file, then it probably makes sense to include it inline in that file alongside your tests. At the other end of the spectrum, if you are going to use a helper in tests across multiple packages, then you might want to put it in a reusable package called `internal/testutils` (or similar) which can be imported by your test files.

In our case, the helpers will be used for testing code throughout our `cmd/web` package but nowhere else, so it seems reasonable to put them in a new `cmd/web/testutils_test.go` file.

If you’re following along, please go ahead and create this now...

```
`$ touch cmd/web/testutils_test.go`
```

And then add the following code:

```
File: cmd/web/testutils_test.go

package main

import (
	"bytes"
	"io"
	"log/slog"
	"net/http"
	"net/http/httptest"
	"testing"
)

// Create a newTestApplication helper which returns an instance of our
// application struct containing mocked dependencies.
func newTestApplication(t *testing.T) *application {
	return &application{
		logger: slog.New(slog.NewTextHandler(io.Discard, nil)),
	}
}

// Define a custom testServer type which embeds a httptest.Server instance.
type testServer struct {
	*httptest.Server
}

// Create a newTestServer helper which initializes and returns a new instance
// of our custom testServer type.
func newTestServer(t *testing.T, h http.Handler) *testServer {
	ts := httptest.NewTLSServer(h)
	return &testServer{ts}
}

// Implement a get() method on our custom testServer type. This makes a GET
// request to a given url path using the test server client, and returns the
// response status code, headers and body.
func (ts *testServer) get(t *testing.T, urlPath string) (int, http.Header, string) {
	rs, err := ts.Client().Get(ts.URL + urlPath)
	if err != nil {
		t.Fatal(err)
	}

	defer rs.Body.Close()
	body, err := io.ReadAll(rs.Body)
	if err != nil {
		t.Fatal(err)
	}

	body = bytes.TrimSpace(body)

	return rs.StatusCode, rs.Header, string(body)
}
```

Essentially, this is just a generalization of the code that we’ve already written in this chapter to spin up a test server and make a GET request against it.

Let’s head back to our TestPing handler and put these new helpers to work:

```
File: cmd/web/handlers_test.go

package main

import (
	"net/http"
	"testing"

	"snippetbox.alexedwards.net/internal/assert"
)

func TestPing(t *testing.T) {
	app := newTestApplication(t)

	ts := newTestServer(t, app.routes())
	defer ts.Close()

	code, _, body := ts.get(t, "/ping")

	assert.Equal(t, code, http.StatusOK)
	assert.Equal(t, body, "OK")
}
```

And, again, if you run the tests again everything should still pass.

```
$ go test ./cmd/web/
ok   snippetbox.alexedwards.net/cmd/web   0.013s
```

This is shaping up nicely now. We have a neat pattern in place for spinning up a test server and making requests to it, encompassing our routing, middleware and handlers in an end-to-end test. We’ve also broken apart some of the code into helpers, which will make writing future tests quicker and easier.

## Cookies and redirections

So far in this chapter we’ve been using the default test server client settings. But there are a couple of changes I’d like to make so that it’s better suited to testing our web application. Specifically:

- We want the client to automatically store any cookies sent in a HTTPS response, so that we can include them (if appropriate) in any subsequent requests back to the test server. This will come in handy later in the book when we need cookies to be supported across multiple requests in order to test our anti-CSRF measures.

- We don’t want the client to automatically follow redirects. Instead we want it to return the first HTTPS response sent by our server so that we can test the response for that specific request.
