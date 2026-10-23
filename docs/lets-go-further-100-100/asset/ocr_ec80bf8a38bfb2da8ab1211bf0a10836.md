```
data.ValidatePasswordPlaintext(v, input.Password)
data.ValidateTokenPlaintext(v, input.TokenPlaintext)

if !v.Valid() {
    app.failedValidationResponse(w, r, v.Errors)
    return
}

// Retrieve the details of the user associated with the password reset token,
// returning an error message if no matching record was found.
user, err := app.models.Users.GetForToken(data.ScopePasswordReset,
input.TokenPlaintext)
if err != nil {
    switch {
    case errors.Is(err, data.ErrRecordNotFound):
        v.AddError("token", "invalid or expired password reset token")
        app.failedValidationResponse(w, r, v.Errors)
    default:
        app.serverErrorResponse(w, r, err)
    }
    return
}

// Set the new password for the user.
err = user.Password.Set(input.Password)
if err != nil {
    app.serverErrorResponse(w, r, err)
    return
}

// Save the updated user record in our database, checking for any edit conflicts as
// normal.
err = app.models.Users.Update(user)
if err != nil {
    switch {
    case errors.Is(err, data.ErrEditConflict):
        app.editConflictResponse(w, r)
```