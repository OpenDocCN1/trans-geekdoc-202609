# Additional information

# Checking for specific errors

A couple of times in this chapter we’ve used the errors.Is() function to check whether an error matches a specific value. Like this:

```
if errors.Is(err, models.ErrNoRecord) {
	http.NotFound(w, r)
} else {
	app.serverError(w, r, err)
}
```

In very old versions of Go (prior to 1.13), the idiomatic way to compare errors was to use the equality operator ==, like so:

```
if err == models.ErrNoRecord {
	http.NotFound(w, r)
} else {
	app.serverError(w, r, err)
}
```

But, while this code still complies, it’s safer and best practice to use the errors.Is() function instead.

This is because Go 1.13 introduced the ability to add additional information to errors by wrapping them. If an error happens to get wrapped, a entirely new error value is created — which in turn means that it’s not possible to check the value of the original underlying error using the regular == equality operator.

The errors.Is() function works by unwrapping errors as necessary before checking for a match.

There is also another function, errors.As() which you can use to check if a (potentially wrapped) error has a specific type. We’ll use this later on this book.

# Shorthand single-record queries

I’ve deliberately made the code in SnippetModel.Get() slightly long-winded to help clarify and emphasize what is going on behind the scenes of the code.

In practice, you can shorten the code slightly by leveraging the fact that errors from