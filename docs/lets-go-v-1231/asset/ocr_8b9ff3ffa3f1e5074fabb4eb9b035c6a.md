```
err = ts.ExecuteTemplate(w, "base", nil)
if err != nil {
  // And we also need to update the code here to use the structured logger
  // too.
  app.logger.Error(err.Error(), "method", r.Method, "uri", r.URL.RequestURI())
  http.Error(w, "Internal Server Error", http.StatusInternalServerError)
}

// Change the signature of the snippetView handler so it is defined as a method
// against *application.
func (app *application) snippetView(w http.ResponseWriter, r *http.Request) {
  id, err := strconv.Atoi(r.PathValue("id"))
  if err != nil || id < 1 {
    http.NotFound(w, r)
    return
  }

  fmt.Fprintf(w, "Display a specific snippet with ID %d...", id)
}

// Change the signature of the snippetCreate handler so it is defined as a method
// against *application.
func (app *application) snippetCreate(w http.ResponseWriter, r *http.Request) {
  w.Write([]byte("Display a form for creating a new snippet..."))
}

// Change the signature of the snippetCreatePost handler so it is defined as a method
// against *application.
func (app *application) snippetCreatePost(w http.ResponseWriter, r *http.Request) {
  w.WriteHeader(http.StatusCreated)
  w.Write([]byte("Save a new snippet..."))
}

```

And finally let's wire things together in our main.go file: