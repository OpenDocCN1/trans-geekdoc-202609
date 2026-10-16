```
t.Run("it records wins when POST", func(t *testing.T) {
    request := newPostWinRequest("Pepper")
    response := httptest.NewRecorder()

    server.ServeHTTP(response, request)

    assertStatus(t, response.Code, http.StatusAccepted)

    if len(store.winCalls) != 1 {
        t.Errorf("got %d calls to RecordWin want %d", len(st
    }
    })
}

func newPostWinRequest(name string) *http.Request {
    req, _ := http.NewRequest(http.MethodPost, fmt.Sprintf("/pla
    return req
}
```

# Try to run the test

```
./server_test.go:26:20: too few values in struct initializer
./server_test.go:65:20: too few values in struct initializer
```

# Write the minimal amount of code for the test to run and check the failing test output

We need to update our code where we create a StubPlayerStore as we've added a new field

```
//server_test.go
store := StubPlayerStore{
    map[string]int{},
    nil,
}
```