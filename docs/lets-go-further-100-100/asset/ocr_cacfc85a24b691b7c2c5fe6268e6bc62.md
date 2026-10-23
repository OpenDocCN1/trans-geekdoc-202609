```
// Note that the first parameter for the middleware function is the
permission code that
// we require the user to have.
func (app *application) requirePermission(code string, next http.HandlerFunc) http.HandlerFunc {
    fn := func(w http.ResponseWriter, r *http.Request) {
        // Retrieve the user from the request context.
        user := app.contextGetUser(r)

        // Get the slice of permissions for the user.
        permissions, err := app.models.Permissions.GetAllForUser(user.ID)
        if err != nil {
            app.serverErrorResponse(w, r, err)
            return
        }

        // Check if the slice includes the required permission. If it
doesn't, then
        // return a 403 Forbidden response.
        if !permissions.Include(code) {
            app.notPermittedResponse(w, r)
            return
        }

        // Otherwise they have the required permission so we call the next
handler in
        // the chain.
        next.ServeHTTP(w, r)
    }

    // Wrap this with the requireActivatedUser() middleware before returning
it.
    return app.requireActivatedUser(fn)
}
```