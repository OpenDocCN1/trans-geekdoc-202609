```
t.Run("record chris win from user input", func(t *testing.T)
    in := strings.NewReader("Chris wins\n")
    playerStore := &StubPlayerStore{}

    cli := &CLI{playerStore, in}
    cli.PlayPoker()

    assertPlayerWin(t, playerStore, "Chris")
})

t.Run("record cleo win from user input", func(t *testing.T)
    in := strings.NewReader("Cleo wins\n")
    playerStore := &StubPlayerStore{}

    cli := &CLI{playerStore, in}
    cli.PlayPoker()

    assertPlayerWin(t, playerStore, "Cleo")
})
}
```

# Try to run the test

```
=== RUN   TestCLI
--- FAIL: TestCLI (0.00s)
=== RUN   TestCLI/record_chris_win_from_user_input
    --- PASS: TestCLI/record_chris_win_from_user_input (0.00s)
=== RUN   TestCLI/record_cleo_win_from_user_input
    --- FAIL: TestCLI/record_cleo_win_from_user_input (0.00s)
        CLI_test.go:27: did not store correct winner got
'Chris' want 'Cleo'
FAIL
```

# Write enough code to make it pass

We'll use a `bufio.Scanner` to read the input from the `io.Reader`.