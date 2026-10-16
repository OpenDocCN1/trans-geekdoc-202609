We need to address the scenario where a user puts a non numeric value when prompted for the number of players:

Our code should not start the game and it should print a handy error to the user and then exit.

# Write the test first

We'll start by making sure the game doesn't start

```
t.Run("it prints an error when a non numeric value is entered ar
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

You'll need to add to our GameSpy a field StartCalled which only gets set if Start is called

# Try to run the test

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