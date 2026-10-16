
```
if !reflect.DeepEqual(got, wantedLeague) {
    t.Errorf("got %v want %v", got, wantedLeague)
}
})
}
```

## Try to run the test

```
./server_test.go:33:3: too few values in struct initializer
./server_test.go:70:3: too few values in struct initializer
```

## Write the minimal amount of code for the test to run and check the failing test output

You'll need to update the other tests as we have a new field in StubPlayerStore; set it to nil for the other tests.

Try running the tests again and you should get

```
=== RUN   TestLeague/it_returns_the_league_table_as_JSON
--- FAIL: TestLeague/it_returns_the_league_table_as_JSON
(0.00s)
    server_test.go:124: got [{Chris 20}] want [{Cleo 32}
{Chris 20} {Tiest 14}]
```

## Write enough code to make it pass

We know the data is in our StubPlayerStore and we've abstracted that away into an interface PlayerStore. We need to update this so anyone passing us in a PlayerStore can provide us with the data for leagues.

//server.go
type PlayerStore interface {
    GetPlayerScore(name string) int
    RecordWin(name string)
    GetLeague() []Player
}

Now we can update our handler code to call that rather than returning a hard-coded list. Delete our method getLeagueTable() and then update leagueHandler to call GetLeague().

//server.go
func (p *PlayerServer) leagueHandler(w http.ResponseWriter, r *r
    json.NewEncoder(w).Encode(p.store.GetLeague())
    w.WriteHeader(http.StatusOK)
}

Try and run the tests.

```
# github.com/quii/learn-go-with-tests/json-and-io/v4
./main.go:9:50:  cannot use NewInMemoryPlayerStore()  (type *InMemoryPlayerStore)  as  type  PlayerStore  in  argument  to NewPlayerServer:
    *InMemoryPlayerStore does not implement PlayerStore (missing GetLeague method)
./server_integration_test.go:11:27:  cannot use  store (type *InMemoryPlayerStore)  as  type  PlayerStore  in  argument  to NewPlayerServer:
    *InMemoryPlayerStore does not implement PlayerStore (missing GetLeague method)
./server_test.go:36:28:  cannot use  &store  (type *StubPlayerStore)  as  type  PlayerStore  in  argument  to NewPlayerServer:
    *StubPlayerStore does not implement PlayerStore (missing GetLeague method)
./server_test.go:74:28:  cannot use  &store  (type *StubPlayerStore)  as  type  PlayerStore  in  argument  to NewPlayerServer:
    *StubPlayerStore does not implement PlayerStore (missing GetLeague method)
./server_test.go:106:29:  cannot use  &store  (type *StubPlayerStore)  as  type  PlayerStore  in  argument  to NewPlayerServer:
```

*StubPlayerStore does not implement PlayerStore (missing GetLeague method)

The compiler is complaining because InMemoryPlayerStore and StubPlayerStore do not have the new method we added to our interface.

For StubPlayerStore it's pretty easy, just return the league field we added earlier.

```
```go
//server_test.go
func (s *StubPlayerStore) GetLeague() []Player {
    return s.league
}
```
```

Here's a reminder of how InMemoryStore is implemented.

```
```go
//in_memory_player_store.go
type InMemoryPlayerStore struct {
    store map[string]int
}
```
```

Whilst it would be pretty straightforward to implement GetLeague "properly" by iterating over the map remember we are just trying to write the minimal amount of code to make the tests pass.

So let's just get the compiler happy for now and live with the uncomfortable feeling of an incomplete implementation in our InMemoryStore.

```
```go
//in_memory_player_store.go
func (i *InMemoryPlayerStore) GetLeague() []Player {
    return nil
}
```
```

What this is really telling us is that later we're going to want to test this but let's park that for now.

Try and run the tests, the compiler should pass and the tests should be passing!

## Refactor

The test code does not convey our intent very well and has a lot of boilerplate we can refactor away.

//server_test.go
t.Run("it returns the league table as JSON", func(t *testing.T)
    wantedLeague := []Player{
    {"Cleo", 32},
    {"Chris", 20},
    {"Tiest", 14},
    }

    store := StubPlayerStore{nil, nil, wantedLeague}
    server := NewPlayerServer(&store)

    request := newLeagueRequest()
    response := httptest.NewRecorder()

    server.ServeHTTP(response, request)

    got := getLeagueFromResponse(t, response.Body)
    assertStatus(t, response.Code, http.StatusOK)
    assertLeague(t, got, wantedLeague)
})

## Here are the new helpers

//server_test.go
func getLeagueFromResponse(t testing.TB, body io.Reader) (league
    t.Helper()
    err := json.NewDecoder(body).Decode(&league)

    if err != nil {
        t.Fatalf("Unable to parse response from server %q into s
    }

    return
}

```
func assertLeague(t testing.TB, got, want []Player) {
    t.Helper()
    if !reflect.DeepEqual(got, want) {
        t.Errorf("got %v want %v", got, want)
    }
}

func newLeagueRequest() *http.Request {
    req, _ := http.NewRequest(http.MethodGet, "/league", nil)

    return req
}
```

One final thing we need to do for our server to work is make sure we return a content-type header in the response so machines can recognise we are returning JSON.

## Write the test first

Add this assertion to the existing test

//server_test.go
if response.Result().Header.Get("content-type") != "application/
    t.Errorf("response did not have content-type of application/
}

## Try to run the test

```
=== RUN   TestLeague/it_returns_the_league_table_as_JSON
--- FAIL: TestLeague/it_returns_the_league_table_as_JSON
(0.00s)
    server_test.go:124: response did not have content-type
of   application/json,   got   map[Content-Type:[text/plain;
charset=utf-8]]
```

## Write enough code to make it pass

Update leagueHandler

//server.go
func (p *PlayerServer) leagueHandler(w http.ResponseWriter, r *r
    w.Header().Set("content-type", "application/json")
    json.NewEncoder(w).Encode(p.store.GetLeague())
}

The test should pass.

## Refactor

Create a constant for "application/json" and use it in leagueHandler

//server.go
const jsonContentType = "application/json"

func (p *PlayerServer) leagueHandler(w http.ResponseWriter, r *r
    w.Header().Set("content-type", jsonContentType)
    json.NewEncoder(w).Encode(p.store.GetLeague())
}

Then add a helper for assertContentType.

//server_test.go
func assertContentType(t testing.TB, response *httptest.Response
    t.Helper()
    if response.Result().Header.Get("content-type") != want {
        t.Errorf("response did not have content-type of %s, got
    }
}

Use it in the test.

//server_test.go
assertContentType(t, response, jsonContentType)

Now that we have sorted out `PlayerServer` for now we can turn our attention to `InMemoryPlayerStore` because right now if we tried to demo this to the product owner `/league` will not work.

The quickest way for us to get some confidence is to add to our integration test, we can hit the new endpoint and check we get back the correct response from `/league`.

## Write the test first

We can use `t.Run` to break up this test a bit and we can reuse the helpers from our server tests - again showing the importance of refactoring tests.

```
```go
//server_integration_test.go
func TestRecordingWinsAndRetrievingThem(t *testing.T) {
    store := NewInMemoryPlayerStore()
    server := NewPlayerServer(store)
    player := "Pepper"

    server.ServeHTTP(httptest.NewRecorder(), newPostWinRequest(
    server.ServeHTTP(httptest.NewRecorder(), newPostWinRequest(
    server.ServeHTTP(httptest.NewRecorder(), newPostWinRequest(

    t.Run("get score", func(t *testing.T) {
        response := httptest.NewRecorder()
        server.ServeHTTP(response, newGetScoreRequest(player))
        assertStatus(t, response.Code, http.StatusOK)

        assertResponseBody(t, response.Body.String(), "3")
    })

    t.Run("get league", func(t *testing.T) {
        response := httptest.NewRecorder()
        server.ServeHTTP(response, newLeagueRequest()
```
