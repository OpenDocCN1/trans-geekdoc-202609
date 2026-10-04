
Finally, in the main function we start our gRPC and HTTP servers. Now gRPC clients can invoke procedures in port 5051 and HTTP clients can use port 8080. Now we can send HTTP requests to the indicated URLs using an HTTP client like curl.

```
>>> curl http://localhost:8080/v1/user/john
{"userId":"john","email":"john@gmail.com"}
>>> curl -d '{"user_id":"john","email":"john@gmail.com"}' http://localhost:8080/v1/user
{"userId":"john","email":"john@gmail.com"}
```

As you can observe, the addition of the gRPC gateway has not impacted the logic of our code. We have added a small piece of code and our server makes the same API using gRPC and HTTP/JSON.

# 15.7 INTERCEPTORS

Interceptors are the name for middleware components in gRPC. Operations such as user authentication, message tracing, request validation, etc. can be done with interceptors. Interceptors are allocated between the client and the server data flow like in Figure 15.6. When an interceptor is introduced into the data flow, this is executed for every message and has access to all the communication elements. An interceptor can manipulate message metadata, for adding example authentication headers on the client-side, or annotating additional information about IP addresses, client time zone, etc.

![](img/c7dcb4df7215ed1d3fb76d25373be6c7_218_0.png)

Figure 15.6: Data flow from client to server using interceptors.

Interceptors are thought to be used for common tasks and can be reused in several solutions. The gRPC-ecosystem has an available collection of interceptors to be used. However, the exact interceptor required for your problem may not be available. Fortunately, gRPC facilitates the implementation of four types of interceptors depending on if they are on the client or server-side and if they are designed for unary or streaming requests. In this section we explore and describe interceptors for unary requests. Streaming versions of these interceptors are very similar and can be easily implemented from unary versions.

## 15.7.1 Server interceptors

gRPC servers are instantiated with the `grpc.NewServer` function that receives arguments of type `ServerOption`. We can build types that implement `ServerOption` to work as interceptors. The following lines sketch the elements required to build a server interceptor:

```go
func MyServerInterceptor(...) (interface{}, error)

func withServerInterceptor() grpc.ServerOption {
  return grpc.UnaryInterceptor(MyServerInterceptor)
}

s := grpc.NewServer(withServerInterceptor())
```

To build a ServerOption, invoke the `UnaryInterceptor` function. This type is a function that must be implemented by our interceptor. The function signature is:

```go
type UnaryServerInterceptor func(ctx context.Context, req interface{}, info *grpc.ServerInfo, handler grpc.UnaryHandler) (interface{}, error)
```

where:
- ctx is the context.
- req contains the actual result.
- info contains server information and URI of the invoked method.
- handler is the handler of the request.

To illustrate how to implement a server interceptor, assume the initial implementation from Example 15.7. We want to enhance this server to only permit authenticated users.

### Example 15.7: Server interceptor (excerpt)

```go
func AuthServerInterceptor(
  ctx context.Context,
  req interface{},
  info *grpc.ServerInfo,
  handler grpc.UnaryHandler) (interface{}, error) {
  md, found := metadata.FromIncomingContext(ctx)
  if !found {
    return nil, status.Error(codes.InvalidArgument, "metadata not found")
  }
  password, found := md["password"]
  if !found {
    return nil, status.Error(codes.Unauthenticated, "password not found")
  }
  if password[0] != "go" {
    return nil, status.Error(codes.Unauthenticated, "password invalid")
  }

  h, err := handler(ctx, req)
  return h, err
}

func withServerInterceptor() grpc.ServerOption {
    return grpc.UnaryInterceptor(AuthServerInterceptor)
}

func main() {
    lis, err := net.Listen("tcp", "localhost:5051")
    if err != nil {
        panic(err)
    }
    s := grpc.NewServer(withServerInterceptor())
    pb.RegisterUserService(s, &Users{})
    if err := s.Serve(lis); err != nil {
        panic(err)
    }
}
```

