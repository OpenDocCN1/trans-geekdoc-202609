
serve dot-prefixed files or traverse dot-prefixed directories.

The net/http package documentation includes an example of an http.FileSystem that prevents the http.FileServer from serving dot-prefixed files and directories. Listing 9-13 takes a different approach by using middleware to offer the same protection.

package middleware

import (

"net/http"

"path"

`204` Chapter 9

"strings"

)

func RestrictPrefix(prefix string, next http.Handler) http.Handler {

return http.HandlerFunc(

func(w http.ResponseWriter, r \*http.Request) {

for _, p := range strings.Split(path.Clean(r.URL.Path), "/") {

if strings.HasPrefix(p, prefix) {

http.Error(w, "Not Found", http.StatusNotFound)

return

}

}

next.ServeHTTP(w, r)

},

)

}

*Listing 9-13: Protecting any file or directory with a given prefix (* middleware/restrict_prefix .go *).*

The RestrictPrefix middleware examines the URL path to look for any elements that start with a given prefix. If the middleware finds an element in the URL path with the given prefix, it preempts the http.Handler and responds with a 404 Not Found status.

Listing 9-14 uses the RestrictPrefix middleware with a series of test cases.

package middleware

import (

"net/http"

"net/http/httptest"

"testing"

)

func TestRestrictPrefix(t \*testing.T) {

handler := http.StripPrefix("/static/",

RestrictPrefix(".", http.FileServer(http.Dir("../files/"))),

)

testCases := []struct {

path string

code int

}{
{"http://test/static/sage.svg", http.StatusOK},
{"http://test/static/.secret", http.StatusNotFound},
{"http://test/static/.dir/secret", http.StatusNotFound},
}

for i, c := range testCases {

r := httptest.NewRequest(http.MethodGet, c.path, nil)

w := httptest.NewRecorder()

handler.ServeHTTP(w, r)

actual := w.Result().StatusCode

if c.code != actual {

t.Errorf("%d: expected %d; actual %d", i, c.code, actual)

}

}

}

*Listing 9-14: Using the RestrictPrefix middleware (* middleware/restrict_prefix_test .go *)* It’s important to realize the server first passes the request to the http.StripPrefix middleware, then the RestrictPrefix middleware, and if the RestrictPrefix middleware approves the resource path, the http.FileServer. The RestrictPrefix middleware evaluates the request’s resource path to determine whether the client is requesting a restricted path, no matter whether the path exists or not. If so, the RestrictPrefix middleware responds to the client with an error without ever passing the request onto the http.FileServer.

The static files served by this test’s http.FileServer exist in a directory named files in the restrict_prefix_test.go file’s parent directory. Files in the ../files directory are in the root of the filesystem passed to the http.FileServer.

For example, the ../files/sage.svg file on the operating system’s filesystem is at /sage.svg in the http.FileSystem passed to the http.FileServer. If a client wanted to retrieve the sage.svg file from the http.FileServer, the request path should be /sage.svg.

But the URL path for each of our test cases includes the /static/ prefix followed by the static filename. This means that the test requests static/sage.svg from the http.FileServer, which doesn’t exist. The test uses another bit of middleware from the net/http package to solve this path discrepancy.

The http.StripPrefix middleware strips the given prefix from the URL path before passing along the request to the http.Handler, the http.FileServer in this test.

Next, you block access to sensitive files by wrapping the http.FileServer with the RestrictPrefix middleware to prevent the handler from serving any file or directory prefixed with a period. The first test case results in a 200 OK status, because no element in the URL path has a period prefix.

The http.StripPrefix middleware removes the /static/ prefix from the test case’s URL, changing it from /static/sage.svg to sage.svg. It then passes this path to the http.FileServer, which finds the corresponding file in its http.FileSystem. The http.FileServer writes the file contents to the response body.

The second test case results in a 404 Not Found status because the .secret filename has a period as its first character. The third case also results in a 404 Not Found status due to the .dir element in the URL path, because your RestrictPrefix middleware considers the prefix of each segment in the path, not just the file.

A better approach to restricting access to resources would be to block all resources by default and explicitly allow select resources. As an exercise, try implementing the inverse of the RestrictPrefix middleware by creating middleware that permits requests for only an allowed list of resources.

**206** Chapter 9

**Multiplexers**

One afternoon, I walked into the University of Michigan’s library, the fourth largest library in the United States. I was looking for a well-worn copy of Kurt Vonnegut’s *Cat’s Cradle* and had no idea where to start my search. I found the nearest librarian and asked for help finding the book.

When we arrived at the correct location, the book was 404 Not Found.

A *multiplexer*, like the friendly librarian routing me to the proper book-shelf, is a general handler that routes a request to a specific handler. The http.ServeMux multiplexer is an http.Handler that routes an incoming request to the proper handler for the requested resource. By default, http.ServeMux responds with a 404 Not Found status for all incoming requests, but you can use it to register your own patterns and corresponding handlers. It will then compare the request’s URL path with its registered patterns, passing the request and response writer to the handler that corresponds to the longest matching pattern.

Listing 9-1 used a multiplexer to send all requests to a single endpoint.

Listing 9-15 introduces a slightly more complex multiplexer that has three endpoints. This one evaluates the requested resource and routes the request to the right endpoint.

package main

import (

"fmt"

"io"

"io/ioutil"

"net/http"

"net/http/httptest"

"testing"

)

func drainAndClose(next http.Handler) http.Handler {

return http.HandlerFunc(

func(w http.ResponseWriter, r \*http.Request) {

next.ServeHTTP(w, r)

_, _ = io.Copy(ioutil.Discard, r.Body)

\_ = r.Body.Close()

},

)

}

func TestSimpleMux(t \*testing.T) {

serveMux := http.NewServeMux()

serveMux.HandleFunc("/", func(w http.ResponseWriter, r \*http.Request) {

w.WriteHeader(http.StatusNoContent)

})

serveMux.HandleFunc("/hello", func(w http.ResponseWriter,

r \*http.Request) {

\_, \_ = fmt.Fprint(w, "Hello friend.")

})

serveMux.HandleFunc("/hello/there/", func(w http.ResponseWriter,

r \*http.Request) {

\_, \_ = fmt.Fprint(w, "Why, hello there.")

})

mux := drainAndClose(serveMux)

*Listing 9-15: Registering patterns to a multiplexer and wrapping the entire multiplexer with* *middleware (* mux_test .go *).*

The test creates a new multiplexer and registers three routes using the multiplexer’s HandleFunc method. The first route is simply a forward slash, showing the default or empty URL path, and a function that sets the 204 No Content status in the response. This route will match all URL paths if no other route matches. The second is /hello, which writes the string Hello friend. to the response. The final path is /hello/there/, which writes the string Why, hello there. to the response.

Notice that the third route ends in a forward slash, making it a subtree, while the earlier route did not end in a forward slash, making it an absolute path. This distinction tends to be a bit confusing for unaccustomed users. Go’s multiplexer treats absolute paths as exact matches: either the request’s URL path matches, or it doesn’t. By contrast, it treats subtrees as
