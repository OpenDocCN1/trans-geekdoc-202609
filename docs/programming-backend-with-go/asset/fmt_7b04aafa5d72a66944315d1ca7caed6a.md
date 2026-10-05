
# Handling Message Patterns

Messaging patterns are foundational to effective communication and data flow within distributed systems like microservices. Two of the most prevalent patterns are publish/subscribe (`pub/sub`) and queues. Each serves distinct purposes, facilitates scalability, and enhances system resilience.

## Understanding Pub/Sub and Queues

* **Publish/Subscribe (`Pub/Sub`)**: In this pattern, messages are published to a "topic" rather than directly to a single consumer. Any number of subscribers can listen to or subscribe to this topic and receive messages when they are published. This pattern is useful for broadcasting data, such as real-time status updates or event notifications, to multiple interested consumers simultaneously.
* **Queues**: This pattern ensures that a message is processed by exactly one consumer. Messages are sent to a queue and processed by a single consumer in a First In, First Out (`FIFO`) manner. It is ideal for tasks that need to be processed in order or where each task is only processed once, such as processing a bank transaction or an order in an e-commerce platform.

## Implementing Pub/Sub and Queues

We will integrate Apache Kafka for Pub/Sub and NSQ for queues into a basic service architecture that handles new user registrations and notifications to show these patterns.

### Implementing Pub/Sub with Kafka

Think of a situation wherein, when a new user registers, multiple parts of the application need to react, such as the email service sending a welcome email and the analytics service updating statistics.

* First, create a topic for registration events:
```
kafka-topics --create --topic user-registrations --bootstrap-server localhost:9092 --partitions 3 --replication-factor 1
```
* A simple producer sends a message to the `user-registrations` topic whenever a new user registers.

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
* Services that need to react to the registration implement consumers that subscribe to the `user-registrations` topic.

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

### Implementing Queues with NSQ

To understand this better, consider a scenario wherein you have to process user feedback messages one at a time to ensure each message is dealt with sequentially and without loss.

* Assuming NSQ is running, you would write to a specific topic as users submit feedback.

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
* Processing Messages from the Queue:

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

Events impacting numerous system components at once are well-suited to Kafka's pub/sub model, which enables extensive data distribution. By contrast, the order and integrity of critical operations are preserved by NSQ's queue model, which guarantees the reliable handling of tasks requiring singular processing without loss or duplication.
