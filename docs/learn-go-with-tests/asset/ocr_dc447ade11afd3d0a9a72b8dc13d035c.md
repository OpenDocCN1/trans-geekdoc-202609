server_test.go:143: timed out
server_test.go:150: got "", want "Blind is 100"

# Write enough code to make it pass

Finally, we can now change our server code, so it sends our WebSocket connection to the game when it starts

```
```go
func (p *PlayerServer) webSocket(w http.ResponseWriter, r *http.
    ws := newPlayerServerWS(w, r)

    numberOfPlayersMsg := ws.WaitForMsg()
    numberOfPlayers, _ := strconv.Atoi(numberOfPlayersMsg)
    p.game.Start(numberOfPlayers, ws)

    winner := ws.WaitForMsg()
    p.game.Finish(winner)
}
```
```

# Refactor

The server code was a very small change so there's not a lot to change here but the test code still has a time.Sleep call because we have to wait for our server to do its work asynchronously.

We can refactor our helpers assertGameStartedWith and assertFinishCalledWith so that they can retry their assertions for a short period before failing.

Here's how you can do it for assertFinishCalledWith and you can use the same approach for the other helper.

```
```go
func assertFinishCalledWith(t testing.TB, game *GameSpy, winner
    t.Helper()

    passed := retryUntil(500*time.Millisecond, func() bool {
        return game.FinishCalledWith == winner
```
```