with specific form data in the request body.

Go ahead and add the following code (which follows the same general pattern that we used for the get() method earlier in the book):

```
File: cmd/web/testutils_test.go

package main

import (
	"bytes"
	"html"
	"io"
	"log/slog"
	"net/http"
	"net/http/cookiejar"
	"net/http/httptest"
	"net/url" // New import
	"regexp"
	"testing"
	"time"

	"snippetbox.alexedwards.net/internal/models/mocks"

	"github.com/alexedwards/scs/v2"
	"github.com/go-playground/form/v4"
)

...

// Create a postForm method for sending POST requests to the test server. The
// final parameter to this method is a url.Values object which can contain any
// form data that you want to send in the request body.
func (ts *testServer) postForm(t *testing.T, urlPath string, form url.Values) (int, http.Header, string) {
	rs, err := ts.Client().PostForm(ts.URL+urlPath, form)
	if err != nil {
		t.Fatal(err)
	}

	// Read the response body from the test server.
	defer rs.Body.Close()
	body, err := io.ReadAll(rs.Body)
	if err != nil {
		t.Fatal(err)
	}
	body = bytes.TrimSpace(body)

	// Return the response status, headers and body.
	return rs.StatusCode, rs.Header, string(body)
}
```

And now, at last, we’re ready to add some table-driven sub-tests to test the behavior of our application’s POST /user/signup route. Specifically, we want to test that:

+   • A valid signup results in a 303 See Other response.
+   • A form submission without a valid CSRF token results in a 400 Bad Request response.
+   • A invalid form submission results in a 422 Unprocessable Entity response and the