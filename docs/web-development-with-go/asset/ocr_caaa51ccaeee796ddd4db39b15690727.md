# CHAPTER 7. CREATING A SIGN UP PAGE

We need to import the controllers package that we created so that we can construct a users controller. Once we have the package imported, we will go ahead and create a users controller and assign it to a variable inside of our main function. This code is shown in Listing 7.15, but again your code won't compile just yet.

```
Listing 7.15: Instantiating a users controller
```go
import (
  "net/http"
  "lenslocked.com/controllers"
  "lenslocked.com/views"

  "github.com/gorilla/mux"
)

// this is all the same

func main() {
  homeView = views.NewView("bootstrap","views/home.gohtml")
  contactView = views.NewView("bootstrap","views/contact.gohtml")
  usersC := controllers.NewUsers()
  // this is all the same
}
```
```

Finally, we are ready to use the New method on the users controller as our handler function passed into our router. Find the line that reads:

```
r.HandleFunc("/signup", signup)
```

It should be located inside of the main function. We are going to update the last part of this, the signup argument, and we are instead to pass in usersC.New which is the new user handler we created. The new code is shown in Listing 7.16.