
feature altogether.

OK, let's get back to our Go code and begin by creating a new `middleware.go` file. We'll use this to hold all the custom middleware that we write throughout this book.

```
$ touch cmd/web/middleware.go
```

Then open it up and add a `commonHeaders()` function using the pattern that we introduced in the previous chapter:

File: cmd/web/middleware.go

```
package main

import (
	"net/http"
)

func commonHeaders(next http.Handler) http.Handler {
	return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
		// Note: This is split across multiple lines for readability. You don't
		// need to do this in your own code.
		w.Header().Set("Content-Security-Policy",
			"default-src 'self'; style-src 'self' fonts.googleapis.com; font-src fonts.gstatic.com")
		w.Header().Set("Referrer-Policy", "origin-when-cross-origin")
		w.Header().Set("X-Content-Type-Options", "nosniff")
		w.Header().Set("X-Frame-Options", "deny")
		w.Header().Set("X-XSS-Protection", "0")

		w.Header().Set("Server", "Go")

		next.ServeHTTP(w, r)
	})
}
```

Because we want this middleware to act on every request that is received, we need it to be executed *before* a request hits our servemux. We want the flow of control through our application to look like:

```
commonHeaders → servemux → application handler
```

To do this we'll need the `commonHeaders` middleware function to *wrap our servemux*. Let's update the `routes.go` file to do exactly that:

File: cmd/web/routes.go

```
package main

import "net/http"

// Update the signature for the routes() method so that it returns a
// http.Handler instead of *http.ServeMux.
func (app *application) routes() http.Handler {
    mux := http.NewServeMux()

    fileServer := http.FileServer(http.Dir("./ui/static/"))
    mux.Handle("GET /static/", http.StripPrefix("/static", fileServer))

    mux.HandleFunc("GET /{$}", app.home)
    mux.HandleFunc("GET /snippet/view/{id}", app.snippetView)
    mux.HandleFunc("GET /snippet/create", app.snippetCreate)
    mux.HandleFunc("POST /snippet/create", app.snippetCreatePost)

    // Pass the servemux as the 'next' parameter to the commonHeaders middleware.
    // Because commonHeaders is just a function, and the function returns a
    // http.Handler we don't need to do anything else.
    return commonHeaders(mux)
}
```

**Important:** Make sure that you update the signature of the routes() method so that it returns a http.Handler here, otherwise you'll get a compile-time error.

We also need to quickly update our home handler code to remove the `w.Header().Add("Server", "Go")` line, otherwise we'll end up adding that header twice on responses from the homepage.

File: cmd/web/handlers.go

```
package main

...

func (app *application) home(w http.ResponseWriter, r *http.Request) {
    snippets, err := app.snippets.Latest()
    if err != nil {
        app.serverError(w, r, err)
        return
    }

    data := app.newTemplateData(r)
    data.Snippets = snippets

    app.render(w, r, http.StatusOK, "home.html", data)
}

...
```

Go ahead and give this a try. Run the application then open a terminal window and try making some requests with curl. You should see that the security headers are now included in every response.

```
$ curl --head http://localhost:4000/
HTTP/1.1 200 OK
Content-Security-Policy: default-src 'self'; style-src 'self' fonts.googleapis.com; font-src fonts.gstatic.com
Referrer-Policy: origin-when-cross-origin
Server: Go
X-Content-Type-Options: nosniff
X-Frame-Options: deny
X-XSS-Protection: 0
Date: Wed, 18 Mar 2024 11:29:23 GMT
Content-Length: 1700
Content-Type: text/html; charset=utf-8
```

## Additional information

## Flow of control

It's important to know that when the last handler in the chain returns, control is passed back up the chain in the reverse direction. So when our code is being executed the flow of control actually looks like this:

commonHeaders → servemux → application handler → servemux → commonHeaders

In any middleware handler, code which comes before `next.ServeHTTP()` will be executed on the way down the chain, and any code after `next.ServeHTTP()` — or in a deferred function — will be executed on the way back up.

```
func myMiddleware(next http.Handler) http.Handler {
	return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
		// Any code here will execute on the way down the chain.
		next.ServeHTTP(w, r)
		// Any code here will execute on the way back up the chain.
	})
}
```

## Early returns

Another thing to mention is that if you call return in your middleware function before you call `next.ServeHTTP()`, then the chain will stop being executed and control will flow back upstream.

