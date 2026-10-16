
-   calls 2. 但首先，你需要解决一个问题。`http.Client` 如果其 Transport 方法为 nil，则使用 `http.DefaultTransport`。`http.DefaultTransport` 非常出色地缓存了 TCP 连接。如果所有 500 个 HTTP 客户端都使用相同的 transport，它们都会通过约两个 TCP 套接字进行调用。

-   我们的打开连接计数器在完成此示例后会反映出两个空闲连接，这并不是我们的目标。

-   相反，你必须确保为每个 HTTP 客户端提供其自己的 transport。克隆默认 transport 3 足够我们的目的。

-   现在每个客户端都有自己的 transport，你可以确信每个客户端都会建立自己的 TCP 连接，然后循环执行 100 次 GET 调用 4，每个客户端一次。你也必须小心地 draining 5 和关闭 6 响应体，以便每个客户端可以重用其 TCP 连接。

-   当所有 500 个 HTTP 客户端完成其 100 次调用 7 后，你可以转到 Listing 13-29 并检查指标的当前状态。

**324** 第 13 章

 *\--snip--*

 resp, err := 1http.Get(fmt.Sprintf("http://%s/metrics", \*metricsAddr))

 if err != nil {

 log.Fatal(err)

 }

 b, err := ioutil.ReadAll(resp.Body)

 if err != nil {

 log.Fatal(err)

 }

 \_ = resp.Body.Close()

 metricsPrefix := 2fmt.Sprintf("%s\_%s", \*metrics.Namespace,

 \*metrics.Subsystem)

 fmt.Println("Current Metrics:")

 for \_, line := range bytes.Split(b, \[\]byte("\\n")) {

 if 3bytes.HasPrefix(line, \[\]byte(metricsPrefix)) {

 fmt.Printf("%s\\n", line)

 }

 }

 }

*Listing 13-29: 显示与你的命名空间和子系统相匹配的当前指标* *( instrumentation/main.go )*

 你从指标端点 1 获取所有指标。这将导致 Prometheus 客户端返回所有已存储的指标，以及它跟踪的每个指标的详细信息，包括你自定义的指标。由于你只关心你的指标，你可以检查每行以你的命名空间、下划线和子系统开头 2。如果行匹配这个前缀 3，则将其打印到标准输出；否则，忽略该行并继续。

 让我们在命令行上运行此示例，并查看 Listing 13-30 中的结果指标。

 $ **go run instrumentation/main.go**

 Metrics listening on "127.0.0.1:8081" ...

 Web listening on "127.0.0.1:8082" ...

 Spawning 500 connections to make 100 requests each ... done.

 Current Metrics:

 web\_server1\_open\_connections 1500

 web\_server1\_request\_count 250000

 web\_server1\_request\_duration\_histogram\_seconds\_bucket{le="1e-07"} 30

 web\_server1\_request\_duration\_histogram\_seconds\_bucket{le="2e-07"} 1

 web\_server1\_request\_duration\_histogram\_seconds\_bucket{le="3e-07"} 613

 web\_server1\_request\_duration\_histogram\_seconds\_bucket{le="4e-07"} 13591

 web\_server1\_request\_duration\_histogram\_seconds\_bucket{le="5e-07"} 33216

 web\_server1\_request\_duration\_histogram\_seconds\_bucket{le="1e-06"} 40183

 web\_server1\_request\_duration\_histogram\_seconds\_bucket{le="2.5e-06"} 49876

 web\_server1\_request\_duration\_histogram\_seconds\_bucket{le="5e-06"} 49963

 web\_server1\_request\_duration\_histogram\_seconds\_bucket{le="7.5e-06"} 49973

 web\_server1\_request\_duration\_histogram\_seconds\_bucket{le="1e-05"} 49979

 web\_server1\_request\_duration\_histogram\_seconds\_bucket{le="0.0001"} 49994

 web\_server1\_request\_duration\_histogram\_seconds\_bucket{le="0.001"} 49997

 web\_server1\_request\_duration\_histogram\_seconds\_bucket{le="0.01"} 450000

 web\_server1\_request\_duration\_histogram\_seconds\_bucket{le="+Inf"} 50000

 web\_server1\_request\_duration\_histogram\_seconds\_sum 50.04102166899999979

 web\_server1\_request\_duration\_histogram\_seconds\_count 650000