The logic of our interceptor is contained in the `AuthServerInterceptor` function that implements the `UnaryServerInterceptor` type. The code looks into gRPC request metadata for the key/value pair "password". If it is found and equal to "go", we authenticate the user. In this case we simply return the result of the handler with the given context and original request. We could go further by removing the password from the metadata and adding another field with the authenticated user id, role, etc.

Additional code prepares the interceptor to be converted into a `ServerOption` as explained above. Every request will pass through our interceptor. The client must include the corresponding metadata, otherwise requests will not be authorized.

### Example 15.8: Client extended metadata (except)

```go
func main() {
    conn, err := grpc.Dial("localhost:5051", grpc.WithInsecure(), grpc.WithBlock())
    if err != nil {
        panic(err)
    }
    defer conn.Close()

    ctx, cancel := context.WithTimeout(context.Background(), time.Second)
    ctx = metadata.AppendToOutgoingContext(ctx, "password", "go")
    defer cancel()

    r, err := c.GetUser(ctx, &pb.UserRequest{UserId: "John"})
    if err != nil {
        panic(err)
    }
    fmt.Printf("Client received: %s\n", r.String())
}
```

Example 15.8 shows how the client puts additional metadata into the context before sending the request (line 22). For demonstration purposes and simplicity, the user was fixed. You can check that modifying the username returns an error from the server-side. Adding this metadata could be done using an interceptor on the client-side. Check the next section to understand how to write a client interceptor.

## 15.7.2 Client interceptors

Client interceptors work similarly to server interceptors. The three major elements to be filled are schematically shown below:

```go
func MyClientInterceptor(...) error

func withClientInterceptor() grpc.DialOption {
    return grpc.WithUnaryInterceptor(MyClientInterceptor)
}

conn, err := grpc.Dial(":50051", withClientInterceptor())
```

Our interceptor must implement the function signature defined by the `UnaryClientInterceptor` type:

```go
type UnaryClientInterceptor func(ctx context.Context, method string, req,
    reply interface{}, cc *ClientConn, invoker UnaryInvoker, opts ...CallOption) error
```

where:
- ctx is the context.
- method is the URI of the invoked method.
- req is the request.
- reply is the server response.
- cc is the connection.
- invoker is the function to be called.

We now plan to extend the gRPC call by adding to every request information about the client operating system and timezone. Example 15.9 defines the clientInterceptor with logging metadata.

### Example 15.9: Client interceptor with logging metadata (excerpt)

```go
func ClientLoggerInterceptor(
	ctx context.Context,
	method string,
	req interface{},
	reply interface{},
	cc *ClientConn,
	invoker UnaryInvoker,
	opts ...CallOption) error {
	os := runtime.GOOS
	zone, _ := time.Now().Zone()
	ctx = metadata.AppendToOutgoingContext(ctx, "os", os)
	ctx = metadata.AppendToOutgoingContext(ctx, "zone", zone)
	err := invoker(ctx, method, req, reply, cc, opts...)
	return err
}

func withClientInterceptor() grpc.DialOption {
	return grpc.WithUnaryInterceptor(ClientLoggerInterceptor)
}

func main() {
	conn, err := grpc.Dial("localhost:5051", grpc.WithInsecure(),
	grpc.WithBlock())
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
	fmt.Printf("Client received: %s\n", r.String())
}
```

For completeness, we have created a server interceptor that captures this metadata for logging purposes in Example 15.10. The steps to prepare this interceptor are similar to those described in the previous section.

### Example 15.10: Server interceptor consuming logging metadata (except)

```go
func RequestLoggerInterceptor(
	ctx context.Context,
	req interface{},
	info *grpc.ServerInfo,
	handler grpc.UnaryHandler) (interface{}, error) {
	md, ok := metadata.FromIncomingContext(ctx)
	if ok {
		os, _ := md["os"]
		zone, _ := md["zone"]
		fmt.Printf("Request from %s using %s\n", os, zone)
	}

	h, err := handler(ctx, req)
	return h, err
}
```
