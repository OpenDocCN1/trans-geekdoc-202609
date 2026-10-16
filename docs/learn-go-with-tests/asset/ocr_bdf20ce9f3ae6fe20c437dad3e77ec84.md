```
})

t.Run("get player score", func(t *testing.T) {
    database, cleanDatabase := createTempFile(t, `[ 
        {"Name": "Cleo", "Wins": 10},
        {"Name": "Chris", "Wins": 33}]`)
    defer cleanDatabase()

    store := FileSystemPlayerStore{database}

    got := store.GetPlayerScore("Chris")
    want := 33
    assertScoreEquals(t, got, want)
})
}
```

Run the tests and they should be passing! There were a fair amount of changes but now it feels like we have our interface definition complete and it should be very easy to add new tests from now.

# Let's get the first iteration of recording a win for an existing player

```
//file_system_store_test.go
t.Run("store wins for existing players", func(t *testing.T) {
    database, cleanDatabase := createTempFile(t, `[ 
        {"Name": "Cleo", "Wins": 10},
        {"Name": "Chris", "Wins": 33}]`)
    defer cleanDatabase()

    store := FileSystemPlayerStore{database}

    store.RecordWin("Chris")

    got := store.GetPlayerScore("Chris")
    want := 34
    assertScoreEquals(t, got, want)
})
```

# Try to run the test