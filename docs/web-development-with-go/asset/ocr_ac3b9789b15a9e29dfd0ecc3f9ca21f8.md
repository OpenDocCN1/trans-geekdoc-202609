# CHAPTER 7. CREATING A SIGN UP PAGE

We will start by adding a field to the Users type that will store the new user view. You will also need to import the views package while doing this. The new code is shown in Listing 7.12.

```
$ atom controllers/users.go
```

Listing 7.12: Add the NewView field to Users
```go
import "lenslocked.com/views"

type Users struct {
    NewView *views.View
}
```

This doesn't do us much unless we need to write some code to create our view using the NewView function and the new user template.

Rather than doing this in main.go like we have been, we are instead going to provide a NewUsers function in our controllers that will handle up all the views our users controller will need. This will make it easier to reuse our controllers in the future.

Listing 7.13 shows the updated code for. In the new code we first import the views package, then we begin to write the NewUsers function that will be to construct and return a Users object.

Inside the NewUsers we call the NewView function provided by the views package and pass in the layout and template that we want to use, and then the newly created view is assigned to the NewView field of the users controller we are constructing. Finally, the users controller is returned.

Listing 7.13: Add the NewView to Users
```go
package controllers
```