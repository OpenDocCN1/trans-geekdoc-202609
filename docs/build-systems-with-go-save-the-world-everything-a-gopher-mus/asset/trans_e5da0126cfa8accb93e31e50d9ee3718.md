

## 示例 8.13: 使用字段标签自定义编码的 Marshal 函数（延续 8.12）。

```go
type User struct {
	UserID   string `pretty:"upper"`
	Email    string `pretty:"lower"`
	password string `pretty:"lower"`
}

type Record struct {
	Name    string `pretty:"lower" json:"name"`
	Surname string `pretty:"upper" json:"surname"`
	Age     int    `pretty:"other" json:"age"`
}

func main() {
	u := User{"John", "John@Gmail.com", "admin"}
	marser, _ := Marshal(u)
	fmt.Println("pretty user", string(marser))
	r := Record{"John", "Johnson", 33}
	marRec, _ := Marshal(r)
	fmt.Println("pretty rec", string(marRec))
	jsonRec, _ := json.Marshal(marRec)
	fmt.Println("json rec", string(jsonRec))
}
```

pretty user (UserID:JOHN, Email:john@gmail.com)
pretty rec (Name:John, Surname: JOHNSON)
json rec("name":"John", "surname":"Johnson", "age":33")

## 8.6 总结

在本章中，我们探索了 Go 中提供的不同编码格式。特别是，我们探索了 CSV、JSON、XML 和 YAML。marshal/unmarshal 方法的简单性加上字段标签（fields tagging）的使用，使得定义如何将结构转换为不同的格式成为可能。最后，我们展示了一个允许使用字段标签定义自定义编码的用例。

## 第 9 章
HTTP

自从 Tim Berners Lee 提出万维网的想法以来，HTTP 一一直是它的基础。深入理解 HTTP 是交换数据、操作 API 或爬取网页的基础。本章详细介绍了 Go 提供的工具，提供了必要元素来管理 HTTP 结构，如请求、cookie 或标头（headers）。特别是，我们探索了 net/http 包。本章假设你已经熟悉 HTTP 及其工作原理。

## 9.1 请求 (REQUESTS)

HTTP 请求是 HTTP 服务器根据客户端-服务器模型在给定的 URL 上执行的操作。Go 通过 `Get`、`Post` 和 `PostForm` 函数简化了 HTTP 请求的发送。只需调用这些函数即可发送 HTTP 请求。

## 9.1 GET

发送 GET 请求的最简单方法是使用 `http.Get` 函数。该函数返回一个填充了 `error y` 的 `http.Response` 类型。正如 HTTP 协议中定义的，响应包含一个 `Header` 类型和一个被编码为 `Reader` 类型的正文。

示例 9.1：GET 请求。

```go
package main

import (
	"bufio"
	"fmt"
	"net/http"
)

func main() {
	resp, err := http.Get("https://httpbin.org/get")
	if err != nil {
		panic(err)
	}

	fmt.Println(resp.Status)
	fmt.Println(resp.Header["Content-Type"])

	defer resp.Body.Close()
	buf := bufio.NewScanner(resp.Body)

	for buf.Scan() {
		fmt.Println(buf.Text())
	}
}
```

200 OK
[application/json]
{
  "args": {},
  "headers": {
    "Accept-Encoding": "zip",
    "Host": "httpbin.org",
    "User-Agent": "Go-http-client/2.0",
    "X-Amzn-Trace-Id": "root=1-6006ab94-3e51e2b50a91d3433bb59c1"
  },
  "origin": "111.111.111.111",
  "url": "https://httpbin.org/get"
}

示例 9.1 展示了如何向 https://httpbin.org/get 发送 GET 请求。当我们测试程序时，该 URL 将返回一个基础响应。响应状态是 RFC7231 定义的值之一（200 OK 如果一切正常）。header 字段是一个 map，因此我们可以使用 `resp.Header["Content-Type"]` 访问值。响应的正文是一个被消耗的 reader。如果你不熟悉 I/O 操作，这个 reader 的方便方法是使用 `bufio` 包中的任何函数。**在访问正文时不要关闭** reader（`resp.Body.Close()`）。

## 9.1.2 POST

发送 POST 遵循 GET 请求的相同原理。然而，我们需要发送 body并在 header 中设置 Content-type。再次，Go 有 `Post` 函数像示例 9.2 那样简化了这一操作。注意 POST body 预期是一个 `io.Reader`。在这个示例中，我们向 https://httpbin.org/post 发送 JSON body，它简单的返回我们发送的内容。注意 `http.Post` 的第二个参数指示 content-type。来自 `Response` 类型的字段可以如前所述。

示例 9.2：POST 请求

```go
package main

import (
	"bufio"
	"bytes"
	"fmt"
	"net/http"
)

func main() {
	bodyRequest := []byte(
	bufferBody := bytes.NewBuffer(bodyRequest)

	url := "https://httpbin.org/post"

	resp, err := http.Post(url, "application/json", bufferBody)
	if err != nil {
		panic(err)
	}
	defer resp.Body.Close()

	fmt.Println(resp.Status)
	bodyAnswer := bufio.NewScanner(resp.Body)
	for bodyAnswer.Scan() {
		fmt.Println(bodyAnswer.Text())
	}
}
```

```json
200 OK
{
  "args": [],
  "data": {"user": "john", "email": "john@gmail.com"},
  "files": [],
  "headers": {
    "Accept-Encoding": "zip",
    "Content-Length": "41",
    "Content-Type": "application/json",
    "Host": "httpbin.org",
    "User-Agent": "Go-http-client/2.0",
    "X-Trace-Id": "Root-1-606b0b32-6be58a13751bc0379bee0b"
  },
  "json": {
    "email": "john@gmail.com",
    "user": "john"
  },
  "origin": "111.111.111.111",
  "url": "https://httpbin.org/post"
}
```

http.Post 是通用的并接受任何 content-type。对于那些使用 application/x-www-form-urlencoded 的 post 方法，PostForm 函数会获取 content-type 规范并将 body 值直接允许 url-encoded 格式。

示例 9.3 展示了如何向 https://httpbin.org/post 发送 POST 请求。

```go
package main

import (
	"bufio"
	"fmt"
	"net/http"
	"net/url"
)

func main() {
	target := "https://httpbin.org/post"
	data := url.Values{}
	data.Set("user", "john")
	data.Set("email", "john@gmail.com")

	resp, err := http.PostForm(target, data)
	if err != nil {
		panic(err)
	}
	defer resp.Body.Close()

	fmt.Println(resp.Status)
	bodyAnswer := bufio.NewScanner(resp.Body)
	for bodyAnswer.Scan() {
		fmt.Println(bodyAnswer.Text())
	}
}
```

```json
200 OK
{
  "args": {},
  "data": "email=john@gmail.com&user=john",
  "files": [],
  "headers": {
    "Accept-Encoding": "zip",
    "Content-Length": "33",
    "Content-Type": "application/x-www-form-urlencoded",
    "Host": "httpbin.org",
    "User-Agent": "Go-http-client/2.0",
    "X-Amzn-Trace-Id": "root=1-6006ab94-3e51e2b50a91d3433bb59c1"
  },
  "origin": "111.111.111.111",
  "url": "https://httpbin.org/post"
}
```

## 9.1.3 标头（Headers）、客户端和其他方法

我们已经提到最常见的方法是 GET 和 POST。然而，还有更多方法，如 DELETE、UPDATE。此外，headers 包含与服务器交互所需的宝贵字段。

