```
func (p *PlayerServer) processWin(w http.ResponseWriter) {
    w.WriteHeader(http.StatusAccepted)
}
```

This makes the routing aspect of ServeHTTP a bit clearer and means our next iterations on storing can just be inside processWin.

Next, we want to check that when we do our POST /players/{name} that our PlayerStore is told to record the win.

# Write the test first

We can accomplish this by extending our StubPlayerStore with a new RecordWin method and then spy on its invocations.

```
//server_test.go
type StubPlayerStore struct {
    scores   map[string]int
    winCalls []string
}

func (s *StubPlayerStore) GetPlayerScore(name string) int {
    score := s.scores[name]
    return score
}

func (s *StubPlayerStore) RecordWin(name string) {
    s.winCalls = append(s.winCalls, name)
}
```

Now extend our test to check the number of invocations for a start

```
//server_test.go
func TestStoreWins(t *testing.T) {
    store := StubPlayerStore{
        map[string]int{},
    }
    server := &PlayerServer{&store}
```