# 7.3. CREATING OUR FIRST CONTROLLER

```
import "lenslocked.com/views"

func NewUsers() *Users {
    return &Users{
        NewView: views.New("bootstrap", "views/users/new.gohtml"),
    }
}

type Users struct {
    NewView *views.View
}
```

Finally, we are going create our handler (aka action) that will handle web requests when a user visits the sign up page. Our method will be made New because it is used to create a new user. This is why we named the template new.gohtml.

This is going to be very similar to the signup function we created earlier, it is going to be a method associated with the Users type. This is important, because it means our New method will also have access to the NewView that we created.

The code for our New action is shown in Listing 7.14.

# Listing 7.14: The new user action

```
import (
    "net/http"

    "lenslocked.com/views"
)
// ... this is all the same

// New is used to render the form where a user can
// create a new user account.
// GET /signup
func (u *Users) New(w http.ResponseWriter, r *http.Request) {
    if err := u.NewView.Render(w, nil); err != nil {
        panic(err)
    }
}
```