*Listing 13-30: Web 服务器输出和结果指标*

 如预期，500 个连接在你查询指标时处于打开状态。这些连接是空闲的。你可以通过在完成 100 次 GET 调用后调用其 CloseIdleConnections 方法来尝试更改空闲连接计数的变化；观察该变化如何影响打开连接计数。同样，观察当你未定义其 Transport 字段时，打开连接计数的变化情况。

 请求计数为 50,000 2，因此所有请求都成功了。

 你注意到什么缺失了？写入错误计数。由于没有发生写入错误，写入错误计数从未递增。因此，它不会出现在指标输出中。你可以调用 metrics.WriteErrors .Add(0) 让该指标显示而不改变其值，但它的缺失可能更令你困扰而不是令 Prometheus 困扰。要注意指标输出可能不包含所有已仪器化的指标，只包含自初始化以来已发生变化的指标。

 底层的 Prometheus 直方图是 *累积* 直方图：任何递增 bucket 的计数也会递增小于该值的所有 bucket 的计数。因此，你会在每个 bucket 中看到递增的值，直到达到 0.01 bucket 4。即使你定义了 bucket 范围，Prometheus 仍会为你添加一个无限 bucket。在此示例中，你定义的 bucket 小于所有观察到的值 3，因此其计数仍为零。

 直方图和摘要（summary）都维护两个额外计数：所有观测值的总和 5 和观测值的总数 6。如果你使用摘要，Prometheus 端点只会显示这两个计数。它不会像直方图那样详细列出摘要的 bucket。

 因此，Prometheus 服务器可以聚合直方图 bucket，但无法对摘要进行聚合。

**What You’ve Learned**

-   日志记录很难。仪器化（instrumentation）不难。要精打细算地记录日志，要 generous（慷慨）地进行仪器化。日志记录并非免费，如果不小心日志的位置和数量，它会迅速增加服务的延迟。你无法通过只记录可操作的项目（特别是那些应触发警报的项目）来犯错。相反，仪器化非常高效。你应该至少在初始阶段仪器化所有内容。指标详细描述你的服务的当前状态，并提供潜在问题的洞察，而日志则提供一种不可变的审计日志，解释服务的当前状态，并帮助你诊断故障。

-   Go 的 log 包提供了满足基本日志要求的功能。但当你需要将日志输出到多个目标或以不同级别的详细程度记录时，它会变得笨重。此时，你更适合使用像 Uber 的 Zap 这样的综合解决方案。无论你使用哪种日志记录器，都应考虑在日志条目中添加结构化的元数据。结构化日志使你能够利用软件快速过滤和搜索日志条目，尤其是当你在基础设施中集中日志时。

-   随需求调试日志（on-demand debug logging）和宽事件日志（wide event logging）是两种可以在最小化对服务性能影响的同时收集重要信息的方法。你可以通过创建一个信号文件（semaphore file）来触发日志记录器启用调试日志。当你删除该信号文件时，日志记录器会立即禁用调试日志。

-   宽事件日志（wide event logs）在请求-响应循环中总结事件。你可以将多个日志条目替换为单个宽事件日志，而不会妨碍你诊断故障的能力。

-   一种仪器化方法是使用 Go kit 的 metrics 包，该包提供了常见指标类型的接口，并为流行的指标平台提供适配器。它将指标平台的细节与你的仪器化代码隔离开来。

-   metrics 包支持计数器、计量表（gauges）、直方图和摘要（summaries）。计数器单调递增，可用于计算变化率。使用计数器跟踪请求计数、错误计数或