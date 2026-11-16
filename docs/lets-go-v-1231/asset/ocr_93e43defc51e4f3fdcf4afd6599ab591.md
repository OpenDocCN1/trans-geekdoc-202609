The important thing to emphasize here is the following difference:

+   - When we *don't* have a valid authenticated user, we pass the original and unchanged *http.Request* to the next handler in the chain.
+   - When we *do* have a valid authenticated user, we create a copy of the request with a *isAuthenticatedContextKey* key and *true* value stored in the request context. We then pass this copy of *http.Request* to the next handler in the chain.

Alright, let's update the *cmd/web/routes.go* file to include the *authenticate()* middleware in our *dynamic* middleware chain:

```
File: cmd/web/routes.go

```go
package main

...

func (app *application) routes() http.Handler {
    mux := http.NewServeMux()

    fileServer := http.FileServer(http.Dir("./ui/static/"))
    mux.Handle("GET /static/", http.StripPrefix("/static", fileServer))

    // Add the authenticate() middleware to the chain.
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
```

The last thing that we need to do is update our *isAuthenticated()* helper, so that instead of checking the session data it now checks the request context to determine if a user is authenticated or not.

We can do this like so: