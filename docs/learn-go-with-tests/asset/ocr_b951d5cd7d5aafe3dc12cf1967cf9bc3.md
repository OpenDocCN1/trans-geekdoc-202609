```
--- FAIL: TestStoreWins (0.00s)
    --- FAIL: TestStoreWins/it_records_wins_when_POST (0.00s)
        server_test.go:80: got 0 calls to RecordWin want 1
```

# Write enough code to make it pass

As we're only asserting the number of calls rather than the specific values it makes our initial iteration a little smaller.

We need to update PlayerServer's idea of what a PlayerStore is by changing the interface if we're going to be able to call RecordWin.

```
//server.go
type PlayerStore interface {
    GetPlayerScore(name string) int
    RecordWin(name string)
}
```

By doing this main no longer compiles

```
./main.go:17:46:  cannot use InMemoryPlayerStore literal (type *InMemoryPlayerStore) as type PlayerStore in field value:
    *InMemoryPlayerStore does not implement PlayerStore
(missing RecordWin method)
```

The compiler tells us what's wrong. Let's update InMemoryPlayerStore to have that method.

```
//main.go
type InMemoryPlayerStore struct{}

func (i *InMemoryPlayerStore) RecordWin(name string) {}
```

Try and run the tests and we should be back to compiling code - but the test is still failing.

Now that PlayerStore has RecordWin we can call it within our PlayerServer