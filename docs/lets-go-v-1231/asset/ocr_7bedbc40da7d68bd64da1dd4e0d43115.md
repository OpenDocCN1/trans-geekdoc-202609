To make these changes, let's go back to the testutils_test.go file we just created and update the newTestServer() function like so:

```
File: cmd/web/testutils_test.go

package main

import (
	"bytes"
	"io"
	"log/slog"
	"net/http"
	"net/http/cookiejar" // New import
	"net/http/httptest"
	"testing"
)

...

func newTestServer(t *testing.T, h http.Handler) *testServer {
	// Initialize the test server as normal.
	ts := httptest.NewTLSServer(h)

	// Initialize a new cookie jar.
	jar, err := cookiejar.New(nil)
	if err != nil {
		t.Fatal(err)
	}

	// Add the cookie jar to the test server client. Any response cookies will
	// now be stored and sent with subsequent requests when using this client.
	ts.Client().Jar = jar

	// Disable redirect-following for the test server client by setting a custom
	// CheckRedirect function. This function will be called whenever a 3xx
	// response is received by the client, and by always returning a
	// http.ErrUseLastResponse error it forces the client to immediately return
	// the received response.
	ts.Client().CheckRedirect = func(req *http.Request, via []*http.Request) error {
	return http.ErrUseLastResponse
	}

	return &testServer{ts}
}

...
```