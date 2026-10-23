```
}()

// Send the welcome email.
err = app.mailer.Send(user.Email, "user_welcome.tmpl", user)
if err != nil {
    app.logger.PrintError(err, nil)
}
}()

err = app.writeJSON(w, http.StatusAccepted, envelope{"user": user}, nil)
if err != nil {
    app.serverErrorResponse(w, r, err)
}
}
```

# Using a helper function

If you need to execute a lot of background tasks in your application, it can get tedious to keep repeating the same panic recovery code — and there’s a risk that you might forget to include it altogether.

To help take care of this, it’s possible to create a simple helper function which wraps the panic recovery logic. If you’re following along, open your cmd/api/helpers.go file and create a new background() helper method as follows:

```
File: cmd/api/helpers.go

package main

...
```