Remember embedding? This is an interface comprised of Reader and Seeker

```
type Seeker interface {
    Seek(offset int64, whence int) (int64, error)
}
```

This sounds good, can we change FileSystemPlayerStore to take this interface instead?

```
//file_system_store.go
type FileSystemPlayerStore struct {
    database io.ReadSeeker
}

func (f *FileSystemPlayerStore) GetLeague() []Player {
    f.database.Seek(0, 0)
    league, _ := NewLeague(f.database)
    return league
}
```

Try running the test, it now passes! Happily for us string.NewReader that we used in our test also implements ReadSeeker so we didn't have to make any other changes.

Next we'll implement GetPlayerScore.

# Write the test first

```
//file_system_store_test.go
t.Run("get player score", func(t *testing.T) {
    database := strings.NewReader(`[
        {"Name": "Cleo", "Wins": 10},
        {"Name": "Chris", "Wins": 33}]`)

    store := FileSystemPlayerStore{database}

    got := store.GetPlayerScore("Chris")
```