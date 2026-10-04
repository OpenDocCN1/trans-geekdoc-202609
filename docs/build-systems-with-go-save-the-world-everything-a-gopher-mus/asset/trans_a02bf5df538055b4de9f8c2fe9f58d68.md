
开销。在接收批消息后进行提交更有意义。示例 20.4 中，提交在一个独立的 goroutine 中执行所有消息。批处理大小可能非常小，仅用于演示目的。Committer 函数可以检测提交是否失败，这样我们就可以处理该情况了。

# 示例 20.4: Confluent Kafka 异步消费者。

```go
package main

import (
    "fmt"
    "github.com/confluentinc/confluent-kafka-go/kafka"
)

const COMMIT_N = 2

func Committer(c *kafka.Consumer) {
    offsets, err := c.Commit()
    if err != nil {
        fmt.Printf("Error: %s\n", err)
        return
    }
    fmt.Printf("offset: %v\n", offsets[0].String())
}

func main() {
    c, err := kafka.NewConsumer(&kafka.Config{
        "bootstrap.servers": "localhost:9092",
        "group.id": "HelloGroup",
        "auto.offset.reset": "earliest",
    })
    if err != nil {
        panic(err)
    }
    defer c.Close()

    c.Subscribe("helloTopic", nil)
    counter := 0
    for {
        ev, err := c.Poll(1000)
        switch ev := ev.(type) {
        case *kafka.Message:
            counter += 1
            if counter % COMMIT_N == 0 {
                go Committer(c)
            }
            fmt.Printf("Msg on: %s\n", ev.TopicPartition, string(ev.Value))
        case kafka.PartitionEOF:
            fmt.Printf("%v\n", ev)
        case kafka.Error:
            fmt.Printf("Error: %v\n", err)
        }
    }
}
```

![](img/c7dcb4df7215ed1d3fb76d25373be6c7_298_0.png)

```go
46 break
47 default:
48     fmt.Printf("Ignored: %w\n", e)
49 }
50 }
51 }
```

![](img/c7dcb4df7215ed1d3fb76d25373be6c7_299_0.png)

在在上一个示例中，消息的处理独立于提交操作的结果。即使提交失败了，我们也可以继续接收消息。我们可以推迟消息处理，直到我们知道提交已成功。

```go
case *kafka.Message:
    offset, err := c.Commit()
    if err != nil {
        // process message...
```

如之前所述，这会产生大量的开销。一种解决方案是存储传入的消息，并在提交后以批处理的方式处理它们。这甚至可以在 routine 中完成。

```go
case *kafka.Message:
    append(messages,msg)
    counter += 1
    if counter % COMMIT_N == 0 {
        offset, err := c.Commit()
        if err != nil {
            go ProcessMsgs(messages)
        }
```

# 20.3 使用 SEGMENTIO 客户端

Kafka 客户端的缺点之一是 C 语言库的封装。这在某些平台或仅支持 Go 语言的项目中可能会成为问题。Segmentio Kafka 客户端完全用 Go 编写，并提供了消费者和生产者的完整实现，且带有如压缩或安全连接等额外功能。

# 20.3.1 Connection 类型

Segmentio 客户端使用基于 `Connection` 实例的简单实现。实例化 `Connection` 时可以指定 Kafka 主机、主题和分区。该连接提供了消费者和生产者所需的所有方法。

示例 20.5 显示了生产者的实现。连接使用 `SetWriteDeadline` 方法定义写入操作的超时。产生消息的最基本方法是 `conn.Write`，它接收包含要发送消息的字节数组。然而，出于演示目的，我们使用了 `conn.WriteMessages`，它接收包含更多信息的 Message 实例，如下定义所示。

```go
type Message struct {
  Topic string
  Partition int
  Offset int64
  Key []byte
  Value []byte
  Headers []Header
  Time time.Time
}
```

在示例中，我们遍历了所有要发送的消息。然而，我们可以简单地传递一个要发送的消息集合。写入操作返回写入的字节数以及是否存在任何错误。

> 在写入消息时，不能设置 Message 实例中的 Partition 字段。它是一个只读字段。

# 示例 20.5: Segmentio Kafka 生产者。

```go
package main

import (
	"context"
	"fmt"
	"github.com/segmentio/kafka-go"
	"time"
)

func main() {
	topic := "helloTopic"
	partition := 0
	conn, err := kafka.DialLeader(context.Background(),
	"tcp", "localhost:8092", topic, partition)
	if err != nil {
	panic(err)
	}

	defer conn.Close()

conn.SetWriteDeadline(time.Now().Add(3*time.Second))
	msgs := []string{"Save", "the", "world", "with", "Go!!!"}
	for _, m := range msgs {
		i, err := conn.WriteMessages(kafka.Message{Value: []byte(m)})
		if err != nil {
			panic(err)
		}
	}
	fmt.Printf("%d bytes: %s\n", len(m), m)
}
```

