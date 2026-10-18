The rate of invocations on the promhttp_metric_handler_requests_total metric are being tracked for HTTP 200 status codes for the service job over a 1-minute window.

Remember that this is just the status code for the Prometheus endpoint itself, so it does not yet instrument any API calls that our service may have. There is value in this though, since it can also track leaking Goroutines which haven't been cleared up with a similar query:

```
rate(
    go_goroutines{
        job="service"
    }[1m]
)
```

Note the “job” is looking at the scrape endpoint for our HTTP server. If you want, you can also review the amount of Goroutines Prometheus itself is running, since it instruments itself under the “prometheus” job.

# Tracking HTTP metrics for our microservice

We will now build a microservice that can generate a SHA256 hash of any input body, and will return a 200 status code for valid inputs. When a body isn't present and the HTTP method isn't POST, then the service will return a 400 error.

When complete, we'll be able to measure Rate Error Duration (RED) metrics for any HTTP middleware or handler you wish to instrument.

```
export GH_USERNAME="alexellis"
mkdir -p $GOPATH/src/github.com/$GH_USERNAME/custom-metrics/
cd $GOPATH/src/github.com/$GH_USERNAME/custom-metrics/
go mod init metrics

touch main.go
touch metrics.go
```

Create metrics.go:

```
package main

import (
    "net/http"

    "github.com/prometheus/client_golang/prometheus"
    "github.com/prometheus/client_golang/prometheus/promauto"
    "github.com/prometheus/client_golang/prometheus/promhttp"
)

type HttpMetrics struct {
    RequestsTotal           *prometheus.CounterVec
    RequestDurationHistogram *prometheus.HistogramVec
}

func NewHttpMetrics() HttpMetrics {
    return HttpMetrics{
        RequestsTotal: promauto.NewCounterVec(prometheus.CounterOpts{
            Subsystem: "http",
            Name:      "requests_total",
            Help:      "total HTTP requests processed",
        }, []string{"code", "method"}),
        RequestDurationHistogram: promauto.NewHistogramVec(prometheus.HistogramOpts{
```