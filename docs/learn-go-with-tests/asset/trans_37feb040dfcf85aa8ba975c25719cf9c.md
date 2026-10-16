
```
func (cli *CLI) playPoker() {
    fmt.Fprint(cli.out, PlayerPrompt)

    numberOfPlayersInput := cli.readLine()
    numberOfPlayers, _ := strconv.Atoi(strings.TrimSpace(numberOfPlayersInput))

    cli.game.Start(numberOfPlayers)

    winnerInput := cli.readLine()
    winner := extractWinner(winnerInput)

    cli.game.Finish(winner)
}

func extractWinner(userInput string) string {
    return strings.Replace(userInput, " wins\n", "", 1)
}

func (cli *CLI) readLine() string {
    cli.in.Scan()
    return cli.in.Text()
}
```

从“领域”的角度来看：

- 我们希望`Start`一个`Game`，表明有多少人在玩
- 我们希望`Finish`一个`Game`，宣布获胜者

新的`Game`类型为我们封装了这些。

通过这一改动，我们将`BlindAlerter`和`PlayerStore`传递给了`Game`，因为现在它负责警报和存储结果。

我们的`CLI`现在只关心：

- 使用其现有的依赖项构造`Game`（我们接下来会进行重构）
- 将用户输入解释为对`Game`的方法调用

我们希望尽量避免“大规模”重构，因为那样会让我们长时间处于测试失败的状态，从而增加出错的机会。（如果你在一个大型/分布式团队中工作，这一点格外重要）

我们要做的第一件事是重构`Game`，以便将其注入到`CLI`中。我们将在测试中做最小的改动来促进这一点，然后我们会看看如何将测试分解为解析用户输入和游戏管理两个主题。

我们现在需要做的就是修改`NewCLI`。

```
func NewCLI(in io.Reader, out io.Writer, game *Game) *CLI {
    return &CLI{
        in:    bufio.NewScanner(in),
        out:   out,
        game:  game,
    }
}
```

这已经感觉是一个改进。我们的依赖更少了，依赖列表也反映了我们的整体设计目标，即`CLI`负责输入/输出，并将游戏特定的操作委托给`Game`。

如果你尝试编译，会遇到问题。你应该能够自己解决这些问题。现在不要担心为`Game`创建任何模拟（mock），只需初始化真实的`Game`，让所有代码编译通过，测试变绿。

要做到这一点，你需要创建一个构造函数。

```
func NewGame(alerters BlindAlerter, store PlayerStore) *Game {
    return &Game{
        alerter: alerter,
        store:   store,
    }
}
```

以下是一个修复中测试的配置示例

```
```go
stdout := &bytes.Buffer{}
in := strings.NewReader("7\n")
blindAlerter := &SpyBlindAlerter{}
game := poker.NewGame(blindAlerter, dummyPlayerStore)

cli := poker.NewCLI(in, stdout, game)
cli.PlayPoker()
```
```

修复测试并重新变绿应该不需要太多功夫（这正是重点！），但在进入下一阶段之前，请确保也修复了`main.go`。

```
```go
// main.go
game := poker.NewGame(poker.BlindAlerterFunc(poker.StdOutAlerter))
cli := poker.NewCLI(os.Stdin, os.Stdout, game)
cli.PlayPoker()
```
```

既然我们已经提取出了`Game`，我们应该将游戏特定的断言移到与`CLI`分离的测试中。

这只是一个复制`CLI`测试的练习，但依赖更少。

