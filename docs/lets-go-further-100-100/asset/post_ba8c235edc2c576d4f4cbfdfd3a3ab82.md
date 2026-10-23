
```go
func main() {
    // Make the server address configurable at runtime via a command-line flag.
    addr := flag.String("addr", ":9000", "Server address")
    flag.Parse()

    log.Printf("starting server on %s", *addr)

    // Start a HTTP server listening on the given address, which responds to all
    // requests with the webpage HTML above.
    err := http.ListenAndServe(*addr, http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        w.Write([]byte(html))
    }))
    log.Fatal(err)
}
```

The Go code here should be nice and familiar to you already, but let’s take a closer look at the JavaScript code in the <script> tag and explain what it does.

```html
<script>
    document.addEventListener('DOMContentLoaded', function() {
        fetch("http://localhost:4000/v1/healthcheck").then(
            function (response) {
                response.text().then(function (text) {
                    document.getElementById("output").innerHTML = text;
                });
            },
            function(err) {
                document.getElementById("output").innerHTML = err;
            }
        )
    }
```

> **Note:** I've explained the above because it's interesting, but this book isn't about JavaScript and you don't really need to worry about the details here. All you need to know is that *the JavaScript makes a HTTP request to our API's healthcheck endpoint, and then dumps the response inside the* `<div id="output"></div>` *element.*

## Demonstration

OK, let's try this out. Go ahead and start up the new application:

```
$ go run ./cmd/examples/cors/simple
2021/04/17 17:23:14 starting server on :9000
```

And then open a second terminal window and start our regular API application at the same time:

```
$ go run ./cmd/api
{"level":"INFO","time":"2021-04-17T15:23:34Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-17T15:23:34Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
```

You may also want to open the network activity tab in your developer tools and examine the HTTP headers associated with the blocked request.

![](img/30f9221bfc265d52b544dd595ca099de_642_0.png)

There are a couple of important things to point out here.

The first thing is that the headers demonstrate that the request was sent to our API, which processed the request and returned a successful 200 OK response to the web browser containing all our standard response headers. To re-iterate: the request itself was not prevented by the same-origin policy — it’s just that the browser won’t let JavaScript see the response.

The second thing is that the web browser automatically set an `Origin` header on the request to show where the request originates from (highlighted by the red arrow above). You’ll see that the header looks like this:

```
Origin: http://localhost:9000
```

We’ll use this header in the next chapter to help us selectively relax the same-origin policy, depending on whether we trust the origin that a request is coming from.

Finally, it’s important to emphasize that the same-origin policy is a *web browser thing only*.

Outside of a web browser, anyone can make a request to our API from anywhere, using `curl`, `wget` or any other means and read the response. That’s completely unaffected and unchanged by the same-origin policy.

```go
func (app *application) enableCORS(next http.Handler) http.Handler {
    return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        w.Header().Set("Access-Control-Allow-Origin", "*")

        next.ServeHTTP(w, r)
    })
}
```

And then update your `cmd/api/routes.go` file so that this middleware is used on all the application routes. Like so:

```
File: cmd/api/routes.go

```go
package main

...

func (app *application) routes() http.Handler {
    router := httprouter.New()

    router.NotFound = http.HandlerFunc(app.notFoundResponse)
    router.MethodNotAllowed = http.HandlerFunc(app.methodNotAllowedResponse)

    router.HandlerFunc(http.MethodGet, "/v1/healthcheck",
app.healthcheckHandler)

    router.HandlerFunc(http.MethodGet, "/v1/movies",
app.requirePermission("movies:read", app.listMoviesHandler))
    router.HandlerFunc(http.MethodPost, "/v1/movies",
app.requirePermission("movies:write", app.createMovieHandler))
    router.HandlerFunc(http.MethodGet, "/v1/movies/:id",
app.requirePermission("movies:read", app.showMovieHandler))
    router.HandlerFunc(http.MethodPatch, "/v1/movies/:id",
app.requirePermission("movies:write", app.updateMovieHandler))
}
```
```

```go
router.HandlerFunc(http.MethodDelete, "/v1/movies/:id",
app.requirePermission("movies:write", app.deleteMovieHandler))

router.HandlerFunc(http.MethodPost, "/v1/users", app.registerUserHandler)
router.HandlerFunc(http.MethodPut, "/v1/users/activated",
app.activateUserHandler)

router.HandlerFunc(http.MethodPost, "/v1/tokens/authentication",
app.createAuthenticationTokenHandler)

// Add the enableCORS() middleware.
return
app.recoverPanic(app.enableCORS(app.rateLimit(app.authenticate(router))))
}
```
```

It’s important to point out here that the `enableCORS()` middleware is deliberately positioned early in the middleware chain.

If we positioned it after our rate limiter, for example, any cross-origin requests that exceed the rate limit would *not have the* `Access-Control-Allow-Origin` *header set*. This means that they would be blocked by the client’s web browser due to the same-origin policy, rather than the client receiving a `429 Too Many Requests` response like they should.

OK, let’s try this out.

Restart the API application and then try visiting `http://localhost:9000` in your browser again. This time the cross-origin request should complete successfully, and you should see the JSON from our healthcheck handler presented on the webpage. Like so:

![](img/30f9221bfc265d52b544dd595ca099de_647_0.png)

I also recommend taking a quick look at the request and response headers relating to the JavaScript `fetch()` request again. You should see that the `Access-Control-Allow-Origin: *` header has been set on the response, similar to this:

![](img/30f9221bfc265d52b544dd595ca099de_648_0.png)

## Restricting Origins

Using a wildcard to allow cross-origin requests, like we are in the code above, can be useful in certain circumstances (like when you have a completely public API with no access control checks). But more often you’ll probably want to restrict CORS to a much smaller set of *trusted origins*.

To do this, you need to explicitly include the trusted origins in the `Access-Control-Allow-Origin` header instead of using a wildcard. For example, if you want to only allow CORS from the origin `https://www.example.com` you could send the following header in your responses:

```
Access-Control-Allow-Origin: https://www.example.com
```

If you only have one, fixed, origin that you want to allow requests from, then doing this is quite simple — you can just update your `enableCORS()` middleware to hard-code in the necessary origin value.

But if you need to support multiple trusted origins, or you want the value to be configurable at runtime, then things get a bit more complex.

One of the problems is that — in practice — you can only specify *exactly one origin* in the `Access-Control-Allow-Origin` header. You can’t include a list of multiple origin values, separated by spaces or commas like you might expect.

To work around this limitation, you’ll need to update your `enableCORS()` middleware to check if the value of the `Origin` header matches one of your trusted origins. If it does, then you can reflect (or *echo*) that value back in the `Access-Control-Allow-Origin` response header.

> **Note:** The web origin specification does permit multiple *space-separated* values in the `Access-Control-Allow-Origin` header but, unfortunately, no web browsers actually support this.
