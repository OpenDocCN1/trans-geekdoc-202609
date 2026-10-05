# 7.5. CLEANING UP AND CREATING A STATIC CONTROLLER

need to store two different views - the home view, and the contact view. Then, just like we did with the users, we are going to create a NewStatic controller, including initializing our views.

**Listing 7.27:** Starting to create a static controller
```go
package controllers

import "lenslocked.com/views"

func NewStatic() *Static {
	return &Static{
		HomeView: views.NewView(
			"bootstrap", "views/static/home.shtml"),
			ContactView: views.NewView(
			"bootstrap", "views/static/contact.shtml"),
		}
}

type Static struct {
	HomeView *views.View
	ContactView *views.View
}\```

Next, we need to move our views to the correct location. We will following the same pattern as before, so both home.shtml and contact.shtml (both in the views directory) will be moved into a static directory where all of our template files for the static controller will live. To do this we need to create the views/static directory, then move our .shtml files into the new directory.

**Listing 7.28:** Moving the static controller templates
```bash
$ mkdir views/static
$ mv views/home.shtml views/static
$ mv views/contact.shtml views/static
```

Next we need to write our handler functions inside of our controller, but if we look at both the home and contact functions in main.go you will notice that neither of these are really doing much.