```
```go
func TestGame_Start(t *testing.T) {
    t.Run("schedules alerts on game start for 5 players", func(t *testing.T) {
        blindAlerter := &poker.SpyBlindAlerter{}
        game := poker.NewGame(blindAlerter, dummyPlayerStore)

        game.Start(5)

        cases := []poker.ScheduledAlert{
            {At: 0 * time.Second, Amount: 100},
            {At: 10 * time.Minute, Amount: 200},
            {At: 20 * time.Minute, Amount: 300},
            {At: 30 * time.Minute, Amount: 400},
            {At: 40 * time.Minute, Amount: 500},
            {At: 50 * time.Minute, Amount: 600},
            {At: 60 * time.Minute, Amount: 800},
            {At: 70 * time.Minute, Amount: 1000},
            {At: 80 * time.Minute, Amount: 2000},
            {At: 90 * time.Minute, Amount: 4000},
        }
```
```

```
{At: 100 * time.Minute, Amount: 8000},
}

checkSchedulingCases(cases, t, blindAlerter)
})

t.Run("schedules alerts on game start for 7 players", func(t *testing.T) {
    blindAlerter := &poker.SpyBlindAlerter{}
    game := poker.NewGame(blindAlerter, dummyPlayerStore)

    game.Start(7)

    cases := []poker.ScheduledAlert{
        {At: 0 * time.Second, Amount: 100},
        {At: 12 * time.Minute, Amount: 200},
        {At: 24 * time.Minute, Amount: 300},
        {At: 36 * time.Minute, Amount: 400},
    }

    checkSchedulingCases(cases, t, blindAlerter)
})

}

func TestGame_Finish(t *testing.T) {
    store := &poker.StubPlayerStore{}
    game := poker.NewGame(dummyBlindAlerter, store)
    winner := "Ruth"

    game.Finish(winner)
    poker.AssertPlayerWin(t, store, winner)
}
```

现在，扑克游戏开始时发生的事情背后的意图变得更加清晰。

请确保也将游戏结束时的测试移过去。

一旦我们满意地将测试移到了游戏逻辑上，我们就可以简化`CLI`的测试，使其更清晰地反映我们预期的职责：

- 处理用户输入，并在适当时调用`Game`的方法
- 发送输出
- 关键的是，它不关心游戏的实际运作方式

要做到这一点，我们必须让`CLI`不再依赖于具体的`Game`类型，而是接受一个带有`Start(numberOfPlayers)`和`Finish(winner)`方法的接口。然后我们可以创建该接口的间谍（spy），并验证正确的调用。

这时我们意识到命名有时会很尴尬。将`Game`重命名为`TexasHoldem`（因为我们正在玩的是这种游戏），新的接口将命名为`Game`。这保持了我们`CLI`不关心实际游戏以及`Start`和`Finish`时发生什么的理念。

```
type Game interface {
    Start(numberOfPlayers int)
    Finish(winner string)
}
```

将`CLI`中所有对`*Game`的引用替换为`Game`（我们的新接口）。在重构过程中，一如既往地不断运行测试，确保一切保持绿色。

现在我们已经将`CLI`与`TexasHoldem`解耦，可以使用间谍来检查`Start`和`Finish`是否在我们期望的时候以正确的参数被调用。

创建一个实现`Game`接口的间谍。

```
type GameSpy struct {
    StartedWith int
    FinishedWith string
}
```

```
func (g *GameSpy) Start(numberOfPlayers int) {
    g.StartedWith = numberOfPlayers
}

func (g *GameSpy) Finish(winner string) {
    g.FinishedWith = winner
}
```

将任何测试游戏特定逻辑的`CLI`测试替换为对我们`GameSpy`被调用方式的检查。这将使`CLI`的职责在我们的测试中清晰地体现出来。

以下是一个正在修复的测试示例；尝试自己完成其余部分，如果卡住了可以查看源代码。

```
t.Run("it prompts the user to enter the number of players at the start", func(t *testing.T) {
    stdout := &bytes.Buffer{}
    in := strings.NewReader("7\n")
    game := &GameSpy{}

    cli := poker.NewCLI(in, stdout, game)
    cli.PlayPoker()

    gotPrompt := stdout.String()
    wantPrompt := poker.PlayerPrompt

    if gotPrompt != wantPrompt {
        t.Errorf("got %q, want %q", gotPrompt, wantPrompt)
    }

    if game.StartedWith != 7 {
        t.Errorf("wanted Start called with 7 but got %d", game.StartedWith)
    }
})
```

现在我们已经有了清晰的关注点分离，检查`CLI`中与IO相关的边界情况应该更容易了。

我们需要处理这样一个场景：用户在提示输入玩家数量时输入了一个非数字值：

我们的代码不应该启动游戏，而应该向用户打印一个有用的错误信息，然后退出。

# 先编写测试

我们首先要确保游戏不会启动。

```
t.Run("it prints an error when a non numeric value is entered and does not start the game", func(t *testing.T) {
    stdout := &bytes.Buffer{}
    in := strings.NewReader("Pies\n")
    game := &GameSpy{}

    cli := poker.NewCLI(in, stdout, game)
    cli.PlayPoker()

    if game.StartCalled {
        t.Errorf("game should not have started")
    }
})
```

你需要在我们`GameSpy`中添加一个`StartCalled`字段，只有在`Start`被调用时才设置它。

# 尝试运行测试

```
===
RUN
TestCLI/it_prints_an_error_when_a_non_numeric_value_is_entered_
and_does_not_start_the_game
--- FAIL:
TestCLI/it_prints_an_error_when_a_non_numeric_value_is_entered_
and_does_not_start_the_game (0.00s)
    CLI_test.go:62: game should not have started
```

