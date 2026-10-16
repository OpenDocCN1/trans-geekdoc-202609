Now that we know there is one element in our `winCalls` slice we can safely reference the first one and check it is equal to `player`.

# Try to run the test

```
=== RUN   TestStoreWins/it_records_wins_on_POST
   --- FAIL: TestStoreWins/it_records_wins_on_POST (0.00s)
         server_test.go:86: did not store correct winner got
'Bob' want 'Pepper'
```

# Write enough code to make it pass

```
//server.go
func (p *PlayerServer) processWin(w http.ResponseWriter, r *http
    player := strings.TrimPrefix(r.URL.Path, "/players/")
    p.store.RecordWin(player)
    w.WriteHeader(http.StatusAccepted)
}
```

We changed `processWin` to take `http.Request` so we can look at the URL to extract the player's name. Once we have that we can call our `store` with the correct value to make the test pass.

# Refactor

We can DRY up this code a bit as we're extracting the player name the same way in two places

```
//server.go
func (p *PlayerServer) ServeHTTP(w http.ResponseWriter, r *http.
    player := strings.TrimPrefix(r.URL.Path, "/players/")

    switch r.Method {
    case http.MethodPost:
```