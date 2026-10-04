

```go
func Middleware(next http.Handler) http.Handler {
	return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
	// 在调用下一个处理器之前执行某些操作
	next.ServeHTTP(w, r)
	// 在下一个处理器执行完成后执行某些操作
	})
}
// / ...
http.ListenAndServe(":8080", Middleware(Middleware(Handler)))
```

上面的代码总结了中间件处理器（middleware handler）的定义。该处理器接收另一个处理器，并必须使用相同的 `Request` 和 `ResponseWriter` 调用它。该处理器可以根据其逻辑，在调用下一个处理器之前修改这两个元素。为了将中间件应用于每个请求，我们将其与后续的处理器串联起来。由于中间件返回一个 `Handler`，我们可以串联多个中间件，直到最终按照预期的逻辑调用目标处理器。

9.9 为服务器实现了一个基础身份验证机制。基础身份验证基于 `Authorization: Basic <credential>` 请求头，其中 `credential` 是经过 base64 编码的字符串。`AuthMiddleware` 函数检查此头是否存在，如果匹配 `Open Sesame`，则解码并对请求进行授权。如果任何一步失败，中间件将把请求标记为未授权（错误 401）并返回。

## 9.9: 基础身份验证中间件处理器。

```go
1 package name
2
3 import (
4	"encoding/base64"
5	"net/http"
6	"strings"
7	"fmt"
8 \)
9
10 type MyHandler struct {
11
12 func (mh *MyHandler) ServeHTTP(w http.ResponseWriter, r *http.Request) {
13	w.WriteHeader(http.StatusOK)
14	w.Write([]byte("Perfect!!"))
15	return
16 }
17
18
19 func AuthMiddleware(next http.Handler) http.Handler {
20	return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
21	header := r.Header.Get("Authorization")
22	if header == "" {
23		w.WriteHeader(http.StatusUnauthorized)
24		return
25	}
26
27	authType := strings.Split(header," ")
```

```go
fmt.Println(authType)
if len(authType) == 2 || authType[0] != "Basic" {
	w.WriteHeader(http.StatusUnauthorized)
	return
}

creds,err := base64.StdEncoding.DecodeString(authType[1])
if err != nil {
	w.WriteHeader(http.StatusUnauthorized)
	return
}

if string(creds) == "Open Sesame" {
	next.ServeHTTP(w, r)
}
}
```

```go
func main() {
	targetHandler := MyHandler()
	panic(http.ListenAndServe(":8080", AuthMiddleware(targetHandler))))
}
```

```bash
>>> auth=$(echo -n "Open Sesame" | base64);
>>> echo auth
T3B0bElTZnhbWU=
>>> curl -w "%http_code" -H "Authorization: Basic $auth" http://localhost:8080/three
200
```

现在，请求在找到正确的授权头之前将未授权。为了获取 base64 编码，如果你使用类似 Unix 环境，可以使用下面的命令。

现在我们已经看到了如何定义中间件处理器，以及如何轻松地串联所有中间件。这是一个有趣的问题，因为我们可以期望处理多个处理器。9.10 定义了 `Middleware` 类型和 `ApplyMiddleware` 函数来帮助串联多个处理器。核心思想是使用 `AuthMiddleware(&targetHandler)` 来替换可以程序化执行的内容。在注册服务器处理器时，我们只需注册 `/three` 和 `/one`，应用一次或三次 `SimpleMiddleware`。这个中间件检查头并添加内容。响应中的中间件数量取决于处理请求的方式。

示例 9.10: 多个处理器的串联。

```go
package main

import "net/http"

type MyHandler struct{}

func (mh *MyHandler) ServeHTTP(w http.ResponseWriter, r *http.Request) {
	w.WriteHeader(http.StatusOK)
	w.Write([]byte("Perfect!!!"))
	return
}

type Middleware func(http.Handler) http.Handler

func ApplyMiddleware(h http.Handler, middleware ...Middleware) http.Handler {
	for _, next := range middleware {
		h = next(h)
	}
	return h
}

func SimpleMiddleware(next http.Handler) http.Handler {
	return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
		value := w.Header().Get("simple")
		if value == "" {
			value = "X"
		} else {
			value = value + "X"
		}
		w.Header().Set("simple", value)
		next.ServeHTTP(w, r)
	})
}

func main() {
	h := &MyHandler{}

	http.Handle("/three", ApplyMiddleware(http.HandlerFunc(h.ServeHTTP), SimpleMiddleware, SimpleMiddleware))

	http.Handle("/one", ApplyMiddleware(http.HandlerFunc(h.ServeHTTP), SimpleMiddleware))

	panic(http.ListenAndServe(":8080", nil))
}
```

