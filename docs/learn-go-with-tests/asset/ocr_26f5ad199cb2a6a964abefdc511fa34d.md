```
t.Run("when you don't get a 200 you get a status error", func(t
    svr := httptest.NewServer(http.HandlerFunc(func(res http.Res
        res.WriteHeader(http.StatusTeapot)
    }))
    defer svr.Close()

    _, err := DumbGetter(svr.URL)

    if err == nil {
        t.Fatal("expected an error")
    }

    var got BadStatusError
    isBadStatusError := errors.As(err, &got)
    want := BadStatusError{URL: svr.URL, Status: http.StatusTeap

    if !isBadStatusError {
        t.Fatalf("was not a BadStatusError, got %T", err)
    }

    if got != want {
        t.Errorf("got %v, want %v", got, want)
    }
})
```

In this case we are using errors.As to try and extract our error into our custom type. It returns a `bool` to denote success and extracts it into `got` for us.