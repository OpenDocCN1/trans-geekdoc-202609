```
import (
    "errors"
    "net/http"

    "greenlight.alexedwards.net/internal/data"
    "greenlight.alexedwards.net/internal/validator"
)

func (app *application) registerUserHandler(w http.ResponseWriter, r *http.Request) {
    // Create an anonymous struct to hold the expected data from the request body.
    var input struct {
        Name     string `json:"name"`
        Email    string `json:"email"`
        Password string `json:"password"`
    }

    // Parse the request body into the anonymous struct.
    err := app.readJSON(w, r, &input)
    if err != nil {
        app.badRequestResponse(w, r, err)
        return
    }

    // Copy the data from the request body into a new User struct. Notice also that we
    // set the Activated field to false, which isn't strictly necessary because the
    // Activated field will have the zero-value of false by default. But setting this
    // explicitly helps to make our intentions clear to anyone reading the code.
    user := &data.User{
        Name:       input.Name,
        Email:      input.Email,
        Activated: false,
    }
}
```