```
fastServer . httptest.NewServer(http.HandlerFunc(func(w htt
    w.WriteHeader(http.StatusOK)
}))

slowURL := slowServer.URL
fastURL := fastServer.URL

want := fastURL
got := Racer(slowURL, fastURL)

    if got != want {
        t.Errorf("got %q, want %q", got, want)
    }

    slowServer.Close()
    fastServer.Close()
}
```

The syntax may look a bit busy but just take your time.

httptest.NewServer takes an http.HandlerFunc which we are sending in via an anonymous function.

http.HandlerFunc is a type that looks like this: type HandlerFunc func(ResponseWriter, *Request).

All it's really saying is it needs a function that takes a ResponseWriter and a Request, which is not too surprising for an HTTP server.

It turns out there's really no extra magic here, this is also how you would write a real HTTP server in Go. The only difference is we are wrapping it in an httptest.NewServer which makes it easier to use with testing, as it finds an open port to listen on and then you can close it when you're done with your test.

Inside our two servers, we make the slow one have a short time.Sleep when we get a request to make it slower than the other one. Both servers then write an OK response with w.WriteHeader(http.StatusOK) back to the caller.