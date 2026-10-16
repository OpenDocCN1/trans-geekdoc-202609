As Pedro says, we *could* write a test for the status error like so.

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

    want := fmt.Sprintf("did not get 200 from %s, got %d", svr.L
    got := err.Error()

    if got != want {
        t.Errorf(`got "%v", want "%v"`, got, want)
    }
})
```

This test creates a server which always returns `StatusTeapot` and then we use its URL as the argument to `DumbGetter` so we can see it handles non 200 responses correctly.

# Problems with this way of testing

This book tries to emphasise *listen to your tests* and this test doesn't *feel* good:

+   - We're constructing the same string as production code does to test it
+   - It's annoying to read and write
+   - Is the exact error message string what we're *actually concerned with* ?