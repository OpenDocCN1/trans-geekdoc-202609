

- 根据不寻常的条件（例如 HTTP 请求标头）将请求路由到处理程序。

如果您的应用程序需要这些功能，则需要使用第三方路由器包。我推荐的有 httprouter、chi、flow 和 gorilla/mux，您可以在这篇博客文章中找到它们的比较以及关于使用哪一个的指导。

## 自定义响应

默认情况下，您的处理程序发送的每个响应都带有 HTTP 状态码 200 OK（这表示用户的请求已接收并成功处理），此外还有三个自动生成的系统标头：一个 Date 标头，以及响应正文的 Content-Length 和 Content-Type。例如：

```
$ curl -i localhost:4000/
HTTP/1.1 200 OK
Date: Wed, 18 Mar 2024 11:29:23 GMT
Content-Length: 21
Content-Type: text/plain; charset=utf-8

Hello from Snippetbox
```

在本章中，我们将深入探讨如何自定义处理程序发送的响应标头，还将介绍向用户发送纯文本响应的其他几种方式。

## HTTP 状态码

首先，让我们更新 snippetCreatePost 处理程序，使其发送 201 Created 状态码，而不是 200 OK。为此，您可以在处理程序中使用 w.WriteHeader() 方法，如下所示：

```
File: main.go

package main

...

func snippetCreatePost(w http.ResponseWriter, r *http.Request) {
    // Use the w.WriteHeader() method to send a 201 status code.
    w.WriteHeader(201)

    // Then w.Write() method to write the response body as normal.
    w.Write([]byte("Save a new snippet..."))
}

...
```

（是的，这有点傻，因为处理程序目前实际上还没有创建任何东西！但它很好地说明了设置自定义状态码的模式。）

虽然这个变化看起来很简单，但有几个细微差别我应该说明：

- 每个响应只能调用一次 w.WriteHeader()，并且在状态码写入后无法更改。如果您尝试第二次调用 w.WriteHeader()，Go 会记录一条警告消息。
- 如果您不显式调用 w.WriteHeader()，那么对 w.Write() 的第一次调用会自动向用户发送 200 状态码。因此，如果您想发送非 200 状态码，必须在任何对 w.Write() 的调用之前调用 w.WriteHeader()。

重启服务器，然后使用 curl 再次向 http://localhost:4000/snippet/create 发送 POST 请求。您应该看到 HTTP 响应现在带有类似于以下内容的 201 Created 状态码：

```
$ curl -i -d "" http://localhost:4000/snippet/create
HTTP/1.1 201 Created
Date: Wed, 18 Mar 2024 11:29:23 GMT
Content-Length: 21
Content-Type: text/plain; charset=utf-8

Save a new snippet...
```

## 状态码常量

net/http 包提供了 HTTP 状态码常量，我们可以使用这些常量，而不是亲自编写状态码数字。使用这些常量是良好做法，因为它有助于防止因拼写错误而导致的错误，并且还可以帮助使代码更清晰、自文档化——尤其是在处理不常用的状态码时。

让我们更新 snippetCreatePost 处理程序，使用常量 http.StatusCreated 代替整数 201，如下所示：

```
File: main.go

package main

...

func snippetCreatePost(w http.ResponseWriter, r *http.Request) {
	w.WriteHeader(http.StatusCreated)

	w.Write([]byte("Save a new snippet..."))
}

...
```

## 自定义标头

您还可以通过更改*响应标头映射*来自定义发送给用户的 HTTP 标头。您可能最希望做的事情是在映射中包含一个附加标头，您可以使用 `w.Header().Add()` 方法来实现。

为了演示这一点，让我们向 `home` 处理程序发送的响应添加一个 `Server: Go` 标头。如果您在跟随操作，请继续更新处理程序代码，如下所示：

```
File: main.go

package main

...

func home(w http.ResponseWriter, r *http.Request) {
	// Use the Header().Add() method to add a 'Server: Go' header to the
	// response header map. The first parameter is the header name, and
	// the second parameter is the header value.
	w.Header().Add("Server", "Go")

	w.Write([]byte("Hello from Snippetbox"))
}

...
```

