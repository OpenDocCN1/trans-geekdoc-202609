```
```go
//CLI.go
type CLI struct {
    playerStore PlayerStore
    in          *bufio.Scanner
}

func NewCLI(store PlayerStore, in io.Reader) *CLI {
    return &CLI{
        playerStore: store,
        in:          bufio.NewScanner(in),
    }
}
```
```

By doing this, we can then simplify and refactor our reading code

```
```go
//CLI.go
func (cli *CLI) PlayPoker() {
    userInput := cli.readLine()
    cli.playerStore.RecordWin(extractWinner(userInput))
}

func extractWinner(userInput string) string {
    return strings.Replace(userInput, " wins", "", 1)
}

func (cli *CLI) readLine() string {
    cli.in.Scan()
    return cli.in.Text()
}
```
```

Change the test to use the constructor instead and we should be back to the tests passing.

Finally, we can go back to our new main.go and use the constructor we just made

```
```go
//cmd/cli/main.go
game := poker.NewCLI(store, os.Stdin)
```
```

Try and run it, type "Bob wins".