# Integration tests

Integration tests can be useful for testing that larger areas of your system work but you must bear in mind:

+   - They are harder to write
+   - When they fail, it can be difficult to know why (usually it's a bug within a component of the integration test) and so can be harder to fix
+   - They are sometimes slower to run (as they often are used with "real" components, like a database)

For that reason, it is recommended that you research *The Test Pyramid*.

# Write the test first

In the interest of brevity, I am going to show you the final refactored integration test.

```
```go
//server_integration_test.go
package main

import (
    "net/http"
    "net/http/httptest"
    "testing"
)

func TestRecordingWinsAndRetrievingThem(t *testing.T) {
    store := InMemoryPlayerStore{}
    server := PlayerServer{&store}
    player := "Pepper"

    server.ServeHTTP(httptest.NewRecorder(), newPostWinRequest(
    server.ServeHTTP(httptest.NewRecorder(), newPostWinRequest(
    server.ServeHTTP(httptest.NewRecorder(), newPostWinRequest(
```
```