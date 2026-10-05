

# 请求和响应的流程

为了更好地理解流程，我们来看一个来自我们应用的真实示例，涉及检索图书详情：

## 客户端请求

* 一个用户想要查看一本名为 "Learning Go." 的图书的详情。
* 客户端发送一个 GET 请求到 `http://gitforgits.com/books/123`，其中 "123" 是图书 ID。
* 请求如下：
  * Method: `GET`
  * URL: `/books/123`
  * Headers: `Accept: application/json`

## 服务器处理

* Go 服务器的路由器 `http.ServeMux` 将路径 `/books/123` 匹配到特定的处理器函数。
* 处理器函数解析 URL 以提取图书 ID。
* 它查询数据库获取图书 ID，检索图书详情，并准备 JSON 响应。

## 服务器响应

假设图书被找到，服务器构造一个 HTTP 响应：
* Status Line: `HTTP/1.1 200 OK`
* Headers: `Content-Type: application/json`
* Body:
```json
{"id": "123", "title": "Learning Go", "author": "Jane Doe", "description": "An introductory book on Go programming."}
```

## 客户端接收

客户端接收响应，解析 JSON 数据，并向用户显示图书详情。

## 请求和响应的处理

处理此流程涉及几个关键步骤：
* **解析 URL 路径和查询参数**: `http.Request` 对象提供诸如 `URL.Path` 和 `URL.Query()` 等方法，允许你分别提取 URL 的各部分和查询字符串。
* **读取请求体**: 对于 POST 和 PUT 请求，你通常需要读取请求体。这是通过 `r.Body` 完成的，它是一个 `io.ReadCloser`，可以像其他流一样读取：
```go
body, err := ioutil.ReadAll(r.Body)
if err != nil {
  http.Error(w, "Error reading body", http.StatusBadRequest)
  return
}
```
* **设置响应头和写入请求体**: 你使用 `http.ResponseWriter` 上的方法设置响应头：
```go
w.Header().Set("Content-Type", "application/json")
fmt.Fprint(w, jsonResponse)
```
这种对请求和响应架构的深入了解，结合来自 `gitforgits.com` 的实际示例，展示了 Web 服务器如何解释并响应客户端活动。要成功管理客户端-服务器连接并保证后端逻辑对不同客户端请求做出适当的处理和响应，了解此流程至关重要。

# 使用 http.ServeMux 进行路由的基础

路由是任何 Web 应用的基础方面，它将传入的 HTTP 请求导向应处理的正确代码。在我们项目 `gitforgits.com` 的上下文中，有效的路由确保查看图书、将图书添加到购物车或结账的请求都能到达可以执行这些操作的适当函数。

## 理解路由

路由是 Web 应用处理 HTTP 请求上的不同路径和方法的过程。当用户访问 URL 或与应用交互时，HTTP 请求的路径和方法需要与可以适当响应的特定代码匹配。例如，一个 URL 可能需要显示用户购物车，而另一个可能处理添加新图书的过程。

## http.ServeMux 简介

在 Go 中，处理路由最简单的方法之一是使用 `http.ServeMux`，它是一个多路复用器，将每个传入请求的 URL 与已注册路径列表进行匹配，并在找到匹配时调用该路径的关联处理器。`http.ServeMux` 是 `net/http` 包的一部分，可以用于创建新的多路复用器实例或通过直接调用包中的函数来利用默认多路复用器。

### http.ServeMux 的特性

* **模式匹配**: `http.ServeMux` 将请求的 URL 与已注册模式列表进行匹配并执行最具体的匹配模式的处理器。
* **干净的 URL 模式**: 它确保 URL 模式定义良好，可以匹配确切的标记或前缀。
* **方法被忽略**: 多路复用器默认不会对不同方法进行不同处理；它纯粹基于路径匹配。

## 示例程序：使用 http.ServeMux 进行路由

我们将编写一个简单的 Go 程序，使用 `http.ServeMux` 为我们的应用 `gitforgits.com` 路由不同端点。
```go
package main
import (
  "fmt"
  "net/http"
)
func mainHandler(w http.ResponseWriter, r *http.Request) {
  fmt.Fprintf(w, "Welcome to gitforgits.com!")
}
func booksHandler(w http.ResponseWriter, r *http.Request) {
  fmt.Fprintf(w, "Here are some books to browse.")
}
func orderHandler(w http.ResponseWriter, r *http.Request) {
  fmt.Fprintf(w, "Here's your order summary.")
}
func main() {
  mux := http.NewServeMux()
  // Registering handlers
  mux.HandleFunc("/", mainHandler)
  mux.HandleFunc("/books", booksHandler)
  mux.HandleFunc("/order", orderHandler)
  // Starting the server
  fmt.Println("Server starting on port 8080...")
  if err := http.ListenAndServe(":8080", mux); err != nil {
    fmt.Println("Error starting server: ", err)
  }
}
```
在上面的示例中：
* 创建了一个新的 `ServeMux` 实例。
* 定义了三个处理器：一个用于根路径 `/`，一个用于 `/books`，一个用于 `/order`。
* 每个处理器函数输出与路由对应的简单消息。
* `HandleFunc` 方法将处理器与特定路径注册。
* `http.ListenAndServe` 使用定义的 `ServeMux` 作为处理器启动 HTTP 服务器，监听端口 8080。

当服务器接收到 HTTP 请求时：
* `ServeMux` 检查请求 URL 与已注册模式列表。
* 它为最接近匹配的模式选择处理器。例如，如果服务器接收到对 `/books` 的请求，它将调用 `booksHandler`。
* 如果没有模式匹配，`ServeMux` 发送 HTTP 404 响应。

学习如何使用 `http.ServeMux` 进行路由是开发后端的一个基本但简单的方面。它帮助程序员以合理的方式组织服务器的 API，以便正确的组件可以处理正确类型的请求。随着 `gitforgits.com` 等程序的不断变化，这种 Web 开发的基本原则对于保持代码组织和高效变得更加重要。

