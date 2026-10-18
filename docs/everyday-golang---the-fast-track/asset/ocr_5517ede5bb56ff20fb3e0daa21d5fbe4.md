# Targets

![](bbox=[0.09, 0.07, 0.91, 0.3])

Figure 14.1: The scrape configuration

The metrics explorer (globe) button shows all metrics available for browsing.

![](bbox=[0.09, 0.39, 0.91, 0.73])

Figure 14.2: The metrics explorer

The table view can also be useful to view numbers

One of the most useful queries you can write is to check the rate of certain HTTP requests against your service. This query looks for 200 / OK responses, but you may want to pick out specific error codes to detect issues.

A graph showing the rate from the query

```
rate(
    promhttp_metric_handler_requests_total{
        code="200",
        job="service"
    }[1m]
)
```