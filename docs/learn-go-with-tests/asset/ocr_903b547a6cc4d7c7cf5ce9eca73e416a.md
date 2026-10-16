```
```go
request := httptest.NewRequest(http.MethodGet, "/", nil)

cancellingCtx, cancel := context.WithCancel(request.Context(
time.AfterFunc(5*time.Millisecond, cancel)
request = request.WithContext(cancellingCtx)

response := &SpyResponseWriter{}

svr.ServeHTTP(response, request)

if response.written {
    t.Error("a response should not have been written")
}
})
```
```

# Try to run the test

```
```
=== RUN   TestServer
===
RUN
TestServer/tells_store_to_cancel_work_if_request_is_cancelled
--- FAIL: TestServer (0.01s)
---
FAIL:
TestServer/tells_store_to_cancel_work_if_request_is_cancelled
(0.01s)
    context_test.go:47: a response should not have been written
```
```

# Write enough code to make it pass

```
```go
func Server(store Store) http.HandlerFunc {
    return func(w http.ResponseWriter, r *http.Request) {
        data, err := store.Fetch(r.Context())

        if err != nil {
            return // todo: log error however you like
        }
    }
}
```
```