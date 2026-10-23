```
```go
if err != nil {
    switch {
    case errors.Is(err, data.ErrRecordNotFound):
        app.notFoundResponse(w, r)
    default:
        app.serverErrorResponse(w, r, err)
    }
    return
}

// Return a 200 OK status code along with a success message.
err = app.writeJSON(w, http.StatusOK, envelope{"message": "movie successfully deleted"}, nil)
if err != nil {
    app.serverErrorResponse(w, r, err)
}
```
```

Note: You may prefer to send an empty response body and a `204 No Content` status code here, rather than a `"movie successfully deleted"` message. It really depends on who your clients are — if they are humans, then sending a message similar to the above is a nice UX touch; if they are machines, then a `204 No Content` response is probably sufficient.

Finally, we need to hook up the new route in our `cmd/api/routes.go` file:

```
File: cmd/api/routes.go
```