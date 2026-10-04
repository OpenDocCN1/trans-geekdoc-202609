# Figure 15.1: Summary of elements in a gRPC deployment.

Observe in the Figure that clients implemented in different languages (Go and Python) can call rpc functions running in any server independently of the employed language (C++ in the example) as they share the same definition of methods and services.

gRPC differentiates between synchronous and asynchronous methods. A synchronous method blocks the execution until a response or an error is received. On the other hand, an asynchronous method immediately returns the execution without blocking the current thread.

A second category of methods are unary and streaming. A unary method (or if it is asynchronous) for a response. gRPC is built on top of HTTP/2 enables it to work with long-lived connection and full-duplex communication. This permits gRPC to define streaming methods in the client side, server side, or both.

![](bbox=[0.118, 0.345, 0.15, 0.377])

Although gRPC defines synchronous and asynchronous methods, the last ones are not available for Go. This must be taken into consideration when implementing APIs using these kind of methods. For this reason, asynchronous methods are not detailed in this Chapter.

# 15.2 DEFINITION OF SERVICES

A Remote Procedure Call (RPC) can be seen as an extension of the available functions we can invoke in a local machine. These functions are defined by an IDL (Interface Definition Language) that is used to generate stubs following the instructions from the IDL. In this case, we define methods and services in a .proto file as we did in Chapter 14 for protocol buffers.

In gRPC, a service is composed of one or several RPCs. We can think of services as a mechanism to group RPCs that operate with similar entities. For example, a user management service can have several operations: get a user, register a new user, remove a user, etc. Example 15.1 shows the .proto file for a service to manage users. The service has only one RPC call getUser receives a UserRequest and returns a User message. We have only included one RPC call to the UserService for the sake of simplification, although services can have as many RPCs as needed.

# Example 15.1: Service definition using gRPC.

```
syntax = "proto3";

package user;

option go_package="github.com/juanmanuel-tirado/savetheorldwith/13_grpc/example_01/user";

message User {
  string user_id = 1;
  string email = 2;
}
```