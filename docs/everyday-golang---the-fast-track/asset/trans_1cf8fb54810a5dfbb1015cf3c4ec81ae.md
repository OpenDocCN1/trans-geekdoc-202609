
```go
MaxHeaderBytes: http.DefaultMaxHeaderBytes, // 1MB - can be overridden by setting Server.MaxHeaderBytes.
    Handler:        router,
}
log.Printf("Listening on: %d", tcpPort)
log.Fatal(s.ListenAndServe())
}
```

然后试试看：

```text
# Terminal 1
$ go run main.go

# Terminal 2
$ curl -i http://127.0.0.1:8080/customer/alex

HTTP/1.1 200 OK
Date: Tue, 08 Jun 2021 10:32:16 GMT
Content-Length: 20
Content-Type: text/plain; charset=utf-8

Found customer: alex

$ curl -i http://127.0.0.1:8080/customer/john

HTTP/1.1 404 Not Found
Content-Type: text/plain; charset=utf-8
X-Content-Type-Options: nosniff
Date: Tue, 08 Jun 2021 10:32:55 GMT
Content-Length: 24

Customer john not found
```

## 编写 HTTP 中间件

HTTP 中间件是一种在端点的主 HTTP 处理器执行之前或之后运行的函数。你可能需要这样做的原因包括：日志记录与追踪、身份验证与授权，以及应用其他规则或解析。

让我们尝试一个完整的示例，该示例会拒绝任何没有 Bearer 头（通常用于身份验证）的 HTTP 请求：

```sh
export GH_USERNAME="alexellis"
mkdir -p $GOPATH/src/github.com/$GH_USERNAME/http-bearer
cd $GOPATH/src/github.com/$GH_USERNAME/http-bearer
go mod init http-bearer

touch main.go
```

代码如下：

```go
package main

import (
    "fmt"
```
```
"log"
"net/http"
"os"
"time"
)

func makeAuth(token string, next http.HandlerFunc) http.HandlerFunc {
    return func(w http.ResponseWriter, r *http.Request) {
        if b := r.Header.Get("Authorization"); len(b) == 0 || b != "Bearer: "+token {
            http.Error(w, "Not authorized", http.StatusUnauthorized)
        } else {
            next(w, r)
        }
    }
}

func main() {
    token := os.Getenv("TOKEN")
    next := func(w http.ResponseWriter, r *http.Request) {
        w.Write([]byte("Authorized"))
    }

    http.HandleFunc("/customer/", makeAuth(token, next))

    tcpPort := 8080
    s := &http.Server{
        Addr:           fmt.Sprintf(":%d", tcpPort),
        ReadTimeout:    time.Second * 10,
        WriteTimeout:   time.Second * 10,
        MaxHeaderBytes: http.DefaultMaxHeaderBytes,
    }
    log.Printf("Listening on: %d", tcpPort)
    log.Fatal(s.ListenAndServe())
}
```

请注意，makeAuth 函数在 HTTP 授权头周围添加了一个 if 守卫；如果未找到该头部或令牌不匹配，则不会进行“next”HTTP 调用。这样，你可以按需链式使用任意数量的 HTTP 中间件，例如先授权再记录日志，以及其他任何需要的操作。

试试运行：

```
# Terminal 1
go run main.go

# Terminal 2

curl http://127.0.0.1:8080/customer/alex -H "Authorization: Bearer: test"
Authorized

curl http://127.0.0.1:8080/customer/alex
Not authorized
```

```go
})

s := &http.Server{
	Addr:           fmt.Sprintf(":%d", port),
	ReadTimeout:    readTimeout,
	WriteTimeout:   writeTimeout,
	MaxHeaderBytes: 1 << 20, // Max header of 1MB
	Handler:        metricsMux,
}

s.ListenAndServe()
}
```

现在：

```bash
# Terminal 1
go run main.go

# Terminal 2
curl http://127.0.0.1:8080/metrics
```

你会看到关于 `/metrics` 端点本身的 HTTP 指标：

```text
# HELP promhttp_metric_handler_requests_in_flight Current number of scrapes being served.
# TYPE promhttp_metric_handler_requests_in_flight gauge
promhttp_metric_handler_requests_in_flight 1
# HELP promhttp_metric_handler_requests_total Total number of scrapes by HTTP status code.
# TYPE promhttp_metric_handler_requests_total counter
promhttp_metric_handler_requests_total{code="200"} 1
promhttp_metric_handler_requests_total{code="500"} 0
promhttp_metric_handler_requests_total{code="503"} 0
```

然后你还会看到内存信息、Go 版本、活跃的 Goroutine 数量以及许多其他细节。

```text
# HELP go_goroutines Number of goroutines that currently exist.
# TYPE go_goroutines gauge
go_goroutines 8

# HELP go_info Information about the Go environment.
# TYPE go_info gauge
go_info{version="go1.15.6"} 1

# HELP go_memstats_alloc_bytes Number of bytes allocated and still in use.
# TYPE go_memstats_alloc_bytes gauge
go_memstats_alloc_bytes 1.152704e+06
# HELP go_memstats_alloc_bytes_total Total number of bytes allocated, even if freed.
# TYPE go_memstats_alloc_bytes_total counter
go_memstats_alloc_bytes_total 1.152704e+06
```