> **重要：** 您必须确保响应标头映射中包含您想要的所有标头，*在* 调用 `w.WriteHeader()` 或 `w.Write()` *之前*。在调用 `w.WriteHeader()` 或 `w.Write()` 之后对响应标头映射所做的任何更改，都不会对用户收到的标头产生任何影响。

让我们尝试使用 curl 向 `http://localhost:4000/` 发送另一个请求。这一次，您应该看到响应现在包含一个新的 `Server: Go` 标头，如下所示：

```
$ curl -i http://localhost:4000

HTTP/1.1 200 OK
Server: Go
Date: Wed, 18 Mar 2024 11:29:23 GMT
Content-Length: 21
Content-Type: text/plain; charset=utf-8

Hello from Snippetbox
```

## 写入响应体

迄今为止，在本书中我们一直使用 w.Write() 向用户发送特定的 HTTP 响应体。虽然这是发送响应最简单、最基本的方式，但在实践中，将 http.ResponseWriter 值传递给另一个由其编写响应的函数要常见得多。

事实上，有很多函数可用于编写响应！

关键在于理解这一点……由于您处理程序中的 http.ResponseWriter 值具有一个 Write() 方法，它满足 io.Writer 接口。

如果您是 Go 新手，那么接口的概念可能有点令人困惑，我现在也不想太过纠结于此。但在实际层面上，这意味着任何您看到带有 io.Writer 参数的函数，您都可以传入 http.ResponseWriter 值，而任何被写入的内容随后都将作为 HTTP 响应的正文发送。

这意味着您可以使用标准库函数，例如 io.WriteString() 和 fmt.Fprint*() 家族（它们都接受 io.Writer 参数）来编写纯文本响应体。

```go
// Instead of this...
w.Write([]byte("Hello world"))

// You can do this...
io.WriteString(w, "Hello world")
fmt.Fprint(w, "Hello world")
```

让我们利用这一点，并更新 snippetView 处理程序中的代码，以使用 fmt.Fprintf() 函数。这将使我们能够在响应正文消息中插值通配符 id 值，并用一行代码写入响应，如下所示：

```go
File: main.go

package main

...

func snippetView(w http.ResponseWriter, r *http.Request) {
  id, err := strconv.Atoi(r.PathValue("id"))
  if err != nil || id < 1 {
    http.NotFound(w, r)
    return
  }

  fmt.Fprintf(w, "Display a specific snippet with ID %d...", id)
}

...
```

## 附加信息

## 内容嗅探

为了自动设置 `Content-Type` 标头，Go 使用 `http.DetectContentType()` 函数对响应正文进行内容嗅探。如果该函数无法猜测内容类型，Go 将回退到设置标头 `Content-Type: application/octet-stream`。

`http.DetectContentType()` 函数通常工作得相当不错，但 Web 开发者常遇到的一个问题是，它无法区分 JSON 和纯文本。因此，默认情况下，JSON 响应将使用 `Content-Type: text/plain; charset=utf-8` 标头发送。您可以通过在处理程序中手动设置正确的标头来防止这种情况发生，如下所示：

```
w.Header().Set("Content-Type", "application/json")
w.Write([]byte(`{"name":"Alex"}`))
```

## 操作标头映射

在本章中，我们使用 `w.Header().Add()` 向响应标头映射添加了一个新标头。但您还可以使用 `Set()`、`Del()`、`Get()` 和 `Values()` 方法来操作和读取标头映射。

```
// Set a new cache-control header. If an existing "Cache-Control" header exists
// it will be overwritten.
w.Header().Set("Cache-Control", "public, max-age=31536000")

// In contrast, the Add() method appends a new "Cache-Control" header and can
// be called multiple times.
w.Header().Add("Cache-Control", "public")
w.Header().Add("Cache-Control", "max-age=31536000")

// Delete all values for the "Cache-Control" header.
w.Header().Del("Cache-Control")

// Retrieve the first value for the "Cache-Control" header.
w.Header().Get("Cache-Control")

// Retrieve a slice of all values for the "Cache-Control" header.
w.Header().Values("Cache-Control")
```

## 标头规范化

当您在标头映射上使用 `Set()`、`Add()`、`Del()`、`Get()` 和 `Values()` 方法时，标头名称将始终使用 `textproto.CanonicalMIMEHeaderKey()` 函数进行规范化。这将首字母和任何字母

