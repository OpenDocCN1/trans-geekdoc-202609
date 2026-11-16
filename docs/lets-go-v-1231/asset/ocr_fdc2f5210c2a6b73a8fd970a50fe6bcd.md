```
File: cmd/web/helpers.go

package main

...

func (app *application) isAuthenticated(r *http.Request) bool {
	isAuthenticated, ok := r.Context().Value(isAuthenticatedContextKey).(bool)
	if !ok {
		return false
	}

	return isAuthenticated
}
```

It's important to point out here that if there isn't a value in the request context with the isAuthenticatedContextKey key, or the underlying value isn't a bool, then this type assertion will fail. In that case we take a 'safe' fall back and return false (i.e we assume that the user isn't authenticated).

If you like, try running the application again. It should compile correctly and if you log in as a certain user and browse around the application should work exactly as before.

Then, if you want, open MySQL and delete the record for the user that you're logged in as from the database. For example:

```
mysql> USE snippetbox;
mysql> DELETE FROM users WHERE email = 'bob@example.com';
```

And when you go back to your browser and refresh the page, the application is now smart enough to recognize that the user has been deleted, and you'll find yourself treated as an unauthenticated (logged-out) user.

# Additional information

# Misusing request context

It's important to emphasize that request context should only be used to store information relevant to the lifetime of a specific request. The Go documentation for context.Context warns:

> Use context Values only for request-scoped data that transits processes and APIs.