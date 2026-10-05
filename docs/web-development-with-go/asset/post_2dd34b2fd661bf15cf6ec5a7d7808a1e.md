
## 7.4. PROCESSING THE SIGN UP FORM

```
$ atom controllers/users.go
```

We still want to create the SignupForm variable, but after that we call parseForm, check for an error, and print out our form data. Much easier!

The final code should match Listing 7.26.

```
Listing 7.26: using parseForm() inside Create()
func (u *Users) Create(w http.ResponseWriter, r *http.Request) {
	var form SignupForm
	if err := parseForm(r, &form); err != nil {
		panic(err)
	}
	fmt.Fprintln(w, "Email is", form.Email)
	fmt.Fprintln(w, "Password is", form.Password)
}
```

We still have to handle an error in this code, but we were able to reduce it to only one error check inside of our Create() action, which simplifies things a bit. On top of that, we now have a way to parse any form without rewriting that code.

The last bit of code also update our print statements to demonstrate that we definitely can access each field on the SignupForm instance and that it has the correct value assigned to it.

All that is left to do in this chapter is to clean up our code and try out a few exercises.

## Source code

The links below have the completed source code and a diff of all of the code changed in this section.

- Completed - book.usegolang.com/7.4.5
- Changes - book.usegolang.com/7.4.5-diff

## 7.5 Cleaning up and creating a static controller

Thus far we have been working with the users controller, but in this section we are going to look at how you can use a controller for pages that don't really map to a resource like a user, but instead closer to static pages in your web application.

A great example of this is your contact page. You might be able to put this under something like an inquiries controller because it is how users find out how to make inquiries, but this controller would end up with one action - the page that shows all of your contact information.

Instead of creating a bunch of unnecessary controllers that could get confusing, we are going to create one controller to hold all of our pages that are not quite static pages, but are pretty close to being a static page. We are going to call this the static controller, and inside of it we will have actions for the home page and the contact page.

### 7.5.1 Creating the static controller

Just like before when we created the users controller, our static controller will live inside the controllers package. Create and open a new source code file inside of the controllers directory for your static controller.

```
$ atom controllers/static.go
```

The first thing we need to do is declare the Static type. Inside of this we need to store two different views - the home view, and the contact view. Then, just like we did with the users, we are going to create a NewStatic controller, including initializing our views.

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
}
```

Next, we need to move our views to the correct location. We will following the same pattern as before, so both home.shtml and contact.shtml (both in the views directory) will be moved into a static directory where all of our template files for the static controller will live. To do this we need to create the views/static directory, then move our .shtml files into the new directory.

**Listing 7.28:** Moving the static controller templates
```bash
$ mkdir views/static
$ mv views/home.shtml views/static
$ mv views/contact.shtml views/static
```

Next we need to write our handler functions inside of our controller, but if we look at both the home and contact functions in main.go you will notice that neither of these are really doing much.

In fact, the only thing they actually do is set a content type and render a view. We don't really need a custom function to make that. It would be nice if we could just use our View type from the views package as a handler function that simply renders the view.

To do this, we need to figure out what interface our views.View type needs to implement so that we can simply pass our views.View type to our router. That means heading back over to the gorilla/mux docs again.

Skimming over this list, we are looking for a method with the mux.Router type (because that is what our router is) that will let us pass in an interface implementation.

Well, the only two methods that look plausible are Handle and HandleFunc, but we know that HandleFunc isn't what we want because we have been using it, let's check out the Handle method.

The Handle() method appears to take a path, and then an http.Handler object. That means we need to head over to the net/http docs and look for the http.Handler type.

The http.Handler is an interface that just needs one method:

```
ServeHTTP(ResponseWriter, *Request)
```

That sounds like what we want with our views.View type - a function that receives an http response writer and a request - so it appears we just need to write a ServeHTTP() method for our views.View type.

Open up our views source file.

```
$ atom views/views.go
```

In the views source code we are going to write a ServeHTTP method that resembles the home and contact functions we have in main.go. While we are at it, we should go ahead and move the code that sets the content-type into the Render method.

**Listing 7.29:** Implementing the http.Handler interface

```
func (v *View) Render(w http.ResponseWriter, data interface{}) error {
	w.Header().Set("Content-Type", "text/html")
	return v.Template.ExecuteTemplate(w, v.Layout, data)
}

func (v *View) ServeHTTP(w http.ResponseWriter, r *http.Request) {
	if err := v.Render(w, nil); err != nil {
		panic(err)
	}
}
```

That views.View implements the Handler interface, we can update main.go to just use the views as handlers.

**Listing 7.30:** main.go
```
package main

import (
	"net/http"

	"lenslocked.com/controllers"

	"github.com/gorilla/mux"
)

func main() {
	r := mux.NewRouter()
	staticC := controllers.NewStatic()
	usersC := controllers.NewUsers()

	r.Handle("/", staticC.Home).Methods("GET")
	r.Handle("/contact", staticC.Contact).Methods("GET")
	r.HandleFunc("/signup", userC.Create).Methods("POST")

	http.ListenAndServe(":3000", r)
}
```

Lastly, since we don't plan on creating Home or Contact method on the static controller, we can rename fields from HomeView and ContactView to just Home and Contact. After doing this you will also need to update main.go.

**Listing 7.31:** Renaming fields in controllers/static.go
```go
package controllers

import "lenslocked.com/views"

func NewStatic() *Static {
	return &Static{
		Home: views.NewView(
			"bootstrap", "views/static/home.shtml"),
		Contact: views.NewView(
			"bootstrap", "views/static/contact.shtml"),
	}
}

type Static struct {
	Home *views.View
	Contact *views.View
}
```

**Listing 7.32:** Renaming fields in main.go
```go
r.Handle("/", staticC.Home).Methods("GET")
r.Handle("/contact", staticC.Contact).Methods("GET")
```

Restart your application and verify that it is working. You should still be able to view the home and contact pages, but now they should be served via the ServeHTTP handler method on the views.View type inside our static controller.

### 7.5.2 Simplifying the creation of new views

Open up both of your controllers (users.go and static.go) and look at the code that calls the NewView function provided by the views package. Do you notice anything in common between these two pieces of code?

If you look at the view paths we are passing into these function calls you will notice that they have a lot in common. They start with the prefix (views/), and they both end with the same file extension (.gohtml). Given that we don't plan to store view files outside of the views directory, and we don't intend to use another template extension (using multiple would be pretty confusing), it would be nice if we could simplify that code a bit to not require this information. We might instead call:

```
views.NewView("bootstrap", "users/new")
```

To make this happen, we are going to need to update our views source code.
