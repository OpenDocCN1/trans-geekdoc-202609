```
response := httptest.NewRecorder()

server.ServeHTTP(response, request)

assertStatus(t, response.Code, http.StatusAccepted)
})
}
```

For a start let's just check we get the correct status code if we hit the particular route with POST. This lets us drive out the functionality of accepting a different kind of request and handling it differently to `GET` `/players/{name}`. Once this works we can then start asserting on our handler's interaction with the store.

# Try to run the test

```
=== RUN   TestStoreWins/it_returns_accepted_on_POST
--- FAIL: TestStoreWins/it_returns_accepted_on_POST (0.00s)
server_test.go:70: did not get correct status, got 404, want 202
```

# Write enough code to make it pass

Remember we are deliberately committing sins, so an `if` statement based on the request's method will do the trick.

```
//server.go
func (p *PlayerServer) ServeHTTP(w http.ResponseWriter, r *http.

    if r.Method == http.MethodPost {
        w.WriteHeader(http.StatusAccepted)
        return
    }

player := strings.TrimPrefix(r.URL.Path, "/players/")

score := p.store.GetPlayerScore(player)
```