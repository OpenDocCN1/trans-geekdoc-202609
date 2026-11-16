# Using request context

At the moment our logic for authenticating a user consists of simply checking whether a "authenticatedUserID" value exists in their session data, like so:

```
func (app *application) isAuthenticated(r *http.Request) bool {
	return app.sessionManager.Exists(r.Context(), "authenticatedUserID")
}
```

We could make this check more robust by querying our users database table to make sure that the "authenticatedUserID" value is a real, valid, value (i.e we haven't deleted the user's account since they last logged in).

But there is a slight problem with doing this additional database check.

Our isAuthenticated() helper can potentially be called multiple times in each request cycle. Currently we use it twice — once in the requireAuthentication() middleware and again in the newTemplateData() helper. So, if we query the database from the isAuthenticated() helper directly, we would end up making duplicated round-trips to the database during every request. And that's not very efficient.

A better approach would be to carry out this check in some middleware to determine whether the current request is from an authenticated user or not, and then pass that information down to all subsequent handlers in the chain.

So how do we do this? Enter request context.

In this section you'll learn:

+   - What request context is, how to use it, and when it is appropriate to use it.
+   - How to use request context in practice to pass information about the current user between your handlers.