As an example, a common use-case for early returns is authentication middleware which only allows execution of the chain to continue if a particular check is passed. For instance:

```
func myMiddleware(next http.Handler) http.Handler {
	return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
		// If the user isn't authorized, send a 403 Forbidden status and
		// return to stop executing the chain.
		if !isAuthorized(r) {
			w.WriteHeader(http.StatusForbidden)
			return
		}

		// Otherwise, call the next handler in the chain.
		next.ServeHTTP(w, r)
	})
}
```

We’ll use this ‘early return’ pattern later in the book to restrict access to certain parts of our application.

## Debugging CSP issues

While CSP headers are great and you should definitely use them, it’s worth saying that I’ve spent many hours trying to debug problems, only to eventually realize that a critical resource or script is being blocked by my own CSP rules.

If you’re working on a project which is using CSP headers, like this one, I recommend keeping your web browser developer tools handy and getting into the habit of checking the logs early on if you run into any unexpected problems. In Firefox, any blocked resources will be shown as an error in the console logs — similar to this:

Content Security Policy: The page's settings blocked the loading of a resource at https://fonts.googleapis.com/css?family=Ubuntu+Mono:400,700 ("style-src").

>>

## Request logging

Let's continue in the same vein and add some middleware to log HTTP requests. Specifically, we're going to use the structured logger that we created earlier to record the IP address of the user, and the method, URI and HTTP version for the request.

Open your middleware.go file and create a logRequest() method using the standard middleware pattern, like so:

File: cmd/web/middleware.go

```
package main

...

func (app *application) logRequest(next http.Handler) http.Handler {
	return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
		var (
			ip     = r.RemoteAddr
			proto  = r.Proto
			method = r.Method
			uri    = r.URL.RequestURI()
		)

		app.logger.Info("received request", "ip", ip, "proto", proto, "method", method, "uri", uri)

		next.ServeHTTP(w, r)
	})
}
```

Notice that this time we're implementing the middleware as a method on application?

This is perfectly valid to do. Our middleware method has the same signature as before, but because it is a method against application it also has access to the handler dependencies including the structured logger.

Now let's update our routes.go file so that the logRequest middleware is executed first, and for all requests, so that the flow of control (reading from left to right) looks like this:

```
logRequest ↔ commonHeaders ↔ servemux ↔ application handler
```

File: cmd/web/routes.go

```
package main

import "net/http"

func (app *application) routes() http.Handler {
    mux := http.NewServeMux()

    fileServer := http.FileServer(http.Dir("./ui/static/"))
    mux.Handle("GET /static/", http.StripPrefix("/static", fileServer))

    mux.HandleFunc("GET /{$}", app.home)
    mux.HandleFunc("GET /snippet/view/{id}", app.snippetView)
    mux.HandleFunc("GET /snippet/create", app.snippetCreate)
    mux.HandleFunc("POST /snippet/create", app.snippetCreatePost)

    // Wrap the existing chain with the logRequest middleware.
    return app.logRequest(commonHeaders(mux))
}
```

Alright... let's give it a try!

Restart your application, browse around, and then check your terminal window. You should see log output which looks a bit like this:

```
$ go run ./cmd/web
time=2024-03-18T11:29:23.0000+00:00 level=INFO msg="starting server" addr=:4000
time=2024-03-18T11:29:23.0000+00:00 level=INFO msg="received request" ip=127.0.0.1:56536 proto=HTTP/1.1 method=GET uri=/
time=2024-03-18T11:29:23.0000+00:00 level=INFO msg="received request" ip=127.0.0.1:56536 proto=HTTP/1.1 method=GET uri=/static
time=2024-03-18T11:29:23.0000+00:00 level=INFO msg="received request" ip=127.0.0.1:56546 proto=HTTP/1.1 method=GET uri=/static
time=2024-03-18T11:29:23.0000+00:00 level=INFO msg="received request" ip=127.0.0.1:56536 proto=HTTP/1.1 method=GET uri=/static
time=2024-03-18T11:29:23.0000+00:00 level=INFO msg="received request" ip=127.0.0.1:56536 proto=HTTP/1.1 method=GET uri=/static
time=2024-03-18T11:29:23.0000+00:00 level=INFO msg="received request" ip=127.0.0.1:56536 proto=HTTP/1.1 method=GET uri="/snipp
```

> **Note:** Depending on how your browser caches static files, you might need to do a hard refresh (or open a new incognito/private browsing tab) to see any requests for static files.
