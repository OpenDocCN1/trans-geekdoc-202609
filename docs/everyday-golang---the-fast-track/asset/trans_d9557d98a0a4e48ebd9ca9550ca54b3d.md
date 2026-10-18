
```
})

    err := g.Wait()
    if err != nil {
        fmt.Fprintf(os.Stderr, "error found: %s", err.Error())
        os.Exit(1)
    }
    fmt.Print("All work completed as expected")
}

func printLater(msg string, duration time.Duration) {
    time.Sleep(duration)
    fmt.Printf(msg)
}
```

运行代码时，你将看到以下输出：

```
$ go run ./
Hello
alex
error found: world failed
```

你可以在软件包的文档中了解更多关于*错误组*的信息。

## 限制对昂贵资源的请求

在使用 Goroutine 时，很容易陷入不良状况：像网络连接、数据库连接或打开的文件等资源被消耗得过多。Go 源码中有一个名为 “internal/singleflight” 的包，用于限制 DNS 查找的进行中请求。Go 团队认为它非常有用，于是将其导出并单独维护，以便我们也能从中受益。

你可以在这里查看外部版本：golang.org/x/sync/singleflight

它的API与我们刚刚看过的错误组类似：

```
package main

import (
    "fmt"
    "golang.org/x/sync/singleflight"
)

type ISSPosition struct {
    Latitude  float64 `json:"latitude"`
    Longitude float64 `json:"longitude"`
}

func (i *ISSPosition) String() string {
    return fmt.Sprintf("(%f,%f)", i.Latitude, i.Longitude)
}

func main() {
    s := singleflight.Group{}
    key := "key for resource"
```

```
res, err, shared := s.Do(key, func() (any, error) {
    return ISSPosition{Latitude: 40.0, Longitude: -0.31}, nil
})

fmt.Printf("Shared response? %v\n", shared)
if err != nil {
    fmt.Println(err)
    return
}
position := res.(ISSPosition)

fmt.Printf("Position: %s\n", position.String())
}
```

请注意：

- 响应以 “any” 返回，这与写 “interface{}” 相同，因此任何结果都需要被解包（unwrap）。
- 有一个名为 “key” 的变量，意味着 singleflight 组可以用于多个调用。

如果 key 与现有调用匹配，你将在该调用就绪时获得其响应；如果调用与某个 key 不匹配，它会在完成之前收集其他所有传入的请求。

如果你觉得有用，你还可以判断自己是获得了共享响应，还是作为第一个调用者获得了响应的原始副本。

在我们的示例中，我们永远不会得到共享响应，所以让我们构建一个带有 HTTP 服务器的示例，并模拟多个连接和用户。

你可以在 “singleflight-simple” 文件夹中找到源代码。

假设你正在托管一个 HTTP 服务器，该服务器需要调用另一台服务器并返回结果，而该查询需要 2 秒。如果在 2 秒内收到 1 个请求，那么你将对上游服务器发出 1 次调用；但如果你收到 1000 个请求，那么在同一时间段内你将发出 1000 次调用。

如果 API 调用开销很大或可能被限流，这就尤其成问题。2022 年夏天，我们在 OpenFaaS 网关中实现了 singleflight 模式，这大大减少了从零开始扩容期间的 API 调用。为后端实现单飞查询 #1734

让我们通过一个使用 singleflight 和 HTTP 的示例来实践，这很可能也是你需要使用它的场景。

http://api.open-notify.org/iss-now.json 上的 OpenAPI 会向我们展示国际空间站（ISS）的纬度和经度，不过我们可能想重新格式化响应，使其只包含纬度和经度这两个值。

API 响应：

```
{
  "timestamp": 1658399875,
  "iss_position": {
    "latitude": "43.6602",
    "longitude": "-160.8366",
  },
  "message": "success"
}
```

期望的输出：

```
{
  "latitude": "43.6602",
  "longitude": "-160.8366",
}
```

你可以在 “singleflight-http” 文件夹中找到源代码。

