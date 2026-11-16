```
// Decode the form data into the userLoginForm strct.
var form userLoginForm

err := app.decodePostForm(r, &form)
if err != nil {
    app.clientError(w, http.StatusBadRequest)
    return
}

// Do some validation checks on the form. We check that both email and
// password are provided, and also check the format of the email address as
// a UX-nicety (in case the user makes a typo).
form.CheckField(validator.NotBlank(form.Email), "email", "This field cannot be blank")
form.CheckField(validator.Matches(form.Email, validator.EmailRX), "email", "This field must be a valid email address")
form.CheckField(validator.NotBlank(form.Password), "password", "This field cannot be blank")

if !form.Valid() {
    data := app.newTemplateData(r)
    data.Form = form
    app.render(w, r, http.StatusUnprocessableEntity, "login.tmpl", data)
    return
}

// Check whether the credentials are valid. If they're not, add a generic
// non-field error message and re-display the login page.
id, err := app.users.Authenticate(form.Email, form.Password)
if err != nil {
    if errors.Is(err, models.ErrInvalidCredentials) {
        form.AddNonFieldError("Email or password is incorrect")

        data := app.newTemplateData(r)
        data.Form = form
        app.render(w, r, http.StatusUnprocessableEntity, "login.tmpl", data)
    } else {
        app.serverError(w, r, err)
    }
    return
}

// Use the RenewToken() method on the current session to change the session
// ID. It's good practice to generate a new session ID when the
// authentication state or privilege levels changes for the user (e.g. login
// and logout operations).
err = app.sessionManager.RenewToken(r.Context())
if err != nil {
    app.serverError(w, r, err)
    return
}

// Add the ID of the current user to the session, so that they are now
// 'logged in'.
app.sessionManager.Put(r.Context(), "authenticatedUserID", id)

// Redirect the user to the create snippet page.
http.Redirect(w, r, "/snippet/create", http.StatusSeeOther)
}
...
```