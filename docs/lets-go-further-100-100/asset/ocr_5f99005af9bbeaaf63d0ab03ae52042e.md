```
package main

import (
    "errors"
    "net/http"

    "greenlight.alexedwards.net/internal/data"
    "greenlight.alexedwards.net/internal/validator"
)

func (app *application) registerUserHandler(w http.ResponseWriter, r *http.Request) {
    ...

    // Use the background helper to execute an anonymous function that sends
    the welcome
    // email.
    app.background(func() {
        err = app.mailer.Send(user.Email, "user_welcome.tmpl", user)
        if err != nil {
            app.logger.PrintError(err, nil)
        }
    })

    err = app.writeJSON(w, http.StatusAccepted, envelope{"user": user}, nil)
    if err != nil {
        app.serverErrorResponse(w, r, err)
    }
}
```

Let’s double-check that this is still working. Restart the API, then create another new user with the email address dave@example.com: