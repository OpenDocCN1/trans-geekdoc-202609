+   - We use the `app.logger.PrintError()` helper to manage any errors in our background goroutine. This is because by the time we encounter the errors, the client will probably have already been sent a `202 Accepted` response by our `writeJSON()` helper.
+   
+   Note that we don’t want to use the `app.serverErrorResponse()` helper to handle any errors in our background goroutine, as that would result in us trying to write a second *HTTP response* and getting a `"http: superfluous response.WriteHeader call"` error from our `http.Server` at runtime.

+   - The code running in the background goroutine forms a *closure* over the `user` and `app` variables. It’s important to be aware that these ‘closed over’ variables are *not scoped to the background goroutine*, which means that any changes you make to them will be reflected in the rest of your codebase. For a simple example of this, see the following [playground code](#).
+   
+   In our case we aren’t changing the value of these variables in any way, so this behavior won’t cause us any issues. But it is important to keep in mind.

OK, let’s try this out!

Restart the API, then go ahead and register another new user with the email address `carol@example.com`. Like so:

```
$ BODY='{"name": "Carol Smith", "email": "carol@example.com", "password": "pa55word"}'
$ curl -w '\nTime: %{time_total}\n' -d "$BODY" localhost:4000/v1/users
```