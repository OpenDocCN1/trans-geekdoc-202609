# ASYNC API STYLES 173

```
GET /tasks/sse-event-stream
Accept: text/event-stream

task_created:
data: {"id": "12345"}
id: 12345

task_created:
data: {"id": "6789"}
id: 6789

<<Disconnected>>
GET /tasks/sse-event-stream
Accept: text/event-Id
Last-Event-Id: 6789
```

![](bbox=[0.196, 0.131, 0.864, 0.173])

**Figure 9.8** Using Server-Sent Events (SSE) to allow API servers to push events to the client over a long-lived connection. Connections may be resumed using the Last-Event-Id request header.

supported media types using content negotiation. Clients interested in SSE may do so by specifying the SSE media type instead of JSON or XML in the Accept request header.

Once connected, the server then pushes new events, separated by a newline. If the connection is lost for any reason, the client is able to start to receive new events. Clients may provide the Last-Event-Id HTTP header to recover any missed events since the last event ID seen by the client. This is useful for failure recovery.

The format for the data field may be text-based content, from simple data points to single-line JSON payloads. Multiple lines may be provided using multiple data-prefixed lines several cases:

+   - State notifications to a frontend application, such as a browser or mobile app, to keep a user interface in sync with the latest-server-side state
- Receiving business events over HTTP, without requiring access to an internal message broker or streaming platform such as RabbitMQ or Kafka
- Enabling clients to process data incrementally, rather than all at once, by streaming long-running queries or complex aggregations results as they become available