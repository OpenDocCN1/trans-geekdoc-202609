# 15.5.3 Bidirectional streaming

We have already mentioned that gRPC provides full-duplex communication using HTTP/2. This makes it possible to use bidirectional streaming between client and server. Bidirectional streaming may be particularly suitable for scenarios where data may arise on the fly or even to define your protocols on top of gRPC.

In Example 15.11, we define a chat service that sends back to the user data consumption stats. In a chat service, client and server are expected to send data asynchronously. The client can send text messages to the server at any moment. On the other side, the server periodically sends stats to the user with some periodicity that may vary. Observe the remote method SendTxt sets the argument and responds to the streams.

# Example 15.11: Definition of a bidirectional streaming method.

```
syntax = "proto3"
package numbers;

option go_package="https://github.com/juannanuel-tirado/savetheworldwithgo/13_grpc/streaming/example_03/chat";n
message ChatRequest {
  int64 id = 1;
  int64 to = 2;
  string txt = 3;
}

message StatsResponse {
  int64 total_char = 1;
}

service ChatService {
  rpc SendTxt(stream ChatRequest) returns (stream StatsResponse);
}
```

Figure 15.4 depicts this communication scenario. The client starts the communication by establishing a new stream with the server. Both ends listen to the stream for any incoming message. Finally, both the client or server can close the connection at any moment. In our case, it is the client who finishes the communication.