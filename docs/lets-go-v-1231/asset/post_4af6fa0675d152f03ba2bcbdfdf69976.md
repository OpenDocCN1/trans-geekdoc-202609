
File: go.mod

module snippetbox.alexedwards.net

go 1.23.0

require github.com/go-sql-driver/mysql v1.8.1

require (
	filippo.io/edwards25519 v1.1.0 // indirect
	github.com/justinas/alice v1.2.0 // indirect
)

Again, this is currently listed as an indirect dependency because we're not actually importing and using it in our code yet.

Let's go ahead and do that now, updating our routes.go file to use the justinas/alice package as follows:

File: cmd/web/routes.go

package main

import (
	"net/http"

	"github.com/justinas/alice" // New import
)

func (app *application) routes() http.Handler {
	mux := http.NewServeMux()

	fileServer := http.FileServer(http.Dir("./ui/static/"))
	mux.Handle("GET /static/", http.StripPrefix("/static", fileServer))

	mux.HandleFunc("GET /{$}", app.home)
	mux.HandleFunc("GET /snippet/view/{id}", app.snippetView)
	mux.HandleFunc("GET /snippet/create", app.snippetCreate)
	mux.HandleFunc("POST /snippet/create", app.snippetCreatePost)

	// Create a middleware chain containing our 'standard' middleware
	// which will be used for every request our application receives.
	standard := alice.New(app.recoverPanic, app.logRequest, commonHeaders)

	// Return the 'standard' middleware chain followed by the servemux.
	return standard.Then(mux)
}

If you want, feel free to restart the application at this point. You should find that everything compiles correctly and the application continues to work in the same way as before. You can also run go mod tidy again to remove the // indirect annotation from the go.mod file.

## Processing forms

In this section of the book we're going to focus on adding an HTML form for creating new snippets. The form will look a bit like this:

![](img/c3e650db0d8dfdecc0f8e34a67719f65_193_0.png)

The high-level flow for processing this form will follow a standard Post-Redirect-Get pattern and will work like so:

- 1. The user is shown the blank form when they make a GET request to /snippet/create.
- 2. The user completes the form and it's submitted to the server via a POST request to /snippet/create.
- 3. The form data will be validated by our snippetCreatePost handler. If there are any validation failures the form will be re-displayed with the appropriate form fields highlighted. If it passes our validation checks, the data for the new snippet will be added to the database and then we'll redirect the user to GET /snippet/view/{id}.

As part of this you'll learn:

- How to parse and access form data sent in a POST request.
- Some techniques for performing common validation checks on the form data.
- A user-friendly pattern for alerting the user to validation failures and re-populating form fields with previously submitted data.
- How to keep your handlers clean by using helpers for form processing and validation.

## Setting up an HTML form

Let's begin by making a new ui/html/pages/create.tmpl file to hold the HTML for the form:

```
$ touch ui/html/pages/create.tmpl
```

... and then add the following markup, using the same template patterns that we used earlier in the book.

File: ui/html/pages/create.tmpl

{{define "title"}}Create a New Snippet{{end}}

{{define "main"}}
<form action='/snippet/create' method='POST'>
	<div>
		<label>Title:</label>
		<input type='text' name='title'>
	</div>
	<div>
		<label>Content:</label>
		<textarea name='content'></textarea>
	</div>
	<div>
		<label>Delete in:</label>
		<input type='radio' name='expires' value='365' checked> One Year
		<input type='radio' name='expires' value='7'> One Week
		<input type='radio' name='expires' value='1'> One Day
	</div>
	<div>
		<input type='submit' value='Publish snippet'>
	</div>
</form>
{{end}}
```

There's nothing particularly special about this so far. Our main template contains a standard HTML form which sends three form values: title, content and expires (the number of days until the snippet should expire). The only thing to really point out is the form's action and method attributes — we've set these up so that the form will POST the data to the URL /snippet/create when it's submitted.

Now let's add a new ‘Create snippet’ link to the navigation bar for our application, so that clicking it will take the user to this new form.

File: ui/html/partials/nav.tmpl

{{define "nav"}}
<nav>
  <a href="/">Home</a>
  <!-- Add a link to the new form -->
  <a href="/snippet/create">Create snippet</a>
</nav>
{{end}}
```

And finally, we need to update the snippetCreate handler so that it renders our new page like so:

File: cmd/web/handlers.go

package main

...

func (app *application) snippetCreate(w http.ResponseWriter, r *http.Request) {
  data := app.newTemplateData(r)

  app.render(w, r, http.StatusOK, "create.tmpl", data)
}

...
```

At this point you can fire up the application and visit http://localhost:4000/snippet/create in your browser. You should see a form which looks like this:

![](img/c3e650db0d8dfdecc0f8e34a67719f65_197_0.png)

- Home
- Create snippet

Title:

Content:

Delete in:

- One Year
- One Week
- One Day

Publish snippet

## Parsing form data

Thanks to the work we did previously in the foundations section, any POST /snippets/create requests are already being dispatched to our snippetCreatePost handler. We’ll now update this handler to process and use the form data when it’s submitted.

At a high-level, we can break this down into two distinct steps.

- First, we need to use the r.ParseForm() method to parse the request body. This checks that the request body is well-formed, and then stores the form data in the request’s r.PostForm map. If there are any errors encountered when parsing the body (like there is no body, or it’s too large to process) then it will return an error. The r.ParseForm() method is also idempotent; it can safely be called multiple times on the same request without any side-effects.

- We can then get to the form data contained in r.PostForm by using the r.PostForm.Get() method. For example, we can retrieve the value of the title field with r.PostForm.Get("title"). If there is no matching field name in the form this will return the empty string "".

Open your cmd/web/handlers.go file and update it to include the following code:

File: cmd/web/handlers.go

package main

...

func (app *application) snippetCreatePost(w http.ResponseWriter, r *http.Request) {
	// First we call r.ParseForm() which adds any data in POST request bodies
	// to the r.PostForm map. This also works in the same way for PUT and PATCH
	// requests. If there are any errors, we use our app.ClientError() helper to
	// send a 400 Bad Request response to the user.
	err := r.ParseForm()
	if err != nil {
		app.clientError(w, http.StatusBadRequest)
		return
	}

	// Use the r.PostForm.Get() method to retrieve the title and content
	// from the r.PostForm map.
	title := r.PostForm.Get("title")
	content := r.PostForm.Get("content")

	// The r.PostForm.Get() method always returns the form data as a *string*.
	// However, we're expecting our expires value to be a number, and want to
	// represent it in our Go code as an integer. So we need to manually convert
	// the form data to an integer using strconv.Atoi(), and we send a 400 Bad
	// Request response if the conversion fails.
	expires, err := strconv.Atoi(r.PostForm.Get("expires"))
	if err != nil {
		app.clientError(w, http.StatusBadRequest)
		return
	}

	id, err := app.snippets.Insert(title, content, expires)
	if err != nil {
		app.serverError(w, r, err)
		return
	}

	http.Redirect(w, r, fmt.Sprintf("/snippet/view/%d", id), http.StatusSeeOther)
}
```

Alright, let's give this a try! Restart the application and try filling in the form with the title
and content of a snippet, a bit like this:

## Snippetbox

Home Create snippet

Title:

From time to time

Content:

From time to time
The clouds give rest
To the moon-beholders.
- Matsuo Bashō

Delete in:

- One Year
- One Week
- One Day

Publish snippet

And then submit the form. If everything has worked, you should be redirected to a page displaying your new snippet like so:
