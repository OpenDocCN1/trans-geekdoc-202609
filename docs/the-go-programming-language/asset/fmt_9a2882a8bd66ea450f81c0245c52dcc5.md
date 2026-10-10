
# HTTP 服务器处理逻辑

```go
func (db database) ServeHTTP(w http.ResponseWriter, req *http.Request) {
    switch req.URL.Path {
    case "/list":
        for item, price := range db {
            fmt.Fprintf(w, "%s: %s\n", item, price)
        }
    case "/price":
        item := req.URL.Query().Get("item")
        price, ok := db[item]
        if !ok {
            w.WriteHeader(http.StatusNotFound) // 404
            fmt.Fprintf(w, "no such item: %q\n", item)
            return
        }
        fmt.Fprintf(w, "%s\n", price)
    default:
        w.WriteHeader(http.StatusNotFound) // 404
        fmt.Fprintf(w, "no such page: %s\n", req.URL)
    }
}
```

现在处理程序根据 URL 的路径组件 `req.URL.Path` 决定执行什么逻辑。如果处理程序无法识别该路径，它会通过调用 `w.WriteHeader(http.StatusNotFound)` 向客户端报告 HTTP 错误；这必须在向 `w` 写入任何文本之前完成。（顺便说一下，`http.ResponseWriter` 是另一个接口。它通过发送 HTTP 响应头的方法扩展了 `io.Writer`。）同样地，我们也可以使用 `http.Error` 实用函数：

```go
msg := fmt.Sprintf("no such page: %s\n", req.URL)
http.Error(w, msg, http.StatusNotFound) // 404
```

`/price` 的 case 调用 URL 的 `Query` 方法将 HTTP 请求参数解析为 map，或者更确切地说，是 `net/url` 包中类型为 `url.Values`（[§6.2.1](#ebook_split_054.html#id-urlvalues)）的 multimap。然后它查找第一个 `item` 参数并查找其价格。如果未找到该项，则报告错误。

以下是与新服务器的示例会话：

```bash
$ go build gopl.io/ch7/http2
$ go build gopl.io/ch1/fetch
$ ./http2 &
$ ./fetch http://localhost:8000/list
shoes: $50.00
socks: $5.00
$ ./fetch http://localhost:8000/price?item=socks
$5.00
$ ./fetch http://localhost:8000/price?item=shoes
$50.00
$ ./fetch http://localhost:8000/price?item=hat
no such item: "hat"
$ ./fetch http://localhost:8000/help
no such page: /help
```

显然我们可以继续向 `ServeHTTP` 添加 case，但在实际应用中，为每个 case 在单独的函数或方法中定义逻辑更为方便。此外，相关的 URL 可能需要相似的逻辑；例如，多个图像文件的 URL 可能具有 `/images/*.png` 的形式。出于这些原因，`net/http` 提供了 `ServeMux`（请求多路复用器）来简化 URL 和处理程序之间的关联。`ServeMux` 将一组 `http.Handler` 聚合为单个 `http.Handler`。我们再次看到，满足相同接口的不同类型是*可替换的*：Web 服务器可以将请求分派给任何 `http.Handler`，而不管其背后的具体类型是什么。

对于更复杂的应用程序，可以组合多个 `ServeMux` 来处理更复杂的分派需求。Go 没有类似于 Ruby 的 Rails 或 Python 的 Django 的规范 Web 框架。这并不是说此类框架不存在，而是 Go 标准库中的构建块足够灵活，以至于框架通常是不必要的。此外，虽然框架在项目的早期阶段很方便，但它们额外的复杂性可能会使长期维护变得更难。

在下面的程序中，我们创建了一个 `ServeMux` 并用它将 URL 与 `/list` 和 `/price` 操作的相应处理程序关联起来，这些操作已被拆分为单独的方法。然后我们在调用 `ListenAndServe` 时将 `ServeMux` 作为主处理程序。

```go
func main() {
    db := database{"shoes": 50, "socks": 5}
    mux := http.NewServeMux()
    mux.Handle("/list", http.HandlerFunc(db.list))
    mux.Handle("/price", http.HandlerFunc(db.price))
    log.Fatal(http.ListenAndServe("localhost:8000", mux))
}

type database map[string]dollars

func (db database) list(w http.ResponseWriter, req *http.Request) {
    for item, price := range db {
        fmt.Fprintf(w, "%s: %s\n", item, price)
    }
}

func (db database) price(w http.ResponseWriter, req *http.Request) {
    item := req.URL.Query().Get("item")
    price, ok := db[item]
    if !ok {
        w.WriteHeader(http.StatusNotFound) // 404
        fmt.Fprintf(w, "no such item: %q\n", item)
        return
    }
    fmt.Fprintf(w, "%s\n", price)
}
```

让我们关注一下注册处理程序的两个 `mux.Handle` 调用。在第一个调用中，`db.list` 是一个方法值（[§6.4](#ebook_split_056.html#id-methodvaluesandexpressions)），即类型为

```go
func(w http.ResponseWriter, req *http.Request)
```

的值，调用时会使用接收者值 `db` 调用 `database.list` 方法。因此 `db.list` 是一个实现了类似处理程序行为的函数，但由于它没有方法，所以不满足 `http.Handler` 接口，不能直接传递给 `mux.Handle`。

表达式 `http.HandlerFunc(db.list)` 是一种转换，而不是函数调用，因为 `http.HandlerFunc` 是一个类型。它的定义如下：

```go
package http

type HandlerFunc func(w ResponseWriter, r *Request)

func (f HandlerFunc) ServeHTTP(w ResponseWriter, r *Request) {
    f(w, r)
}
```

`HandlerFunc` 演示了 Go 接口机制的一些不寻常特性。它是一个拥有方法并满足接口 `http.Handler` 的函数类型。其 `ServeHTTP` 方法的行为是调用底层函数。因此 `HandlerFunc` 是一个适配器，允许函数值满足接口，其中函数和接口的唯一方法具有相同的签名。实际上，这个技巧让像 `database` 这样的单一类型以多种不同的方式满足 `http.Handler` 接口：一次通过其 `list` 方法，一次通过其 `price` 方法，依此类推。

因为以这种方式注册处理程序非常常见，`ServeMux` 有一个名为 `HandleFunc` 的便捷方法来为我们完成此操作，因此我们可以将处理程序注册代码简化为：

```go
mux.HandleFunc("/list", db.list)
mux.HandleFunc("/price", db.price)
```

从上面的代码可以很容易地看出如何构建一个程序，其中有两个不同的 Web 服务器，监听不同的端口，定义不同的 URL，并分派给不同的处理程序。我们只需构建另一个 `ServeMux` 并再次调用 `ListenAndServe`，也许可以并发地进行。但在大多数程序中，一个 Web 服务器就足够了。此外，通常在应用程序的许多文件中定义 HTTP 处理程序，如果它们都必须显式注册到应用程序的 `ServeMux` 实例，那将是一种麻烦。

因此，为了方便，`net/http` 提供了一个名为 `DefaultServeMux` 的全局 `ServeMux` 实例，以及包级函数 `http.Handle` 和 `http.HandleFunc`。要将 `DefaultServeMux` 用作服务器的主处理程序，我们不必将其传递给 `ListenAndServe`；`nil` 即可。

服务器的主函数随后可以简化为：

```go
func main() {
    db := database{"shoes": 50, "socks": 5}
    http.HandleFunc("/list", db.list)
    http.HandleFunc("/price", db.price)
    log.Fatal(http.ListenAndServe("localhost:8000", nil))
}
```

最后，一个重要的提醒：正如我们在 [Section 1.7](#ebook_split_017.html#id-awebserver) 中提到的，Web 服务器在新的 goroutine 中调用每个处理程序，因此当访问其他 goroutine（包括对同一处理程序的其他请求）也可能访问的变量时，处理程序必须采取预防措施，例如*加锁*。我们将在接下来的两章中讨论并发。
