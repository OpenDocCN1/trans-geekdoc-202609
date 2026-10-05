

# 处理消息模式

消息模式是微服务等分布式系统中有效通信和数据流的基础。两种最常见的模式是发布/订阅（`pub/sub`）和队列。每种模式服务于不同的目的，促进可扩展性，并增强系统弹性。

## 理解 Pub/Sub 和队列

* **发布/订阅（`Pub/Sub`）**：在此模式中，消息发布到“主题”，而不是直接发送给单个消费者。任意数量的订阅者都可以监听或订阅该主题，并在消息发布时接收消息。此模式适用于向多个感兴趣的消费者同时广播数据，例如实时状态更新或事件通知。
* **队列**：此模式确保消息仅由一个消费者处理。消息发送到队列，并由单个消费者以先进先出（`FIFO`）的方式处理。它非常适合需要按顺序处理或每个任务仅处理一次的任务，例如处理银行交易或电子商务平台中的订单。

## 实现 Pub/Sub 和队列

我们将 Apache Kafka 用于 Pub/Sub，NSQ 用于队列，集成到一个基础服务架构中，该架构处理新用户注册和通知，以展示这些模式。

### 使用 Kafka 实现 Pub/Sub

设想一种情况，当新用户注册时，应用程序的多个部分需要做出反应，例如邮件服务发送欢迎邮件，分析服务更新统计数据。

* 首先，创建一个用于注册事件的主题：
```
kafka-topics --create --topic user-registrations --bootstrap-server localhost:9092 --partitions 3 --replication-factor 1
```
* 一个简单的生产者会在新用户注册时向 `user-registrations` 主题发送消息。

```go
package main
import (
"context"
"github.com/segmentio/kafka-go"
"log"
)
func main() {
w := &kafka.Writer{
Addr: kafka.TCP("localhost:9092"),
Topic: "user-registrations",
Balancer: &kafka.LeastBytes{},
}
err := w.WriteMessages(context.Background(),
kafka.Message{
Value: []byte("New user registered"),
},
)
if err != nil {
log.Fatalf("failed to write messages: %s", err)
}
if err := w.Close(); err != nil {
log.Fatalf("failed to close writer: %s", err)
}
}
```
* 需要对注册做出反应的服务实现消费者，订阅 `user-registrations` 主题。

```go
package main
import (
"context"
"fmt"
"github.com/segmentio/kafka-go"
)
func main() {
r := kafka.NewReader(kafka.ReaderConfig{
Brokers: []string{"localhost:9092"},
Topic: "user-registrations",
GroupID: "email-service",
})
for {
msg, err := r.ReadMessage(context.Background())
if err != nil {
break
}
fmt.Printf("received: %s\n", string(msg.Value))
// Process the message
}
if err := r.Close(); err != nil {
fmt.Printf("failed to close reader: %s", err)
}
}
```

### 使用 NSQ 实现队列

为了更好地理解，请考虑一种场景，其中你需要一次处理一条用户反馈消息，以确保每条消息按顺序处理且不会丢失。

* 假设 NSQ 正在运行，当用户提交反馈时，你会向特定主题写入数据。

```go
package main
import (
"github.com/nsqio/go-nsq"
"log"
)
func main() {
config := nsq.NewConfig()
producer, err := nsq.NewProducer("localhost:4150", config)
if err != nil {
log.Fatal(err)
}
err = producer.Publish("feedback", []byte("User feedback received"))
if err != nil {
log.Fatal("Could not publish message: ", err)
}
producer.Stop()
}
```
* 处理队列中的消息：

```go
package main
import (
"github.com/nsqio/go-nsq"
"log"
)
func main() {
config := nsq.NewConfig()
consumer, err := nsq.NewConsumer("feedback", "default", config)
if err != nil {
log.Fatal(err)
}
consumer.AddHandler(nsq.HandlerFunc(func(message *nsq.Message) error {
log.Printf("Got a message: %v", string(message.Body))
return nil
}))
err = consumer.ConnectToNSQD("localhost:4150")
if err != nil {
log.Fatal("Could not connect to queue: ", err)
}
<-consumer.StopChan
}
```

一次影响众多系统组件的事件非常适合 Kafka 的 pub/sub 模型，该模型能够实现广泛的数据分发。相比之下，NSQ 的队列模型通过保证需要单一处理的任务能够可靠处理且不会丢失或重复，保留了关键操作的顺序和完整性。

