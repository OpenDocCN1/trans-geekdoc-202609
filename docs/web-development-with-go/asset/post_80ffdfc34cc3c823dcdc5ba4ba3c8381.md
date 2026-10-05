
## 6.3. CREATING A REUSABLE BOOTSTRAP LAYOUT

```
{{template "footer" .}}
```

The period (.) in the code above is saying “pass all of the data we have to the footer template”. You can also pass a specific piece of data, like a user’s name.

```
{{template "footer" .Name}}
```

## Source code

The links below have the completed source code and a diff of all the code changed in this section.

- Completed - book.usegolang.com/6.3.1
- Changes - book.usegolang.com/6.3.1-diff

## 6.3.2 Creating a view type

We are eventually going to take what we learned about named templates and apply it to create a layout for all of our pages, but first we are going to address another issue that you may have noticed.

In order to use our footer template, we had to include this file in every single template that we parsed. For one or two templates this is fine, but if we start doing this more frequently it could quickly become problematic.

Not only is this a lot of extra code, it is also really hard to maintain. Every time we add a new layout file we need to change code for each template that we use

## CHAPTER 6. CREATING OUR FIRST VIEWS

Instead doing that, we are going to create a View type that handles all of this logic for us. This will allow us to reuse some of our code and will simplify maintenance. To get started, we are first going to create a new Go source file to contain our view type.

```
$ atom views/view.go
```

Then add the code in Listing 6.11 to the new source file.

```
Listing 6.11: Creating the View type.

package views

import "html/template"

func NewView(files ...string) *View {
	files = append(files, "views/layouts/footer.gohtml")
	t, err := template.ParseFiles(files...)
	if err != nil {
	panic(err)
	}

	return &View{
	Template: t,
	}
}
type View struct {
	Template *template.Template
}
```

At the bottom of Listing 6.11 we are declaring our View type. It is a struct that contains one attribute - a pointer to a template.Template, which will eventually point to our compiled template.

Our view type is going to evolve over time, but for now all we really know is that it needs to store the parsed template that we want to execute, so we will start there.

## 6.3. CREATING A REUSABLE BOOTSTRAP LAYOUT

Above your type declaration we have the NewView function. This function takes in any number of strings as its argument using a variadic parameter (explained in Box 6.4).

We are creating the NewView function in order to make it easier to create views. This function is going to handle appending template files to the list of files provided, then it will parse template files, and finally will construct the *View for us and return it.

### Box 6.4. Variadic parameters (…)

A variadic parameter is essentially a function parameter that can be 0, 1, or any other number of items as long as they match the correct type, and are the last argument to the function call. This is represented by the triple dot (...) operator the argument type when declaring the NewView(). We are saying that our function can take in any number of strings, and Go merges all of these strings into a slice []string named files for us to use inside of the function.

Similarly, we can use the ... operator variable to "unravel" the items in a slice. This is necessary because the template.ParseFiles() function expects a variadic parameter of type string, meaning that it expects 0, 1, or more strings to be passed like we were doing before Listing 6.8, but files is not a string, it is a slice of strings. The ... operator allows us to take a slice of strings and have it treated as if it was a list of strings, template.ParseFiles("a", "b", "c").

Now that we have a View type, let's put it to use. Open up main.go and update our global templates to instead be of the *View. In order to access this type we need to import the views package and then reference the type views.View. We should also update the names of our variables to match their new type. This is all shown in Listing 6.12

NOTE: Our code won't compile just yet. You will need to proceed to the end of this section before it will be ready to run.

## Listing 6.12: Updating the global variables.

```go
package main

import (
    "html/template"
    "net/http"

    "lenslocked.com/views"

    "github.com/gorilla/mux"
)

var homeView views.View
var contactView views.View

// This all stays the same
```

Next we need to update our main function to handle constructing the views using the NewView function created. This is shown in Listing 6.11.

## Listing 6.13: Updating main ( ).

```
func main() {
    homeView = views.NewView("views/home.shtml")
    contactView = views.NewView("views/contact.shtml")

    r := mux.NewRouter()
    r.HandleFunc("/", home)
    r.HandleFunc("/contact", contact)
    http.ListenAndServe(":3000", r)
}
```

Notice how much shorter our main function becomes now that we have offloaded lot of the logic to the NewView function?

Finally, we need to update our home and contact functions to use the view variables. This is roughly the same as before, but instead of directly referencing

## 6.3. CREATING A REUSABLE BOOTSTRAP LAYOUT

the template we are going to access the Template field of each view object. This code is in Listing 6.14.

Note: I adjusted the error checking code to span a few lines in order to make sure the code isn't too wide for the ebook.

## Listing 6.14: Updating home () and contact ().

```go
func home(w http.ResponseWriter, r *http.Request) {
	w.Header().Set("Content-Type", "text/html")
	err := homeView.Template.Execute(w, nil)
	if err != nil {
	panic(err)
	}
}
func contact(w http.ResponseWriter, r *http.Request) {
	w.Header().Set("Content-Type", "text/html")
	err := contactView.Template.Execute(w, nil)
	if err != nil {
	panic(err)
	}
}
```

With all of these changes you should be able to restart your server and see the new views in action. Your pages will look exactly the same as before, but don't they look so much cleaner?

## Source code

The links below have the completed source code and a diff of all the code changed in this section.

- Completed - book.usegolang.com/6.3.2
- Changes - book.usegolang.com/6.3.2-diff

## 6.3.3 Creating the Bootstrap layout

We are finally ready to create a layout that uses Bootstrap². To do this we are first going to create our template file.

```
$ atom views/layouts/bootstrap.gohtml
```

Next, insert the code in Listing 6.15 into the new template file.

```html
Listing 6.15: Initial bootstrap.gohtml.
{{define "bootstrap"}}
<html lang="en">
<head>
<title>LensLocked.com</title>
<link href="//maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>
<div class="container-fluid">
  <!-- Our content will go here... -->
</div>
<!-- jquery & Bootstrap JS -->
<script src="//ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
<script src="//maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>
</body>
</html>
{{end}}
```

I'm not going to spend much time on the actual HTML here if you are interested in learning more about HTML I suggest you check out the beginner resources in the front of this book (see Section 1.3).

> http://bootstrap.com/docs/3.3/

## 6.3. CREATING A REUSABLE BOOTSTRAP LAYOUT

What I am going to talk about is a little issue we just ran into. We have a bootstrap layout created, but how are we going to insert our pages *inside* of the layout? We haven’t done that before.

Remember we included the footer template inside of our home and contact templates earlier in this chapter? What we would like to do something similar to that, but we want to insert a different template depending on what page the user is visiting.

There are several different ways to do this, but in my opinion the easiest is to always render the same template from within our bootstrap layout. Let's call that template *yield*.

Then when we want to change what page is rendered in our web application, we simply need to provide a new definition for the *yield* template.

Once again this is a situation where seeing the final code will help clear up any confusion. First we will open up our home and contact templates and turn them into named templates with the name *yield*.

```
$ atom views/home.gohtml
```

Then update the code to match Listing 6.16.

| Listing 6.16: Turn home.gohtml into a named template |
| {{define "yield"}} |
| <h1>Welcome to my awesome site!</h1> |
| {{template "footer"}} |
| {{end}} |

After that we need to update the contact template.
