
- 1. Example 15.3 is a minimalist server implementation of UserService. The UserServer type must implement the UserServiceServer interface defined in the stub. You can find the interface definition in Example 15.2. Every RPC in the .proto file inside the UserService must have its corresponding method implemented by the server. Only if all the methods are implemented, the server type will be a valid server.

Unary RPC methods have similarly structured signatures:

```
func RPCName(ctx context.Context, req *Request) (*Response, error)
```

We have a count for the request (see Section 6.6) and an incoming request. The method returns an answer and an order. In our example, we print the incoming request and return a manually populated User type.

- 2. The complexity of a server varies depending on the task and the number of RPCs to be implemented. However, once the server is defined we have to expose it in a way that requests can be correctly served by our code. The gRPC server generates RegisterUserServiceServer that links the UserService with any incoming request to this service. This must be done with a gRPC server type (lines 25–26).

- 3. Finally, we can run the gRPC server in an endless loop waiting for incoming requests. s.Server method blocks the execution until the server is stopped or a panic occurs.

The server code can be compared with the implementation of HTTP functions seen in Chapter 9. Notice that this code requires third-party components that may not be available on your platform. You can use mod to ensure you have the required code (See Chapter 12).

## 15.4 CREATING CLIENTS

Creating a gRPC client requires fewer steps than running a server. We have to define the address of the target server as shown in Example 15.4. The UserServiceClient provides methods to call the RPC methods defined in the .proto. A UserServiceClient instance can be obtained with the NewUserServiceClient and a connection to the server. We create a connection with the gRPC.DialOption function returns a server address or none DialOption values. DialOption type sets the connection with the server. In the example, we use WithInsecure to indicate that there is no encryption and WithBlock to block the execution flow until the server is up. Further details about how to use DialOption are given in Section 15.7 when explaining interceptors.

Example 15.4: User service client.

```go
package main

import (
	"context"
	"fmt"
	pb "github.com/juanuel-tirado/savethetoworldwithgo/13_grpc/grpc/example_01/user"
	"google.golang.org/grpc"
	"time"
)

func main() {
	conn, err := grpc.Dial("localhost:50051", grpc.WithInsecure(), grpc.WithBlock())
	if err != nil {
		panic(err)
	}
	defer conn.Close()

	c := pb.NewUserServiceClient(conn)

	ctx, cancel := context.WithTimeout(context.Background(), time.Second)
	defer cancel()

	r, err := c.GetUser(ctx, &pb.UserRequest{UserId: "John"})
	if err != nil {
		panic(err)
	}
	fmt.Println("Client received: ", r.String())
}
```

Running the server and then the client code you should get the outputs below. Remember, that the server must be running before the client is executed. The server will keep running until the program is killed.

Client received: user_id:"John" email:john@gmail.com
Server received: user_id:"John"

## 15.5 STREAMING

HTTP/2 permits full-duplex communication between client and server. This makes it possible to establish a streaming channel between both ends. The channel can be reused to reduce the overhead and latency of networked operations in the channel negotiation process. gRPC leverages this HTTP/2 feature to offer procedures that receive or return data inside streams. Next, we explain how to work with streaming for servers and clients in one direction or bidirectional flows.

### 15.5.1 Server streaming

Consider the .proto example from 15.5. The rnd remote receives a request to receive n random numbers in the range between from and to values. These numbers are not returned in a single batch, instead they are returned using a stream. This can be particularly useful in scenarios where n is very large.

### Example 15.5: Definition of a server streaming method.

```proto
syntax = "proto3";
package numbers;

option go_package="github.com/juanmanuel-tirado/savetheworldwithwithgo/13_grpc/streaming/example_01/numbers";

message NumRequest {
  int64 i = 1;
  int64 to = 2;
  int64 n = 3;
}

message NumResponse {
  int64 i = 1;
  int64 remaining = 2;
}

service NumberService {
  rpc Rnd(NumRequest) returns (stream NumResponse);
}
```

The data flow for this scenario is depicted in Figure 15.2.

**Figure 15.2:** Client-server communication.

| NumRequest | NumResponse |
| :--- | :--- |
| i:0, to:100, n:5 | i:33, remaining:99 |
| | i:42, remaining:98 |
| | i:15, remaining:66 |
| | i:27, remaining:15 |

The server uses the stream to send responses to the client. In Example 15.6, the server generates random numbers for the given range. Note that the server implementation differs from the client. When finished, the server closes the channel by returning an EOF (End Of File).

### Example 15.6: Implementation of streaming on the server.

```go
package main

import (
	"errors"
	"fmt"
	"math/rand"
	"net"
	"time"

	pb "github.com/juanmanuel-tirado/savetheworldwithwithgo/13_grpc/streaming/example_01/numbers"
	"google.golang.org/grpc"
)

type NumberServer struct {
	pb.UnimplementedNumberServiceServer
}

func (s *NumberServer) Rnd(req *pb.NumRequest, stream pb.NumberService_RndServer) error {
	if req.N <= 0 {
		return errors.New("N must be greater than zero")
	}
	if req.To <= req.From {
		return errors.New("to must be greater than from")
	}
	done := make(chan bool)
	go func() {
		for counter := 0; counter < int(req.N); counter++ {
			i := int64(rand.Intn(int(req.To-req.From))) + req.From
			stream.Send(&pb.NumResponse{I: i, Remaining: int64(req.N) - int64(counter)})
			time.Sleep(time.Second)
		}
		done <- true
	}()
	<-done
	return nil
}

func main() {
	lis, err := net.Listen("tcp", ":50051")
	if err != nil {
		panic(err)
	}
	s := grpc.NewServer()
	pb.RegisterNumberServiceServer(s, &NumberServer{})
	if err := s.Serve(lis); err != nil {
		panic(err)
	}
}
```

On the other side, the client listens to incoming responses after sending the initial request. Example 15.7 shows how to consume data from this function until an error is found. An important aspect to consider is the utilization of contexts. The context declared when invoking the remote method (ctx in line 21) lives during all the stream. This means that the client with timelines expires will be closed. For the current example, the channel will be closed after 10 seconds. It remains as an exercise for the reader to extend the length of the requested range to check how the expiration of the context terminates the stream.

### Example 15.7: Implementation of a client consuming responses from a streaming server.

```go
package main

import (
	"context"
	"fmt"
	"io"
	"time"

	pb "github.com/juanuel-tirado/savetheworldwithwithgo/13_grpc/streaming/example_01/numbers"
	"google.golang.org/grpc"
)

func main() {
	conn, err := grpc.Dial("localhost:50051", grpc.WithInsecure(), grpc.WithBlock())
	if err != nil {
		panic(err)
	}
	defer conn.Close()

	c := pb.NewServiceClient(conn)

	ctx, cancel := context.WithTimeout(context.Background(), time.Second(10))
	defer cancel()

	stream, err := c.Rnd(ctx, &pb.NumRequest{N: 5, From: 0, To: 100})
	if err != nil {
		panic(err)
	}

	for {
		resp, err := stream.Recv()
		if err == io.EOF {
			break
		}
		if err != nil {
			panic(err)
		}
		fmt.Printf("Client received: %v\n", resp.String())
	}
}
```
