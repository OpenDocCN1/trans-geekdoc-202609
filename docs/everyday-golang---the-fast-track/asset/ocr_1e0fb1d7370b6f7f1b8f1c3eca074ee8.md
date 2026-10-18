```
```go
Response map[string]int64
}

func (a *APIQuery) Register(name string, replicas int64) {
	a.Response[name] = replicas
}

func (a *APIQuery) Remove(name string) {
	delete(a.Response, name)
}

func (a *APIQuery) QueryFunctions() map[string]int64 {
	return a.Response
}
```
```

The API has a map which we will modify through HTTP requests to the /register and /remove endpoints, passing in a query string for the function name and / or replica count. Normally, if this were production code, we’d also want to use a locking mechanism to make sure we have safe concurrent access to the map.

exporter.go:

```
```go
package main

import (
	"github.com/prometheus/client_golang/prometheus"
)

type Exporter struct {
	ServiceReplicasGauge *prometheus.GaugeVec
	api                  *APIQuery
}

func NewExporter(api *APIQuery) *Exporter {
	return &Exporter{
		api: api,
		ServiceReplicasGauge: prometheus.NewGaugeVec(
			prometheus.GaugeOpts{
				Namespace: "gateway",
				Name:      "service_count",
				Help:      "Current count of replicas for function",
			},
			[]string{"function_name"},
		),
	}
}

// Describe is to describe the metrics for Prometheus
func (e *Exporter) Describe(ch chan<- *prometheus.Desc) {
	e.ServiceReplicasGauge.Describe(ch)
}

// Collect exports the values for each metric to Prometheus
func (e *Exporter) Collect(ch chan<- prometheus.Metric) {
	e.ServiceReplicasGauge.Reset()

	for serviceName, replicas := range e.api.QueryFunctions() {
```
```