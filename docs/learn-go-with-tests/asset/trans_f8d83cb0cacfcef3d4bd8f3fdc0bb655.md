

<div id="blind-value"/>
</section>

<section id="game-end">
    <h1>又一场精彩的扑克游戏，大家！</h1>
    <p><a href="/league">去查看联赛积分榜</a></p>
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

主要的改动是引入一个输入玩家数量的区域和一个显示盲注值的区域。我们有一些逻辑来根据游戏阶段显示/隐藏用户界面。

我们通过 conn.onmessage 接收到的任何消息都假设为盲注提醒，因此我们相应地设置 blindContainer.innerText。

我们该如何发送盲注提醒？在上一章中，我们引入了 Game 的概念，这样我们的 CLI 代码就可以调用 Game，其余一切都将被处理，包括安排盲注提醒。这被证明是一个良好的关注点分离。

```
type Game interface {
    Start(numberOfPlayers int)
    Finish(winner string)
}
```

当用户在 CLI 中被提示输入玩家数量时，它会启动游戏，这将触发盲注提醒，而当用户宣布获胜者时则会结束游戏。这与我们现在的要求相同，只是获取输入的方式不同；因此我们应该尝试重用这个概念，如果可以的话。

我们 Game 的“真实”实现是 TexasHoldem

```
```go
type TexasHoldem struct {
    alerter BlindAlerter
    store   PlayerStore
}
```
```

通过传入一个 `BlindAlerter`，TexasHoldem 可以安排盲注提醒发送到 *任何地方*

```
```go
type BlindAlerter interface {
    ScheduleAlertAt(duration time.Duration, amount int)
}
```
```

作为提醒，这里是我们 CLI 中使用的 `BlindAlerter` 的实现。

```
```go
func StdOutAlerter(duration time.Duration, amount int) {
    time.AfterFunc(duration, func() {
        fmt.Fprintf(os.Stdout, "Blind is now %d\n", amount)
    })
}
```
```

这在 CLI 中有效，因为我们 *总是希望将提醒发送到* `os.Stdout`，但这对我们的 Web 服务器不起作用。对于每个请求，我们都会得到一个新的 `http.ResponseWriter`，然后将其升级为 `*websocket.Conn`。因此，在构建依赖项时我们无法知道提醒需要去往何处。

因此我们需要更改 `BlindAlerter.ScheduleAlertAt`，使其接受提醒的目的地，以便我们可以在 Web 服务器中重用它。

打开 blind_alerter.go 并向 `io.Writer` 添加参数

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

`StdoutAlerter` 的概念不适合我们的新模型，因此只需将其重命名为 `Alerter`

```
```go
func Alerter(duration time.Duration, amount int, to io.Writer) {
    time.AfterFunc(duration, func() {
        fmt.Fprintf(to, "Blind is now %d\n", amount)
    })
}
```
```

如果你尝试编译，它将在 `TexasHoldem` 中失败，因为它在没有目的地的情况下调用了 `ScheduleAlertAt`，为了暂时让代码重新编译，*暂时*将其硬编码为 `os.Stdout`。

尝试运行测试，它们将失败，因为 `SpyBlindAlerter` 不再实现 `BlindAlerter`，通过更新 `ScheduleAlertAt` 的签名来修复此问题，运行测试，我们应该仍然是绿色的。

`TexasHoldem` 知道盲注提醒发送到哪里是没有意义的。现在让我们更新 `Game`，以便在启动游戏时声明提醒应该去往 *哪里*。

```
```go
type Game interface {
    Start(numberOfPlayers int, alertsDestination io.Writer)
    Finish(winner string)
}
```
```

让编译器告诉你需要修复什么。更改并不复杂：

- 更新 `TexasHoldem` 使其正确实现 `Game`
- 在 `CLI` 中启动游戏时，传入我们的 `out` 属性（`cli.game.Start(numberOfPlayers, cli.out)`）
- 在 `TexasHoldem` 的测试中我使用 `game.Start(5, ioutil.Discard)` 来修复编译问题并将提醒输出配置为

丢弃

如果一切正确，一切都应该是绿色的！现在我们可以尝试在 Server 中使用 Game。

## 首先编写测试

CLI 和 Server 的要求是相同的！只是交付机制不同。

让我们看看我们的 CLI 测试以获取灵感。

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

看起来我们应该能够使用 GameSpy 测试驱动出类似的结果

用以下内容替换旧的 websocket 测试

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

- 如讨论所述，我们创建一个 spy Game 并将其传递给 mustMakePlayerServer（请确保更新 helper 以支持此功能）。
- 然后我们为游戏发送 web socket 消息。
- 最后我们断言游戏以我们期望的方式启动和结束。

## 尝试运行测试

你会在其他测试中遇到关于 mustMakePlayerServer 的编译错误。引入一个未导出的变量 dummyGame 并在所有未编译的测试中使用它

```
```go
var (
    dummyGame = &GameSpy{}
)
```
```

最后的错误是我们尝试将 Game 传递给 NewPlayerServer 但它还不支持

```
```
./server_test.go:21:38: too many arguments in call to "github.com/quii/learn-go-with-tests/WebSockets/v2".NewPlayerServer
have     ("github.com/quii/learn-go-with-tests/WebSockets/v2".PlayerStore,
"github.com/quii/learn-go-with-tests/WebSockets/v2".Game)
want     ("github.com/quii/learn-go-with-tests/WebSockets/v2".PlayerStore)
```
```

## 编写最少的代码使测试运行并检查失败的测试输出

现在就把它作为参数添加以便让测试运行

```
func NewPlayerServer(store PlayerStore, game Game) (*PlayerServer
```

最后！

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

## 编写足够多的代码使其通过

我们需要将 `Game` 添加为 `PlayerServer` 的字段，以便它在收到请求时可以使用它。

```
type PlayerServer struct {
    store PlayerStore
    http.Handler
    template *template.Template
    game     Game
}
```

（我们已经有一个名为 `game` 的方法，因此将其重命名为 `playGame`）

