```
```go
"net"
"net/http"
"strings"
"sync"
"time"

"greenlight.alexedwards.net/internal/data"
"greenlight.alexedwards.net/internal/validator"

"golang.org/x/time/rate"
)
...

func (app *application) metrics(next http.Handler) http.Handler {
    // Initialize the new expvar variables when the middleware chain is first built.
    totalRequestsReceived := expvar.NewInt("total_requests_received")
    totalResponsesSent := expvar.NewInt("total_responses_sent")
    totalProcessingTimeMicroseconds :=
    expvar.NewInt("total_processing_time_us")

    // The following code will be run for every request...
    return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        // Record the time that we started to process the request.
        start := time.Now()

        // Use the Add() method to increment the number of requests received by 1.
        totalRequestsReceived.Add(1)

        // Call the next handler in the chain.
        next.ServeHTTP(w, r)

        // On the way back up the middleware chain, increment the number of responses
        // sent by 1.
        totalResponsesSent.Add(1)
```
```