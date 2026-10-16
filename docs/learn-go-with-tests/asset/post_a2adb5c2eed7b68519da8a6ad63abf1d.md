
<div id="blind-value"/>
</section>

<section id="game-end">
    <h1>Another great game of poker everyone!</h1>
    <p><a href="/league">Go check the league table</a></p>
</section>

</body>
<script type="application/javascript">
    const startGame = document.getElementById('game-start')

    const declareWinner = document.getElementById('declare-winner')
    const submitWinnerButton = document.getElementById('winner-submit'
    const winnerInput = document.getElementById('winner')

    const blindContainer = document.getElementById('blind-value'

    const gameContainer = document.getElementById('game')
    const gameEndContainer = document.getElementById('game-end')

    declareWinner.hidden = true
    gameEndContainer.hidden = true

    document.getElementById('start-game').addEventListener('click'
        startGame.hidden = true
        declareWinner.hidden = false

        const numberOfPlayers = document.getElementById('player-

    if (window['WebSocket']) {
        const conn = new WebSocket('ws://' + document.location

        submitWinnerButton.onclick = event => {
            conn.send(winnerInput.value)
            gameEndContainer.hidden = false
            gameContainer.hidden = true
        }

        conn.onclose = evt => {
```

conn.onclose = evt => {
    blindContainer.innerText = 'Connection closed'
}

conn.onmessage = evt => {
    blindContainer.innerText = evt.data
}

conn.onopen = function () {
    conn.send(numberOfPlayers)
}
}
})
</script>
</html>

The main changes is bringing in a section to enter the number of players and a section to display the blind value. We have a little logic to show/hide the user interface depending on the stage of the game.

Any message we receive via conn.onmessage we assume to be blind alerts and so we set the blindContainer.innerText accordingly.

How do we go about sending the blind alerts? In the previous chapter we introduced the idea of Game so our CLI code could call a Game and everything else would be taken care of including scheduling blind alerts. This turned out to be a good separation of concern.

```
type Game interface {
    Start(numberOfPlayers int)
    Finish(winner string)
}
```

When the user was prompted in the CLI for number of players it would Start the game which would kick off the blind alerts and when the user declared the winner they would Finish. This is the same requirements we have now, just a different way of getting the inputs; so we should look to re-use this concept if we can.

Our "real" implementation of Game is TexasHoldem

```
```go
type TexasHoldem struct {
    alerter BlindAlerter
    store   PlayerStore
}
```
```

By sending in a `BlindAlerter` TexasHoldem can schedule blind alerts to be sent to *wherever*

```
```go
type BlindAlerter interface {
    ScheduleAlertAt(duration time.Duration, amount int)
}
```
```

And as a reminder, here is our implementation of the `BlindAlerter` we use in the CLI.

```
```go
func StdOutAlerter(duration time.Duration, amount int) {
    time.AfterFunc(duration, func() {
        fmt.Fprintf(os.Stdout, "Blind is now %d\n", amount)
    })
}
```
```

This works in CLI because we *always want to send the alerts to* `os.Stdout` but this won't work for our web server. For every request we get a new `http.ResponseWriter` which we then upgrade to `*websocket.Conn`. So we can't know when constructing our dependencies where our alerts need to go.

For that reason we need to change `BlindAlerter.ScheduleAlertAt` so that it takes a destination for the alerts so that we can re-use it in our webserver.

Open blind_alerter.go and add the parameter to `io.Writer`

```
```go
type BlindAlerter interface {
    ScheduleAlertAt(duration time.Duration, amount int, to io.Writer)
}
```
```

```
```go
type BlindAlerterFunc func(duration time.Duration, amount int, to io.Writer)
```
```

```
```go
func (a BlindAlerterFunc) ScheduleAlertAt(duration time.Duration, amount int, to io.Writer) {
    a(duration, amount, to)
}
```
```

The idea of a `StdoutAlerter` doesn't fit our new model so just rename it to `Alerter`

```
```go
func Alerter(duration time.Duration, amount int, to io.Writer) {
    time.AfterFunc(duration, func() {
        fmt.Fprintf(to, "Blind is now %d\n", amount)
    })
}
```
```

If you try and compile, it will fail in `TexasHoldem` because it is calling `ScheduleAlertAt` without a destination, to get things compiling again *for now* hard-code it to `os.Stdout`.

Try and run the tests and they will fail because `SpyBlindAlerter` no longer implements `BlindAlerter`, fix this by updating the signature of `ScheduleAlertAt`, run the tests and we should still be green.

It doesn't make any sense for `TexasHoldem` to know where to send blind alerts. Let's now update `Game` so that when you start a game you declare *where* the alerts should go.

```
```go
type Game interface {
    Start(numberOfPlayers int, alertsDestination io.Writer)
    Finish(winner string)
}
```
```

Let the compiler tell you what you need to fix. The change isn't so bad:

- Update `TexasHoldem` so it properly implements `Game`
- In `CLI` when we start the game, pass in our `out` property (`cli.game.Start(numberOfPlayers, cli.out)`)
- In `TexasHoldem`'s test i use `game.Start(5, ioutil.Discard)` to fix the compilation problem and configure the alert output to be

discarded

If you've got everything right, everything should be green! Now we can try and use Game within Server.

## Write the test first

The requirements of CLI and Server are the same! It's just the delivery mechanism is different.

Let's take a look at our CLI test for inspiration.

```
t.Run("start game with 3 players and finish game with 'Chris' as
    game := &GameSpy{}

    out := &bytes.Buffer{}
    in := userSends("3", "Chris wins")

    poker.NewCLI(in, out, game).PlayPoker()

    assertMessagesSentToUser(t, out, poker.PlayerPrompt)
    assertGameStartedWith(t, game, 3)
    assertFinishCalledWith(t, game, "Chris")
})
```

It looks like we should be able to test drive out a similar outcome using GameSpy

Replace the old websocket test with the following

```
t.Run("start a game with 3 players and declare Ruth the winner",
    game := &poker.GameSpy{}
    winner := "Ruth"
    server := httptest.NewServer(mustMakePlayerServer(t, dummyPlayerStore
    ws := mustDialWS(t, "ws"+strings.TrimPrefix(server.URL, "http

    defer server.Close()
    defer ws.Close()
```

```
```go
writeWSMessage(t, ws, "3")
writeWSMessage(t, ws, winner)
time.Sleep(10 * time.Millisecond)
	assertGameStartedWith(t, game, 3)
	assertFinishCalledWith(t, game, winner)
})```
```

- As discussed we create a spy Game and pass it into mustMakePlayerServer (be sure to update the helper to support this).
- We then send the web socket messages for a game.
- Finally we assert that the game is started and finished with what we expect.

## Try to run the test

You'll have a number of compilation errors around mustMakePlayerServer in other tests. Introduce an unexported variable dummyGame and use it through all the tests that aren't compiling

```
```go
var (
	dummyGame = &GameSpy{}
)
```
```

The final error is where we are trying to pass in Game to NewPlayerServer but it doesn't support it yet

```
```
./server_test.go:21:38: too many arguments in call to "github.com/quii/learn-go-with-tests/WebSockets/v2".NewPlayerServer
have     ("github.com/quii/learn-go-with-tests/WebSockets/v2".PlayerStore,
"github.com/quii/learn-go-with-tests/WebSockets/v2".Game)
want     ("github.com/quii/learn-go-with-tests/WebSockets/v2".PlayerStore)
```
```

## Write the minimal amount of code for the test to run and check the failing test output

Just add it as an argument for now just to get the test running

```
func NewPlayerServer(store PlayerStore, game Game) (*PlayerServer
```

Finally!

```
===
RUN
TestGame/start_a_game_with_3_players_and_declare_Ruth_the_winner
--- FAIL: TestGame (0.01s)
--- FAIL:
TestGame/start_a_game_with_3_players_and_declare_Ruth_the_winner (0.01s)
    server_test.go:146: wanted Start called with 3 but got 0
    server_test.go:147: expected finish called with 'Ruth' but got ''
FAIL
```

## Write enough code to make it pass

We need to add `Game` as a field to `PlayerServer` so that it can use it when it gets requests.

```
type PlayerServer struct {
    store PlayerStore
    http.Handler
    template *template.Template
    game     Game
}
```

(We already have a method called `game` so rename that to `playGame`)
