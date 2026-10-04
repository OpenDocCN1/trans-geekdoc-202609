30 )

31 )

+   1. Example 15.3 is a minimalist server implementation of UserService. The UserServer type must implement the UserServiceServer interface defined in the stub. You can find the interface definition in Example 15.2. Every RPC in the .proto file inside the UserService must have its corresponding method implemented by the server. Only if all the methods are implemented, the server type will be a valid server.

Unary rpc methods have similarly structured signatures:

```
func RPCName(ctx context.Context, req *Request) (*Response, error)
```

We have a count for the request (see Section 6.6) and an incoming request. The method returns an answer and order. In our example, we print the incoming request and return a manually populated User type.

+   2. The complexity of a server varies depending on the task and the number of RPCs to be implemented. However, once the server is defined we have to expose it in a way that requests can be correctly served by our code. The gRPC server generates RegisterUserServiceServer that links the UserService with any incoming request to this service. This must be done with a gRPC server type (lines 25–26).
3. Finally, we can run the gRPC server in an endless loop waiting for incoming requests. s.Server method blocks the execution until the server is stopped or panic occurs.

The server code can be compared with the implementation of HTTP functions seen in Chapter 9. Notice that this code requires third-party components that may not be available on your platform. You can use mod to ensure you have the required code (See Chapter 12).

# 15.4 CREATING CLIENTS

Creating a gRPC client requires fewer steps than running a server. We have to define the address of the target server as shown in Example 15.4. The UserServiceClient provides methods to call the rpc methods defined in the .proto. A UserServiceClient instance can be obtained with the NewUserServiceClient and a connection to the server. We create a connection with the gRPC. DialOption function returns a server address or none DialOption values. DialOption type sets the connection with the server. In the example, we use WithInsecure to indicate that there is no encryption and WithBlock to block the execution flow until the server is up. Further details about how to use DialOption are given in Section 15.7 when explaining interceptors.

Example 15.4: User service client.

```
package main
2
3 import (
4    "context"
5    "fmt"
```