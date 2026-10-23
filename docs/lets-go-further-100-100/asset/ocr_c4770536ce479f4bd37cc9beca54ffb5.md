```
app.requirePermission("movies:write", app.deleteMovieHandler))

    router.HandlerFunc(http.MethodPost, "/v1/users", app.registerUserHandler)
    router.HandlerFunc(http.MethodPut, "/v1/users/activated",
app.activateUserHandler)

    router.HandlerFunc(http.MethodPost, "/v1/tokens/authentication",
app.createAuthenticationTokenHandler)

    return app.recoverPanic(app.rateLimit(app.authenticate(router)))
}
```

# Demonstration

Showing this in action is a bit awkward because, if you’ve been following along, none of the users in our database currently have any permissions set for them.

To help demonstrate this new functionality, let’s open `psql` and add some permissions. Specifically, we will:

+   - Activate the user `alice@example.com`.
+   - Give *all* users the "movies:read" permission.
+   - Give the user `faith@example.com` the "movies:write" permission.

If you’re following along, open your `psql` prompt:

```
$ psql $GREENLIGHT_DB_DSN
Password for user greenlight:
psql (13.1 (Ubuntu 13.1-1.pgdg20.04+1))
```