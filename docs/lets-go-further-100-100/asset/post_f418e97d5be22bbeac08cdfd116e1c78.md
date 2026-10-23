
trusted origin:

```
$ go run ./cmd/api -cors-trusted-origins="http://localhost:9000"
{"level":"INFO","time":"2021-04-17T16:48:55Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-17T16:48:55Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
```

Once both are running, open your web browser and navigate to http://localhost:9000. If you look at the console log in your developer tools, you should see a message similar to this:

> Cross-Origin Request Blocked: The Same Origin Policy disallows reading the remote resource at http://localhost:4000/v1/tokens/authentication. (Reason: header ‘content-type’ is not allowed according to header ‘Access-Control-Allow-Headers’ from CORS preflight response).

![](img/30f9221bfc265d52b544dd595ca099de_667_0.png)

The interesting thing here is the preflight request headers. They might look slightly different for you depending on the browser you're using, but broadly they should look something like this:

```
Accept: */*
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.5
Access-Control-Request-Headers: content-type
Access-Control-Request-Method: POST
Cache-Control: no-cache
Connection: keep-alive
Host: localhost:4000
Origin: http://localhost:9000
Pragma: no-cache
Referer: http://localhost:9000/
```

header, and an `Access-Control-Request-Method` header. If any one of these pieces is missing, we know that it is not a preflight request.

Once we identify that it is a preflight request, we need to send a `200 OK` response with some special headers to let the browser know whether or not it's OK for the real request to proceed. These are:

- An `Access-Control-Allow-Origin` response header, which reflects the value of the preflight request's `Origin` header (just like in the previous chapter).
- An `Access-Control-Allow-Methods` header listing the HTTP methods that can be used in real cross-origin requests to the URL.
- An `Access-Control-Allow-Headers` header listing the request headers that can be included in real cross-origin requests to the URL.

In our case, we could set the following response headers to allow cross-origin requests for *all our endpoints*:

```
Access-Control-Allow-Origin: <reflected trusted origin>
Access-Control-Allow-Methods: OPTIONS, PUT, PATCH, DELETE
Access-Control-Allow-Headers: Authorization, Content-Type
```

**Important:** When responding to a preflight request it's not necessary to include the CORS-safe methods `HEAD`, `GET` or `POST` in the `Access-Control-Allow-Methods` header. Likewise,

> > it’s not necessary to include forbidden or CORS-safe headers in `Access-Control-Allow-Headers`.

When the web browser receives these headers, it compares the values to the method and (case-insensitive) headers that it wants to use in the real request. If the method or any of the headers are not allowed, then the browser will block the real request.

## Updating our middleware

Let’s put this into action and update our `enableCORS()` middleware so it intercepts and responds to any preflight requests. Specifically, we want to:

- 1. Set a `Vary: Access-Control-Request-Method` header on all responses, as the response will be different depending on whether or not this header exists in the request.
- 2. Check whether the request is a preflight cross-origin request or not. If it’s not, then we should allow the request to proceed as normal.
- 3. Otherwise, if it is a preflight cross-origin request, then we should add the `Access-Control-Allow-Method` and `Access-Control-Allow-Headers` headers as described above.

Go ahead and update the `cmd/api/middleware.go` file like so:

```
File: `cmd/api/middleware.go`
```

```
package main

...

func (app *application) enableCORS(next http.Handler) http.Handler {
    return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        w.Header().Add("Vary", "Origin")

        // Add the "Vary: Access-Control-Request-Method" header.
        w.Header().Add("Vary", "Access-Control-Request-Method")

        origin := r.Header.Get("Origin")

        if origin != "" && len(app.config.cors.trustedOrigins) != 0 {
            for i := range app.config.cors.trustedOrigins {
                if origin == app.config.cors.trustedOrigins[i] {
                    w.Header().Set("Access-Control-Allow-Origin", origin)

                    // Check if the request has the HTTP method OPTIONS and
                    // contains the
                    // "Access-Control-Request-Method" header. If it does,
                    // then we treat
                    // it as a preflight request.
                    if r.Method == http.MethodOptions &&
                        r.Header.Get("Access-Control-Request-Method") != "" {
                        // Set the necessary preflight response headers, as
                        // discussed
                        // previously.
                        w.Header().Set("Access-Control-Allow-Methods",
                            "OPTIONS, PUT, PATCH, DELETE")
                        w.Header().Set("Access-Control-Allow-Headers",
                            "Authorization, Content-Type")

                        // Write the headers along with a 200 OK status and
                        // return from
                        // the middleware with no further action.
                        w.WriteHeader(http.StatusOK)
                        return
                    }
                }
            }
        }
    }
}
```

```
pool established"}
{"level":"INFO","time":"2021-04-17T17:23:05Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
```

Then open [http://localhost:9000](http://localhost:9000) in your browser again. This time you should see that the cross-origin `fetch()` to POST `/v1/tokens/authentication` succeeds, and you now get an authentication token in the response. Similar to this:

![](img/30f9221bfc265d52b544dd595ca099de_673_0.png)

**Note:** If you look at the details for the preflight request, you should see that our new CORS headers have been set on the preflight response, shown by the red arrow in the screenshot above.

preflight cache, so if you send back the wrong headers the user will be stuck with them until the cache expires.

If you want to disable caching altogether, you can set the value to `-1`:

```
Access-Control-Max-Age: -1
```

It’s also important to be aware that browsers may impose a hard maximum on how long the headers can be cached for. The MDN documentation says:

- *Firefox caps this at 24 hours (86400 seconds).*
- *Chromium (prior to v76) caps at 10 minutes (600 seconds).*
- *Chromium (starting in v76) caps at 2 hours (7200 seconds).*

## Preflight wildcards

If you have a complex or rapidly changing API then it might be awkward to maintain a hard-coded safelist of methods and headers for the preflight response. You might think: *I just want to allow all HTTP methods and headers for cross-origin requests.*

In this case, both the `Access-Control-Allow-Methods` and `Access-Control-Allow-Headers` headers allow you to use a wildcard
* character like so:

```
Access-Control-Allow-Methods: *
Access-Control-Allow-Headers: *
```

But using these comes with some important caveats:

- Wildcards in these headers are currently only supported by 74% of browsers. Any browsers which don’t support them will block the preflight request.
- The `Authorization` header cannot be wildcarded. Instead, you will need to include this explicitly in the header like `Access-Control-Allow-Headers: Authorization, *`.
- Wildcards are not supported for credentialed requests (those with cookies or HTTP basic authentication). For these, the character `*` will be treated as the literal string `"*"`, rather than as a wildcard.
