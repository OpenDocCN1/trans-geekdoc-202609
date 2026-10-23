```
```go
})

// Send a 202 Accepted response and confirmation message to the client.
env := envelope{"message": "an email will be sent to you containing password reset instructions"}

err = app.writeJSON(w, http.StatusAccepted, env, nil)
if err != nil {
    app.serverErrorResponse(w, r, err)
}
}
```
```

```
```go
File: cmd/api/users.go

package main

...

// Verify the password reset token and set a new password for the user.
func (app *application) updateUserPasswordHandler(w http.ResponseWriter, r *http.Request) {
    // Parse and validate the user's new password and password reset token.
    var input struct {
        Password     string `json:"password"`
        TokenPlaintext string `json:"token"`
    }

    err := app.readJSON(w, r, &input)
    if err != nil {
        app.badRequestResponse(w, r, err)
        return
    }

    v := validator.New()
```
```