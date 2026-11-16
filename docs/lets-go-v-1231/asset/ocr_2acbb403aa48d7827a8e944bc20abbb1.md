Show suggested code

# Step 3

Update the main navigation bar for the application to include a link to the new ‘About’ page (the link should be visible to all users, irrespective of whether they are logged in or not).

Show suggested code

# Step 4

Update the about handler so that it renders the about.tmpl file that you’ve just created. Then sanity check that the new page and navigation works by visiting https://localhost:4000/about in your browser.

Show suggested code

# Suggested code

# Suggested code for step 1

```
File: cmd/web/handlers.go

package main

...

func (app *application) about(w http.ResponseWriter, r *http.Request) {
    // Some code will go here later...
}
```