消费者的结构与生产者非常相似。`Connection` 实例可以批量读取多条消息。示例 20.6 定义了一个最小大小为 10 KB、最大大小为 10 MB的消息批。我们使用字节数组填充它，直到找到错误。最后，必须关闭批。

# 示例 20.6: Segmentio Kafka 消费者。

```go
package main

import (
    "context"
    "fmt"
    "github.com/segmentio/kafka-go"
    "time"
)

func main() {
    topic := "helloTopic"
    partition := 0
    conn, err := kafka.DialLeader(context.Background(),
        "tcp", "localhost:8092", topic, partition)
    if err != nil {
        panic(err)
    }
    defer conn.Close()

    conn.SetReadDeadline(time.Now().Add(time.Second))
    batch, err := conn.ReadBatch(10e3)
    defer batch.Close()
    for {
        b := make([][]byte, 10e6)
        n, err := batch.Read(b)
        if err != nil {
            break
        }
        fmt.Printf("Received %d bytes: %s\n", len(b), b)
    }
}
```

![](img/c7dcb4df7215ed1d3fb76d25373be6c7_301_0.png)

# 20.3.2 Writer 和 Reader 类型

Segmentio 客户端提供了 Writer 和 Reader 高级抽象。这些类型简化了生产者和消费者的实现。示例 20.7 使用 writer 实例向 Kafka 发送消息。注意，所有操作都是使用 Writer 实例而不是 `Connection` 实例执行的。

# 示例 20.7: Segmentio Kafka 高级生产者。

```go
package main

import (
    "context"
    "fmt"
    "github.com/segmentio/kafka-go"
    "time"
)

func main() {
    topic := "helloTopic"
    partition := 0
    conn, err := kafka.DialLeader(context.Background(), "localhost:8092", topic, partition)
    if err != nil {
        panic(err)
    }

    defer conn.Close()

    conn.WriteDeadline(time.Now().Add(3*time.Second))
    msgs := []string{"Save", "world", "with", "Go!!!"}
	for _, msg := range msgs {
		i, err := conn.WriteMessages(kafka.Message{Value: []byte(msg)})
		if err != nil {
			panic(err)
		}
	}
	fmt.Printf("Sent %d bytes: %s\n", i, msg)
}
```

![](img/c7dcb4df7215ed1d3fb76d25373be6c7_302_0.png)

WriterMessages 方法旨在接收消息集合。注意示例没有正确使用该函数。为了提高性能，应该将所有可用消息传递给此方法以提高吞吐量。Stats 方法返回包含该 writer 统计信息的实例。示例打印了写入的总字节数，尽管有一组可用的统计数据。

可以使用 Reader 类型实现消费者，如示例 20.8 所示。使用 ReaderConfig 配置 Reader，指定 broker、分区、主题和要订阅的组。FetchMessage 方法会阻塞直到有新事件可用或上下文超时。

# 示例 20.8: Segmentio Kafka 高级消费者。

```go
package main

import (
    "context"
    "fmt"
    "github.com/segmentio/kafka-go"
)

func main() {
    r := kafka.NewReader(kafka.ReaderConfig{
        Brokers:   []string{"localhost:9092"},
        Partition: 0,
        Topic:    "helloTopic",
        GroupID:  "testGroup",
        MinBytes: 10e3,
        MaxBytes: 10e6,
    })
    defer r.Close()

    for {
        m, err := r.FetchMessage(context.Background())
        if err != nil {
            break
        }
        if err := r.CommitMessages(context.Background(), m); err != nil {
            panic(err)
        }
        fmt.Printf("Topic %s msg: %s\n", m.Topic, m.Value)
    }
}
```

> Topic helloTopic msg: Save
> Topic helloTopic msg: the
> Topic helloTopic msg: world
> Topic helloTopic msg: with
> Go!!

在这个示例中，我们提交了每条消费的消息。这产生了不必要的开销，可以通过同时提交多条消息来缓解。CommitMessages 方法有一个变长参数表示要提交的消息数量。

记住，只有当 Kafka broker 中的自动提交配置参数被禁用时，才需要手动提交。

# 20.4 使用 KAFKA REST API

在之前的章节中，我们探索了如何使用官方 Confluent Segmentio 解决方案从 Kafka 生产和消费消息。Kafka 在 TCP 上定义了自己的协议 [3]，该协议由 librdkafka 库实现，使得 Kafka 功能可用。Confluent 客户端是该库的封装。遗憾的是，这可能不是

