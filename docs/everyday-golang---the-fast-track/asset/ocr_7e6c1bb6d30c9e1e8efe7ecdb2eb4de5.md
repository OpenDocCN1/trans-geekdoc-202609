# The Prometheus Collector interface

The Collector interface is important in Prometheus for when you want to extend the metrics or labels that are being exported from your application. I tend to think it works better for when the data is coming from a third party API or remote endpoint like a database or the Kubernetes API server.

I tend to implement a collector as a new type. This code is adapted from the OpenFaaS gateway which is used in production by every installation.

```
type Exporter struct {
}

func NewExporter() *Exporter {
    return &Exporter{
    }
}
```

```
// Describe is to describe the metrics for Prometheus
func (e *Exporter) Describe(ch chan<- *prometheus.Desc) {

}
```

```
// Collect exports the values for each metric to Prometheus
func (e *Exporter) Collect(ch chan<- prometheus.Metric) {

}
```

The two important methods are “Describe” - which lets Prometheus know what metrics are being exported and “Collect” - which is where the actual data is exported. These functions are invoked asynchronously by Prometheus, and you don’t need to invoke them yourself.

You just need to register the instance of the Exporter.

```
e := NewExporter()
prometheus.MustRegister(e)
```

At that point, the Prometheus Go SDK will call Describe followed by Collect each time it’s scraped from the Prometheus server.

So what does it look like to populate these methods with code?

I’ll redact the example so that it only shows one of the fields which is how many replicas exist in Kubernetes for each of the OpenFaaS functions. The various label values for function_name will be reset and then populated dynamically every time the Collect code runs.

We’ll also write a fake API that returns how many replicas of each function we have in the OpenFaaS cluster. We’ll start off with no data, then we’ll add some, see it showing up in the metrics, then remove it and see that it’s removed and no longer tracked or exported, showing how useful the Collector interface is for dynamic data.

api.go:

package main

```
func newAPIQuery() *APIQuery {
    return &APIQuery{
        Response: make(map[string]int64),
    }
}
```

```
type APIQuery struct {
```