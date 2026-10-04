

```go
78 // Delete consumer instance
79 deleteReq, err := 
80 http.NewRequest(http.MethodDelete, fmt.Sprint(DELETE_CONSUMER, HOST, GROUP, CONSUMER), nil)
81 if err != nil {
82 panic(err)
83 }
84 fmt.Printf("->%s\n", deleteReq.URL)
85 resp, err := client.Do(deleteReq)
86 if err != nil {
87 panic(err)
88 }
89 fmt.Printf("<-Response %s\n", resp.Status)
90 }
```

该程序展示了整个过程中客户端与服务器之间的请求和响应。

```
->Call http://localhost:8082/consumers/testGroup
->Body("name":"testConsumer", "format": "json")
->Response 200 OK
->Body("instance_id":"testConsumer", "base_url":"http://rest-proxy/method2/consumers/testGroup/instances/testConsumer")
->Call http://localhost:8082/consumers/testGroup/instances/testConsumer/subscription
->Body("topic":"HelloTopic}")
->Response 204 No Content
->Call http://localhost:8082/consumers/testGroup/instances/testConsumer/records
->Response 200 OK
->Body("topic":"HelloTopic", "key":"null", "value":{
  "name":"John","email":"john@gmail.com", "partition":0, "offset":179},
  "name":"Mary","email":"mary@gmail.com", "partition":0, "offset":188}
}
->Call http://localhost:8082/consumers/testGroup/instances/testConsumer
->Response 204 No Content
```

请注意在这种情况下，我们并没有修改消费者偏移量（offset）。通过 `/consumers/testGroup/instances/testConsumer/positions` 调用 POST 方法并传入主体中指定的下一个偏移量，是为了为处理下一批消息做好准备。对于我们的示例，最新记录的偏移量为 180，我们通过分析以下主体将下一个偏移量设置为 181。

```json
"offsets": [
{
  "topic": "HelloTopic",
  "partition": 0,
  "offset": 181
}
]
```

## 20.5 总结

本章探索了如何使用 Apache Kafka 消息流平台消费和生产数据。我们分析了 Confluent 和 Segmentio提供的不同 Kafka 客户端，并展示了它们如何从不同的角度访问同一解决方案。最后，我们演示了如何使用标准 Go 库通过 Kafka API Rest Proxy 在无需外部依赖的情况下轻松创建自己的客户端。

## 参考文献

-   [1] Apache Cassandra. Apache Cassandra 文档。https://cassandra.apache.org/doc/latest/, 2021.

-   [2] Apache Kafka. Apache Kafka 官方文档。https://kafka.apache.org/documentation/, 2021.

-   [3] Apache Kafka. Kafka 协议指南。http://kafka.apache.org/protocol, 2021.

-   [4] ECMA. JSON 数据交换语法。http://www.ecma-international.org/publications/files/ECMA-ST/ECMA-404.pdf, 2021.

-   [5] GNU. gccgo。http://gcc.gnu.org/onlinedocs/gccgo, 2021.

-   [6] golang. Go 官方文档。https://golang.org/doc/, 2021.

-   [7] GopherJS. 从 Go 到 JavaScript 的编译器。https://github.com/gopherjs/gopherjs, 2021.

-   [8] Tyler Hobbs. Cassandra 数据建模的基础性规则。https://www.datast.com/blog/basic-rules-cassandra-data-modeling, 2015.

-   [9] IETF. 逗号分隔值 (CSV) 文件的通用格式和 MIME 类型。http://tools.ietf.org/rfc4180, 2021.

-   [10] IETF. 超文本传输协议 (HTTP/1.1): 语义与内容。https://tools.ietf.org/html/rfc7231, 2021.

-   [11] Sobel Jonathan M. 和 Friedman Daniel P. 反射导向编程简介。https://web.archive.org/web/20100240091328/http://www.indiana.edu/~isobel1996.

-   [12] Rob Pike. 反射的法则。https://blog.golang.org/laws-of-reflection 2021.

-   [13] Russ Cox. 最小版本选择。https://research.swtch.com/vgo-mvs, 2018.

-   [14] SemVer. 语义版本化 2.0.0。https://semver.org/spec/v2.0.0.html, 2021.

-   [15] W3C. 可扩展标记语言 (XML)。https://www.w3.org/XML/, 2021.

-   [16] Nikola Wirth. 算法 + 数据结构 = 程序。Prentice Hall PTR, 1978.

-   [17] yaml.org. YAML 另一种标记语言 (YAML) 版本 1.2。https://yaml.org/spec/