```
package main

import (
    "encoding/json"
    "fmt"
    "io"
    "log"
    "net/http"
    "time"

    "golang.org/x/sync/singleflight"
)

type ISSRes struct {
    Position ISSPosition `json:"iss_position"`
}

type ISSPosition struct {
    Latitude  string `json:"latitude"`
    Longitude string `json:"longitude"`
}

func main() {

    s := singleflight.Group{}

    http.HandleFunc("/position", func(w http.ResponseWriter, r *http.Request) {

        uri := "http://api.open-notify.org/iss-now.json"
        res, err, _ := s.Do(uri, func() (any, error) {

            fmt.Printf("HTTP call to: %s\n", uri)

            req, err := http.NewRequest(http.MethodGet, uri, nil)
            if err != nil {
                return nil, fmt.Errorf("unable to create request: %s", err)
            }

            res, err := http.DefaultClient.Do(req)
            if err != nil {
                return nil, fmt.Errorf("unable to make request: %s", err)
            }
            var body []byte

            if res.Body != nil {
                defer res.Body.Close()
                body, _ = io.ReadAll(res.Body)
            }

            if res.StatusCode != http.StatusOK {
                return nil, fmt.Errorf("bad status: %d, body: %s", res.StatusCode, string(body))
            }
```

```
i := &ISSRes{}
if err := json.Unmarshal(body, i); err != nil {
return nil, fmt.Errorf("can't unmarshal response: %s, error: %s", string(body), err)
}

return i.Position, nil
})

if err != nil {
    http.Error(w, err.Error(), http.StatusInternalServerError)
    return
}

position := ISSPosition{
    Latitude:  res.(ISSPosition).Latitude,
    Longitude: res.(ISSPosition).Longitude,
}

encoded, _ := json.Marshal(position)
w.Header().Add("Content-Type", "application/json")
w.Write(encoded)
})

port := 8080
server := &http.Server{
    Addr:          fmt.Sprintf(":%d", port),
    ReadTimeout:   10 * time.Second,
    WriteTimeout:  10 * time.Second,
    MaxHeaderBytes: 1 << 20,
}
log.Printf("Listening on port: %d\n", port)
log.Printf("Endpoints available: /position")
log.Fatal(server.ListenAndServe())
}
```

运行该示例，使用 curl 调用它，然后再使用 hey 调用：

```
curl -s http://127.0.0.1:8080/position
{"latitude":"-40.3230","longitude":"-77.2043"}
```

每次命中该端点时，你都会看到消息：“HTTP call to: http://api.open-notify.org/iss-now.json”。现在尝试用 10 个并发用户生成流量，总共 10 个请求：

```
hey -c 10 -n 10 http://127.0.0.1:8080/position
```

当我运行这个时，我只看到“HTTP call to”被打印了一次。

尝试持续 5 秒的更长时间段：

```
hey -c 10 -z 5s http://127.0.0.1:8080/position
```

我注意到在这 5 秒内共发起了 330 次调用，而只有 33 次是对 API 的上游调用。

如果需要，你可以通过使用 Go map 引入缓存来进一步优化 API。请记住，缓存还需要一个失效策略来使数据过期，以便根据需要刷新。

## 在 Goroutine 之间共享数据

在 Go 中，在内存限制范围内，有两种在 Goroutine 之间共享数据的方法。第一种是创建一个带有锁机制的类型，这样读取方或写入方可以获得锁，以防止两个 Goroutine 试图更新同一份数据，进而避免产生竞争条件。

在第一个示例中，我们的代码可能看起来类似于：

```go
package main

import (
    "sync"
)

type ScrapeRun struct {
    Result []ScrapeResult
    Lock   *sync.Mutex
}

type ScrapeResult struct {
    HTTPCode   int
    HTTPLength int
    Error      error
}
```

在主程序流程中，你应该编写与下面类似的代码：

```go
package main

import (
    "fmt"
    "io"
    "net/http"
    "sync"
)

type ScrapeRun struct {
    Results map[string]ScrapeResult
    Lock    *sync.Mutex
}

type ScrapeResult struct {
    HTTPCode   int
    HTTPLength int64
    Error      error
}

func scrape(url string, sr *ScrapeRun) {
    res, err := http.Get(url)
    if err != nil {
        sr.Lock.Lock()
        defer sr.Lock.Unlock()

        sr.Results[url] = ScrapeResult{
            Error:    err,
            HTTPCode: http.StatusBadGateway,
```
