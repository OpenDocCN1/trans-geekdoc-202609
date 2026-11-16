```
func exampleHandler(w http.ResponseWriter, r *http.Request) {
	category := r.PathValue("category")
	itemID := r.PathValue("itemID")

	...
}
```

The r.PathValue() method always returns a string value, and it's important to remember that this can be *any value* that the user includes in the URL — so you should validate or sanity check the value before doing anything important with it.

# Using wildcard segments in practice

OK, let's get back to our application and update it to include a new {id} wildcard segment in the /snippet/view route, so that our routes look like this:

| Route pattern | Handler | Action |
| :--- | :--- | :--- |
| `/{$}` | home | Display the home page |
| `/snippet/view/{id}` | snippetView | Display a specific snippet |
| `/snippet/create` | snippetCreate | Display a form for creating a new snippet |

Open up your main.go file, and make this change like so:

```
File: main.go

package main

...

func main() {
	mux := http.NewServeMux()
	mux.HandleFunc("/{$}", home)
	mux.HandleFunc("/snippet/view/{id}", snippetView) // Add the {id} wildcard segment
	mux.HandleFunc("/snippet/create", snippetCreate)

	log.Print("starting server on :4000")

	err := http.ListenAndServe(":4000", mux)
	log.Fatal(err)
}
```

Now let's head to our snippetView handler and update it to retrieve the id value from the request URL path. Later in the book, we'll use this id value to select a specific snippet from a database, but for now we'll just echo the id back to the user as part of the HTTP