

```go
fmt.Println("Recovered:"
```

Recovered: teams:{key:"teamA" value:{users:{user_id:"John" email:"john@gmail.com"} users:{user_id:"Mary" email:"mary@gmail.com"}}} teams:{key:"teamB" value:{{}}}

## 14.9 总结

本章总结了如何使用 protocol buffers 来定义 Go 序列化类型，这些类型可以独立于平台和语言，在不同的解决方案之间进行交换。本章的示例涵盖了 protocol buffer 消息的定义、语法以及如何在 Go 中使用这些消息。在探索第 15 章节之前，需要理解这些概念。

## 第 15 章 GRPC

gRPC 是一种与语言和平台无关的远程调用（RPC）框架。通过 gRPC，我们可以编写服务的通用定义及其签名，然后创建相应的客户端和服务器端。这种抽象减少了开发开销，并有助于维护一个适用于多个平台的健康且不断演化的 API 生态系统。在本章中，我们将探索如何使用 gRPC 定义服务以及如何在 Go 中使用生成的存根（stubs），以及如何使用流（streaming）、转码（transcoding）和拦截器（interceptors）。

## 15.1 概念

图 15.1 展示了 gRPC 部署的组件。每个部署都需要定义两个基本部分：消息（messages）和服务（services）。在 gRPC 中，消息使用 protocol buffers（参见第 14 章）定义，通过设置通用的序列化框架在客户端和服务器之间发送信息。服务是 RPC 方法的集合，可以接收消息和或返回消息。

如图 15.1 所示，`protoc` 程序将服务定义翻译为支持的语言之一（C/C++、Java、Python、Go 等）的存根集合。这些存根实现了所有逻辑，以确保消息和服务的正确性。因此，开发者只需按照其签名定义每个暴露方法的行为即可。

```go
message User {
    string user_id = 1;
    string email = 2;
}
service UserService {
    rpc GetUser(UserRequest) returns (User);
}
```

![](img/c7dcb4df7215ed1d3fb76d25373be6c7_196_0.png)

### 图 15.1：gRPC 部署中的元素总结。

观察图中可见，用不同语言（Go 和 Python）实现的客户端可以调用运行在任何服务器上的 rpc 函数，而取决于所使用的语言（示例中的 C++），因为它们共享相同的方法和服务的定义。

gRPC 区分了同步方法和异步方法。同步方法会阻塞执行直到接收到响应或错误。另一方面，异步方法会立即返回执行，而不阻塞当前线程。

方法的第二类是单元（unary）和流式（streaming）。单元方法（如果是异步的）用于一个响应。gRPC 构建在 HTTP/2 之上，使其能够处理长连接和全双工通信。这允许 gRPC 在客户端、服务器端或两端都定义流式方法。

![](img/c7dcb4df7215ed1d3fb76d25373be6c7_197_0.png)

尽管 gRPC 定义了同步和异步方法，但 Go 并不支持异步方法。在使用此类方法实现 API 时，必须考虑到这一点。由于由于原因，本章未详细介绍异步方法。

## 15.2 服务定义

远程过程调用（RPC）可以看作是在本地机器上调用的可用函数的扩展。这些函数由 IDL（接口定义语言）定义，用于根据 IDL 的指令生成存根。在这种情况下，我们像在第 14 章中为 protocol buffers 那样，在 .proto 文件中定义方法和服务。

在 gRPC 中，一个服务由一个或多个 RPC 组成。我们可以将服务视为一种对操作相似实体的 RPC 进行分组的机制。例如，一个用户管理服务可以有多个操作：获取用户、注册新用户、删除用户等。示例 15.1 显示了管理用户的服务的 .proto 文件。该服务只有一个 RPC 调用 `getUser`，它接收一个 `UserRequest` 并返回一个 `User` 消息。为了简单起见，我们只在 `UserService` 中包含了一个 RPC 调用，尽管服务可以拥有任意数量的 RPC。

### 示例 15.1：使用 gRPC 定义服务。

```proto
syntax = "proto3";

package user;

option go_package="github.com/juanmanuel-tirado/savetheorldwith/13_grpc/example_01/user";

message User {
  string user_id = 1;
  string email = 2;
}

11 message UserRequest {
12   string user_id = 1;
13 }
14

15 service UserService {
16   rpc GetUser(UserRequest) returns (User);
17 }
```

```

我们已经定义了消息和服务。现在我们需要创建相应的存根以便在 Go 代码中使用这些服务和规范。为了这一点，我们需要 `protoc` 工具。请确保你已经安装了 `protoc` 工具（参见 14.1）。`protoc` 配合 gRPC 插件工作。

```bash
export GOMOD=on
go get google.golang.org/grpc
```

export PATH=$PATH:$(go env)/bin

proto
```

`--go_grpc_out` 参数指定了 go 存根的路径。执行后有两个文件：`user.pb.go` 和 `user_grpc.pb.go`。第一个包含了 .proto 文件的消息定义。第二个包含了 grpc 存根的摘要。

```go
type UserService interface {
    GetUser(context.Context, *UserRequest) (*User, error)
}

type userService struct {
    cc grpc.ClientInterface
}

func NewUserService(cc grpc.ClientInterface) UserServiceClient {
    return &userService{cc}
}

func (c *userService) GetUser(ctx context.Context, in *UserRequest) (*User, error) {
    //
}
```

我们可以看到 `protoc` 自动生成了表示指定服务的 Go 类型。这些代码现在可以使用。

## 15.3 创建服务器

一旦生成了 gRPC 服务器，我们就可以将其导入代码中。这些代码为我们提供了需要在 .proto 文件中实现的 Go 函数框架。注意，现在我们只定义了签名，而不是逻辑本身。这必须在服务器端完成。在服务器运行之前，我们可以考虑三个步骤：服务器实现、服务注册以及服务器等待接入请求。

### 示例 15.3：用户服务服务器。

```go
package main

import (
	"context"
	"fmt"
	"github.com/juanmanuel-tirado/savetheworldwithgo/13_grpc/grpc/example_01/user"
	"google.golang.org/grpc"
	"net"
)

type UserServiceServer struct {
	pb.UnimplementedUserServiceServer
}

func (u *UserServiceServer) GetUser(ctx context.Context, req *pb.UserRequest) (*pb.User, error) {
	fmt.Println("Server received:", req.String())
	return &pb.User{Id: "John", Email: "john@gmail.com"}, nil
}

func main() {
	lis, err := net.Listen("tcp", "localhost:50051")
	if err != nil {
		panic(err)
	}
	s := grpc.NewServer()
	pb.RegisterUserServiceServer(s, &UserServiceServer{})

	if err := s.Serve(lis); err != nil {
		panic(err)
	}
}
```

