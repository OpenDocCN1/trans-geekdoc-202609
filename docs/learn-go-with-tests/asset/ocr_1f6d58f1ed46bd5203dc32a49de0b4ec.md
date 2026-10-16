# Write enough code to make it pass

Update leagueHandler

```
//server.go
func (p *PlayerServer) leagueHandler(w http.ResponseWriter, r *r
    w.Header().Set("content-type", "application/json")
    json.NewEncoder(w).Encode(p.store.GetLeague())
}
```

The test should pass.

# Refactor

Create a constant for "application/json" and use it in leagueHandler

```
//server.go
const jsonContentType = "application/json"

func (p *PlayerServer) leagueHandler(w http.ResponseWriter, r *r
    w.Header().Set("content-type", jsonContentType)
    json.NewEncoder(w).Encode(p.store.GetLeague())
}
```

Then add a helper for assertContentType.

```
//server_test.go
func assertContentType(t testing.TB, response *httptest.Response
    t.Helper()
    if response.Result().Header.Get("content-type") != want {
        t.Errorf("response did not have content-type of %s, got
    }
}
```

Use it in the test.