一旦部署了 Prometheus，你就可以配置它来抓取 Go 应用程序。如果你从其 GitHub 发布页面下载 Prometheus，则可以将它作为普通可执行程序运行。

在压缩包中你会看到 prometheus 和 prometheus.yml 文件。解压文件并编辑 prometheus.yaml。

```yaml
# my global config
global:
  scrape_interval:      15s # Set the scrape interval to every 15 seconds. Default is every 1 minute.
```
```
evaluation_interval: 15s # Evaluate rules every 15 seconds. The default is every 1 minute.
# scrape_timeout is set to the global default (10s).

# Alertmanager configuration
alerting:
  alertmanagers:
  - static_configs:
    - targets:
      # - alertmanager:9093

# Load rules once and periodically evaluate them according to the global
  'evaluation_interval'.
rule_files:
  # - "first_rules.yml"
  # - "second_rules.yml"

# A scrape configuration containing exactly one endpoint to scrape:
# Here it's Prometheus itself.
scrape_configs:
  # The job name is added as a label `job=<job_name>` to any timeseries scraped from this
  config.
  - job_name: 'prometheus'

    # metrics_path defaults to '/metrics'
    # scheme defaults to 'http'.
    static_configs:
    - targets: ['localhost:9090']
```

在 scrape_configs 下，为你的微服务添加一个 job 名称和抓取目标。

```
# The job name is added as a label `job=<job_name>` to any timeseries scraped from this
  config.
- job_name: 'service'

  # metrics_path defaults to '/metrics'
  # scheme defaults to 'http'.
  static_configs:
  - targets: ['localhost:8080']
```

如果部署在集群或网络中，目标地址将从 localhost 改为服务可达的 IP 地址或 DNS 名称，例如：gateway:8080。

```
# In Terminal 1
$ ./prometheus --config.file=./prometheus.yml

# In Terminal 2
$ go run main.go
```

你可以通过以下地址访问 Prometheus UI：

http://127.0.0.1:9090

在“Status”和“Targets”下，你可以查看这两个目标以及它们上次被抓取的时间。如果访问端点时有任何问题，你也可以在这里看到。

抓取配置

![](img/0b5c3b498f62579835cf1d543b46de92_109_0.png)

图 14.1：抓取配置

指标浏览器（地球形按钮）会显示所有可用于浏览的指标。

![](img/0b5c3b498f62579835cf1d543b46de92_109_1.png)

图 14.2：指标浏览器

表格视图在查看数字时也很有用。

你可以编写的最有用的查询之一是检查服务上某些 HTTP 请求的速率。此查询查找 200 / OK 响应，但你可能想挑选出特定的错误码来检测问题。

显示查询速率的图表

```
rate(
    promhttp_metric_handler_requests_total{
        code="200",
        job="service"
    }[1m]
)
```

在 1 分钟窗口内，针对 service 作业的 HTTP 200 状态码，追踪 promhttp_metric_handler_requests_total 指标的调用速率。

请记住，这只是 Prometheus 端点本身的状态码，因此它还没有对我们服务可能发出的任何 API 调用进行检测。不过，这仍有价值，因为它还可以通过类似的查询来跟踪尚未清理的 Goroutine 泄漏：

```
rate(
    go_goroutines{
        job="service"
    }[1m]
)
```

请注意，“job” 正在查看我们 HTTP 服务器的抓取端点。如果你愿意，你也可以查看 Prometheus 自身运行的 Goroutine 数量，因为它在“prometheus”作业下对自身进行检测。

## 为我们的微服务跟踪 HTTP 指标

我们现在将构建一个微服务，它可以为任何输入内容生成 SHA256 哈希，并对有效输入返回 200 状态码。当请求体不存在且 HTTP 方法不是 POST 时，该服务将返回 400 错误。

完成后，我们将能够为你希望检测的任何 HTTP 中间件或处理器测量速率、错误和持续时间（RED）指标。

```
export GH_USERNAME="alexellis"
mkdir -p $GOPATH/src/github.com/$GH_USERNAME/custom-metrics/
cd $GOPATH/src/github.com/$GH_USERNAME/custom-metrics/
go mod init metrics

touch main.go
touch metrics.go
```

创建 metrics.go：

```go
package main

import (
    "net/http"

    "github.com/prometheus/client_golang/prometheus"
    "github.com/prometheus/client_golang/prometheus/promauto"
    "github.com/prometheus/client_golang/prometheus/promhttp"
)

type HttpMetrics struct {
    RequestsTotal           *prometheus.CounterVec
    RequestDurationHistogram *prometheus.HistogramVec
}

func NewHttpMetrics() HttpMetrics {
    return HttpMetrics{
        RequestsTotal: promauto.NewCounterVec(prometheus.CounterOpts{
            Subsystem: "http",
            Name:      "requests_total",
            Help:      "total HTTP requests processed",
        }, []string{"code", "method"}),
        RequestDurationHistogram: promauto.NewHistogramVec(prometheus.HistogramOpts{
```

