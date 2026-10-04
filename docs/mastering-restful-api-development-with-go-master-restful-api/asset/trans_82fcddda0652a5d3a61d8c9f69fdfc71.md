

从核心来看，GraphQL 服务器由三个主要组件组成：模式、解析器以及服务器本身。模式定义了可以查询或变更的类型和字段，本质上勾勒出数据的结构。解析器是处理获取或修改模式中指定数据的逻辑的函数。服务器负责接收 GraphQL 请求，执行适当的解析器，并将结果返回给客户端。

使用 GraphQL 服务器的一个关键优势在于，它允许客户端请求其所需数据的确切内容，减少了数据的过度获取和获取不足。这使得 GraphQL 成为现代 API 的高效且灵活的解决方案。

```go
package main

import (
    "encoding/json"
    "fmt"
    "io/ioutil" // Added for ioutil.ReadFile
    "log"
    "net/http" // Added for HTTP server functionality
    "github.com/graphql-go/graphql"
    "github.com/graphql-go/handler"
)

func main() {
    // Schema
    // Read the schema from the .graphql file
    schemaAsString, err := getSchema("./schema.graphql")
    if err != nil {
        log.Fatalf("Failed to read schema: %v", err) // Changed panic to log.Fatalf for better error handling
    }
    // Parse the read schema string into a GraphQL schema
    diaSchema := graphql.MustParseSchema(schemaAsString, &resolver.RootResolver{}, graphql.UseFieldResolvers())
    // Create a new HTTP multiplexer
    mux := http.NewServeMux()
    // Serve a simple page at the root URL
    mux.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
        _, err := w.Write(page)
        if err != nil {
            log.Printf("Failed to write response: %v", err) // Log instead of silently returning
            return
        }
    })

    // Handle GraphQL queries at /query using the defined schema
    mux.Handle("/query", handler.New(&handler.Config{Schema: diaSchema}))
    // Start the server
    listenPort := ":1111" // Default port if not set in environment
    log.Printf("Listening on %s", listenPort)
    log.Fatal(http.ListenAndServe(listenPort, mux)) // Utilize the listenPort variable
}
```

通过在终端中运行 `go run main.go` 执行此代码。然后，在浏览器中打开 `http://localhost:1111` 以访问配备 GraphQL 界面的页面。此交互式工具允许您直接在浏览器中执行 GraphQL 查询并查看响应，从而为您的 GraphQL API 提供高效的测试和调试流程。

![](images/Figure6.3.jpg)

图 6.3：GraphQL 浏览器

# 使用 PostMan 查询 GraphQL

使用 Postman 查询 GraphQL API 涉及多个步骤。以下是操作方法：

1. **打开 Postman：** 首先在计算机上启动 Postman 应用程序。
2. **创建新请求**：
   1. 点击 `New` 按钮或使用快捷键（macOS 的 `Cmd + N`，Windows/Linux 的 `Ctrl + N`）。
   2. 从选项中选择 `Request` 以创建新请求。
   3. 为请求命名并可选择将其保存到集合中以便更好地组织。
3. **设置请求**：
   1. 在请求选项卡中，将 HTTP 方法更改为 `POST`，因为 GraphQL 查询作为 POST 请求发送。
   2. 在地址栏中输入 GraphQL 端点的 URL。例如，如果您的 GraphQL 服务器在本地运行，URL 可能是 `http://localhost:1111/graphql`。
4. **配置标头**：
   1. 在地址栏下导航到 `Headers` 选项卡。
   2. 将 Content-Type 设置为 `application/json`。这告诉服务器期望 JSON 内容。
   3. 如果您的 GraphQL API 需要身份验证，也在此处添加适当的身份验证标头（例如，`Authorization`）。
5. **编写您的 GraphQL 查询**：
   1. 切换到 `Body` 选项卡并选择 `raw` 单选按钮。
   2. 从单选按钮右侧的下拉菜单中选择 `JSON`。
   3. 在提供的文本编辑器中，在 `query` 键下的 JSON 对象中输入您的 GraphQL 查询或变更。例如：

![](images/Figure6.4.jpg)

图 6.4：GraphQL Postman 浏览器

# 结论

本章对 GraphQL 及其对 API 开发的重要益处进行了全面介绍。我们探讨了 GraphQL 如何作为一种强大的查询语言，允许高效的数据检索，使客户端能够请求其所需的内容。通过了解 GraphQL 在单个请求中获取多个资源的能力及其结构化类型系统，开发人员可以创建比传统 REST API 更有效且可扩展的 API。

我们深入研究了在 Go 中实现 GraphQL API 的实践方面，利用流行的库并定义模式、类型、查询和变更。通过示例，我们了解了如何设置解析器、处理不同类型的操作以及构建响应以满足各种客户端应用程序的需求。

此外，我们还探讨了如何使用 GraphQL 和 Postman 等工具测试和与 GraphQL API 交互，使开发人员更容易调试和优化其查询。

总体而言，转向 GraphQL 代表了向更灵活、高效且对开发人员友好的 API 构建和消费的重大转变。通过拥抱 GraphQL 的原则并利用其功能，开发人员可以构建更强大且适应性强的 Web 服务，以满足现代应用程序不断变化的需求。

在下一章中，我们将深入探讨在架构中为微服务选择合适的通信协议这一关键决策。我们将比较和对比两种领先的协议：REST API，以其简单性和广泛采用而闻名，以及 gRPC，以其高性能和效率著称。讨论将包括每个协议的基本原则、其优势和潜在缺点。通过了解这些关键方面，您将获得必要的见解，以为您的微服务选择最合适的通信方法，确保系统各处的无缝交互和最佳性能。

# 关键术语

* **GraphQL**：一种用于 API 的查询语言，以及一个运行时，用于通过使用您为数据定义的类型系统来执行这些查询。
* **GraphQL Schema**：GraphQL API 的核心契约，定义类型、字段、查询、变更和订阅。
* **Query**：用于从服务器请求特定数据的 GraphQL 操作。
* **Mutation**：用于修改或更新服务器上数据的 GraphQL 操作。
* **Subscription**：GraphQL 的一项功能，通过允许客户端订阅更改来启用实时数据更新。
* **Type System**：GraphQL 中一种结构化的方法，定义数据模型并确保查询和响应中的类型安全。
* **Resolver**：根据查询从数据库或其他来源检索请求数据的函数。
* **Root Query Type**：GraphQL 模式中所有查询的入口点，定义可以获取的数据。
* **Root Mutation Type**：GraphQL 模式中所有变更的入口点，定义可以修改的数据。

# 第 7 章

# 微服务的 RESTful API 还是 gRPC

# 引言

在微服务架构的格局中，服务之间的有效通信至关重要。随着系统复杂性的增长，通信协议的选择变得至关重要。在本章中，我们将深入探讨两个主要竞争者：RESTful API 和 gRPC，检查其功能、性能、简单性、生态系统支持和最佳实践。

# 结构

