`http.Request` object that the `http.HandlerFunc` receives as an argument. Some other examples of input are the `r.Header`, `r.Body`, and `r.URL` members.

We finalize the request by writing it out to our `http.ResponseWriter`. Notice that we didn't explicitly send a response code. If we write out to the response without a code, the `net/http` package will assume that the response is a `200 OK`. This means that if something did happen to go wrong, we should set the response code via the `rw.WriteHeader()` method.

```
http.ListenAndSet(":8080", nil)
```

The last bit of this program starts the server, we pass `nil` as our handler, which assumes that the HTTP requests will be handled by the `net/http` packages default `http.ServeMux`, which is configured using `http.Handle` and `http.HandleFunc`, respectively.

And that is all you need to be able to generate markdown as a service in Go. It is a surprisingly small amount of code for the amount of heavy lifting it does. In the next chapter we will learn how to deploy this application to the web using Heroku.