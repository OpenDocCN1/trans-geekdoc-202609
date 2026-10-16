
```
assertStatus(t, response.Code, http.StatusOK)

got := getLeagueFromResponse(t, response.Body)
want := []Player{
    {"Pepper", 3},
}
assertLeague(t, got, want)
}
}
```

## Try to run the test

```
=== RUN   TestRecordingWinsAndRetrievingThem/get_league
--- FAIL: TestRecordingWinsAndRetrievingThem/get_league
(0.00s)
    server_integration_test.go:35: got [] want [{Pepper 3}]
```

## Write enough code to make it pass

InMemoryPlayerStore is returning nil when you call GetLeague() SO we'll need to fix that.

```
//in_memory_player_store.go
func (i *InMemoryPlayerStore) GetLeague() []Player {
    var league []Player
    for name, wins := range i.store {
        league = append(league, Player{name, wins})
    }
    return league
}
```

All we need to do is iterate over the map and convert each key/value to a Player.

The test should now pass.

## Wrapping up

We've continued to safely iterate on our program using TDD, making it support new endpoints in a maintainable way with a router and it can now return JSON for our consumers. In the next chapter, we will cover persisting the data and sorting our league.

## What we've covered:

- **Routing**. The standard library offers you an easy to use type to do routing. It fully embraces the `http.Handler` interface in that you assign routes to `Handler`s and the router itself is also a `Handler`. It does not have some features you might expect though such as path variables (e.g `/users/{id}`). You can easily parse this information yourself but you might want to consider looking at other routing libraries if it becomes a burden. Most of the popular ones stick to the standard library's philosophy of also implementing `http.Handler`.
- **Type embedding**. We touched a little on this technique but you can learn more about it from Effective Go. If there is one thing you should take away from this is that it can be extremely useful but *always.

Let's try DRYing this up into a function.

Create a new file called league.go and put this inside.

```
//league.go
func NewLeague(rdr io.Reader) ([]Player, error) {
	var league []Player
	err := json.NewDecoder(rdr).Decode(&league)
	if err != nil {
		err = fmt.Errorf("problem parsing league, %v", err)
	}
	return league, err
}
```

Call this in our implementation and in our test helper getLeagueFromResponse in server_test.go

```
//file_system_store.go
func (f *FileSystemPlayerStore) GetLeague() []Player {
	var league []Player
	err := json.NewDecoder(rdr).Decode(&league)
	if err != nil {
		err = fmt.Errorf("problem parsing league, %v", err)
	}
	return league, err
}
```
