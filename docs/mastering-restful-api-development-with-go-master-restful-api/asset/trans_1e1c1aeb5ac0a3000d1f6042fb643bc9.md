

## 状态码

| `OK` | 0 | 不是错误；在成功时返回。 |
| `CANCELLED` | 1 | 操作已被取消，通常由调用方取消。 |
| `UNKNOWN` | 2 | 表示未知错误。通常用于错误性质不明确或无法指定的场景。例如，如果从不同地址空间接收到的 Status 值属于当前空间中未知的错误域，则可能使用此错误。它也适用于 API 错误缺乏足够细节而被归类为未知的情形。 |
| `INVALID_ARGUMENT` | 3 | 此错误表示客户端提供了无效参数。需要注意与 `FAILED_PRECONDITION` 的区别。`INVALID_ARGUMENT` 用于表示固有有问题的参数，与系统状态无关。一个例子是格式不正确的文件名。 |
| `DEADLINE_EXCEEDED` | 4 | 在操作完成之前截止时间已过期。对于改变系统状态的操作，即使操作已成功完成，也可能返回此错误。例如，服务器的成功响应可能被延迟很久。 |
| `NOT_FOUND` | 5 | 某些请求实体（例如文件或目录）未找到。注意给服务器开发者：如果是整类用户被拒绝请求，例如渐进式功能发布或未记录的白名单，可使用 `NOT_FOUND`。如果某类用户中的部分用户被拒绝请求，例如基于用户的访问控制，则必须使用 `PERMISSION_DENIED`。 |
| `ALREADY_EXISTS` | 6 | 客户端尝试创建的实体（例如文件或目录）已存在。 |
| `PERMISSION_DENIED` | 7 | 此错误表示客户端尝试创建的实体，例如文件或目录，已存在。 |
| `RESOURCE_EXHAUSTED` | 8 | 这表示资源已被耗尽，这可能是由于达到每用户配额或整个文件系统空间用完所致。 |
| `FAILED_PRECONDITION` | 9 | 由于系统未处于执行操作所需的必要状态，操作被拒绝。例如，删除目录的请求被拒绝因为它不是空的，或尝试删除一个非目录实体。在实现服务时，以下准则可帮助在 `FAILED_PRECONDITION`、`ABORTED` 和 `UNAVAILABLE` 错误之间做出选择：如果客户端可以简单重试失败的同一调用，使用 `UNAVAILABLE`。如果客户端应在更全面的层级重试，使用 `ABORTED`。这例如适用于客户端的测试并设置操作失败的情况，表明客户端需要重新启动涉及读取、修改和写入数据的操作序列。使用 `FAILED_PRECONDITION` 如果客户端不应在系统状态得到具体解决之前尝试重试。例如，如果删除目录（`rmdir`）的请求失败因为目录包含文件，应返回 `FAILED_PRECONDITION`。客户端不应在目录清空文件之前重试操作。 |
| `ABORTED` | 10 | 操作被中止，通常由于并发问题，例如序列检查失败或事务被中止。有关在 `FAILED_PRECONDITION`、`ABORTED` 和 `UNAVAILABLE` 错误之间选择的指导，请参考上述准则。 |
| `OUT_OF_RANGE` | 11 | 当操作超出允许限制时触发此错误，例如尝试在文件末尾之后查找或读取。与表示永久问题的 `INVALID_ARGUMENT` 错误不同，`OUT_OF_RANGE` 错误意味着如果系统条件发生变化则可能可修复的问题。例如，在 32 位文件系统中，请求在 `[0,2^32-1]` 范围外的偏移量读取会产生 `INVALID_ARGUMENT` 错误。相比之下，请求读取超出文件当前大小会导致 `OUT_OF_RANGE` 错误。虽然 `FAILED_PRECONDITION` 和 `OUT_OF_RANGE` 错误通常重叠，但 `OUT_OF_RANGE` 更适用于更具体的情况。它对于指示数据集遍历的完成特别有帮助，因为遇到 `OUT_OF_RANGE` 错误表示已到达数据集的末尾。 |
| `UNIMPLEMENTED` | 12 | 操作未实现或在此服务中不受支持/未启用。 |
| `INTERNAL` | 13 | 内部错误是指底层系统的某些预期条件或不变量被违反的情况。此错误代码用于严重错误。 |
| `UNAVAILABLE` | 14 | 服务当前不可用，通常由于临时问题所致。通常可以通过在短暂延迟后重试请求，使用退避策略来解决。然而，需要注意的是，重试非幂等操作可能并不总是安全。 |
| `DATA_LOSS` | 15 | 这表示发生了不可恢复的数据丢失或损坏。 |
| `UNAUTHENTICATED` | 16 | 请求对操作没有有效的身份验证凭据。 |

### 表 5.1：状态码

### 状态消息

除了状态码之外，gRPC 还允许你发送状态消息。此消息可以提供有关错误的额外信息。

### 元数据

gRPC 允许在错误响应中发送自定义元数据（键值对），可用于提供额外的上下文或调试信息。

### 在 Go 中实现错误处理

在 Go 中实现 gRPC 服务时，错误通常使用 gRPC 库中的 status 包返回。

```go
import (
    "google.golang.org/grpc/codes"
    "google.golang.org/grpc/status"
)
```

```go
func (s *server) SomeRpcMethod(ctx context.Context, req *pb.SomeRequest) (*pb.SomeResponse, error) {
    if err := validateRequest(req); err != nil {
        return nil, status.Errorf(codes.InvalidArgument, "invalid request: %v", err)
    }
    // …
}
```

在此示例中，如果 `validateRequest` 返回错误，该方法将返回一个 gRPC 错误，其中包含 `InvalidArgument` 状态码和错误消息。

### 在客户端处理错误

在客户端，你可以检查 RPC 调用返回的错误，并使用 status 包提取状态码和消息。

```go
res, err := client.SomeRpcMethod(ctx, req)
if err != nil {
    if st, ok := status.FromError(err); ok {
        // 这里，st.Code() 是状态码，st.Message() 是错误消息
        fmt.Println("gRPC Error (code):", st.Code())
        fmt.Println("gRPC Error (message):", st.Message())
    } else {
        // 非 gRPC 错误
        fmt.Println("Non-gRPC error:", err)
    }
}
```

在 Go 中使用 gRPC 进行错误处理涉及使用 status 包返回和处理标准化的状态码和消息。此模型提供了一种在不同语言和平台间统一处理错误的方式，这是 gRPC 的优势之一。以这种方式正确处理错误可确保客户端能够理解并适当应对不同的错误条件，从而提高 gRPC 服务的健壮性和可靠性。

# 使用流式通信

