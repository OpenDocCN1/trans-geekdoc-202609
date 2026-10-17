
[https://github.com/casbin/casbin#supported-models](#)

[\[29\]](#f_0045.xhtml#FNPTR-29)

: 

[https://en.wikipedia.org/wiki/Superuser](#)

[\[30\]](#f_0045.xhtml#FNPTR-30)

: 

[https://en.wikipedia.org/wiki/Nobody\_(username)](https://en.wikipedia.org/wiki/Nobody_\(username\))

Copyright © 2021, The Pragmatic Bookshelf. 

# Chapter 6  

Observe Your Systems  

Imagine waking up one day and noticing that the last hole in your belt doesn’t fit. You head to your scale and you see that you’ve gained a significant amount of weight overnight. You go on an emergency diet and fitness regimen. A couple of weeks later, you check the scales and see you gained even more weight somehow. What’s going on?

What you need is insight into what’s going on in your body. If our body had built-in observability, we’d have metrics on our body, like hormone levels that we could graph on a dashboard. If we could see a sudden imbalance in our hormone levels, with all things being equal, we could surmise that a hormonal imbalance must be the root cause. But without being able to see what had changed, you’d make many changes in search of the problem, each with their own effects.

We make our systems observable so we can we can ask questions that will give us insight into the system and debug unexpected problems. The keyword is unexpected—making our system observable means we can fix arbitrary problems that haven’t happened before. In this chapter, we’ll make our service observable so we understand what’s going on within it.

## Three Types of Telemetry Data

Observability is a measure of how well we understand our system’s internals—its behavior and state—from its external outputs. We use metrics, structured logs, and traces as the outputs to make our systems observable. While there are three types of telemetry data, each with its own use case we’ll talk about, it’ll often derive from the same events. For example, each time a web service handles a request, it may increment a “requests handled” metric, emit a log for the request, and make a trace.

### Metrics

Metrics measure numeric data over time, such as how many requests failed or how long each request took. Metrics like these help to define service-level indicators (SLI), objectives (SLO), and agreements (SLA). You’ll use metrics to report the health of your system, trigger internal alerts, and graph on dashboards to get an idea of how your system’s doing at a glance.

Because metrics are numerical data, you can gradually reduce resolution to reduce the storage requirements and time to query. For example, if we ran a book publishing company, we’d have metrics on each book purchase. To ship a customer’s books, we’d need to know the customer’s order, but after we’ve delivered the books and the return policy has passed, we don’t care about the order anymore. When we’re doing accounting or analysis on our business, that’s too much detail. Eventually we’d only need quarterly earnings to do our taxes, calculate year-over-year growth, and know if we can hire more editors and authors to expand our business.

There are three kinds of metrics:

Counters

: 

Counters track the number of times an event happened, such as the number of requests that failed or the sum of some fact of your system like the number of bytes processed.

: 

You’ll often take a counter and use it to get a rate: the number of times an event happened in an interval. Who cares about the total requests we’ve received other than to brag about it? What we care about is how many requests we’ve handled in the past second or minute—if that dropped significantly you’d want to check for latency in your system. You’d want to know when your request error rate spikes so you can see what’s wrong and fix it.

Histograms

: 

Histograms show you a distribution of your data. You’ll mainly use histograms for measuring the percentiles of your request duration and sizes.

Gauges

: 

Gauges track the current value of something. You can replace that value entirely. Gauges are useful for saturation-type metrics, like a host’s disk usage percentage or the number of load balancers compared to your cloud provider’s limits.

You could measure just about anything, so what data should you measure? What metrics will provide worthy signals on your system? These are Google’s four golden signals^([\[31\]](#f_0050.xhtml#FOOTNOTE-31)) to measure:

*   Latency—the time it takes your service to process requests. If your latency spikes, you often need to scale your system vertically by changing to an instance with more memory, CPUs, or IOPS, or scale your system horizontally by adding more instances to your load balancer.

*   Traffic—the amount of demand on your service. For a typical web service, this could be requests processed per second. For an online video game or video streaming service, it could be the number of concurrent users. These metrics are good for bragging rights (hopefully), but more important, they can help give you an idea of the scale at which you’re working and when you’ve scaled to the point you need a new design.

*   Errors—your service’s request failure rate. Internal server errors are particularly important.

*   Saturation—a measure of your service’s capacity. For example, if your service persists data to disk, at your current ingress rate will you run out of hard drive space soon? If you have an in-memory store, how much memory is your service using compared to the memory available?

While most debugging stories begin with metrics—either through an alert or someone noticing abnormalities on the dashboard—you’ll go to your logs and traces to learn more details about the problem. Let’s take a look at those next.

### Structured Logs

Logs describe events in your system. You should log any event that gives you useful insight into your service. Logs should help us troubleshoot, audit, and profile so we can learn what went wrong and why, who ran what actions, and how long those actions took. For example, a gRPC service log could log this per RPC call:

| ​  || { |

| --- | --- |

| ​  || "request_id": "f47ac10b-58cc-0372-8567-0e02b2c3d479", |

| ​  || "level": "info", |

| ​  || "ts": 1600139560.3399575, |

| ​  || "caller": "zap/server_interceptors.go:67", |

| ​  || "msg": "finished streaming call with code OK", |

| ​  || "peer.address": "127.0.0.1:54304", |

| ​  || "grpc.start_time": "2020-09-14T22:12:40-05:00", |

| ​  || "system": "grpc", |

| ​  || "span.kind": "server", |

| ​  || "grpc.service": "log.v1.Log", |

| ​  || "grpc.method": "ConsumeStream", |

| ​  || "peer.address": "127.0.0.1:54304", |

| ​  || "grpc.code": "OK", |

| ​  || "grpc.time_ns": 197740 |

| ​  || } |

In this log we see when the caller called the method, the caller’s IP address, the service and method they called, if the call succeeded, and how long the request took. In distributed systems, the request ID is helpful for piecing together a complete picture of a request that’s handled by multiple services.

This gRPC log is a JSON formatted, structured log. A structured log is a set of name and value ordered pairs encoded in consistent schema and format that’s easily read by programs. Structured logs enable us to separate log capturing, transporting, persisting, and querying. For example, we could capture and transport our logs as protocol buffers and then re-encode them in the Parquet^([\[32\]](#f_0050.xhtml#FOOTNOTE-32)) format and persist them in your columnar database.

I recommend collecting your structured logs in an event streaming platform like Kafka to enable arbitrary processing and transporting of your logs. For example, you can connect Kafka with a database like BigQuery to query your logs while connecting Kafka with an object store like GCS to maintain historical copies.