使用 `curl` 我们可以看到 `/three` 返回 `Simple: XXX`，而 `/one` 返回 `Simple: X`。显然，这些中间件函数仅用于演示。然而，应用更真实或复杂的解决方案可以使用完全相同的想法。

>>> curl http://localhost:8080/three -i

```http
HTTP/1.1 200 OK
Simple: XXX
Date: Wed, 17 Feb 2021 20:40:55 GMT
Content-Length: 10
Content-Type: text/plain; charset=utf-8
```

```
Perfect!!!%
>>> curl http://localhost:8080/one -i
HTTP/1.1 200 OK
Simple: X
Date: Wed, 17 Feb 2021 16:50:01 GMT
Content-Length: 10
Content-Type: text/plain; charset=utf-8
```

Perfect!!!%
```

## 9.5 总结

HTTP 被广泛使用，不仅提供了检索 Web 内容的可能性，还提供了访问远程 API 的。本章展示了 Go 如何处理 HTTP 的主要元素，包括请求、响应、头部和 Cookie。额外的材料解释了中间件以及如何方便地定义复杂的管道来处理 HTTP 请求。

## 第 10 章 模板

当你阅读这些行时，有成千上万的报告、网页以及其他结构化非结构化数据集正在生成。其中许多共享一个共同模板，该模板从用户处提取信息并根据预定义的逻辑进行处理。例如，发送到你的账户以重置忘记密码的电子邮件总是相同的，除了包含你应该注意的小部分数据。

从实践角度来看，这些模板应该容易更改和修改，而不一定需要修改任何源代码。Go 提供了数据驱动模板来生成文本输出。这些模板通过将包含表示数据的结构应用于模板包来执行。本章探索了如何使用 `text/template` 和 `html/template` 包分别用于文本和 HTML 的模板。

### 10.1 使用结构体填充

`text/template` 包定义了生成文本模板的语法。我们的目标是用传入的数据填充空白。让我们考虑下面的字符串：

> 亲爱的 {{.Name}}
> 你已通过 ID {{.UserId}} 注册
> 电子邮箱 {{.Email}}

这定义了一个模板，预期由一个具有 `Name`、`UserId` 和 `Email` 字段的结构体填充。示例 10.1：使用结构体填充。

```go
package main

import (
	"os"
	"text/template"
)

type User struct {
	Name   string
	UserId string
	Email  string
}

const Msg = '亲爱的 {{.Name}}.
你已通过 ID {{.UserId}} 注册
电子邮箱 {{.Email}}'.
```

![](img/7cb4df215ed1d3fb76d2537be6c7.png)

```go
17 '
18
19 func main() {
20    u := User{"John", "John33", "john@gmail.com"}
21
22    t := template.Must(template.New("msg").Parse(Msg))
23    err := t.Execute(os.Stdout, u)
24    if err != nil {
25        panic(err)
26    }
27 }
```

模板通过 `New` 函数分配，该函数接收模板名称。`Parse` 方法分析模板字符串。如果模板解析失败，该方法会返回错误。`template.Must` 是一个包装器，如第22行所示有助于模板定义。最后，`Execute` 将模板应用于接口类型并将生成的输出写入 `io.Writer`。输出是我们填充了变量模板。

### 10.2 动作

模板允许根据数据值定义某些逻辑。10.2 根据性别更改输出。`{{if .Female}}Mrs.{{- else}}Mr. {{- end}}` 语句根据布尔字段打印不同的消息。

**示例 10.2：** 模板 if/else。

```go
package main

import (
	"os"
	"text/template"
)

type User struct {
	Name   string
	Female bool
}

const Msg = '{{if .Female}}Mrs.{{- else}}Mr. {{- end}} {{.Name}},
你的软件包已准备好。
谢谢。'.

func main() {
	u1 := User{"John", false}
	u2 := User{"Mary", true}

	t := template.Must(template.New("msg").Parse(Msg))
	t.Execute(os.Stdout, u1)
	t.Execute(os.Stdout, u2)
}
```

