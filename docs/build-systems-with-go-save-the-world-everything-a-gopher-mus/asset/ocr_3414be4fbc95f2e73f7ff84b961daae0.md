overhead. it makes more sense to commit after a batch of messages is received. Example 20.4, a commit does every messages in a separated goroutine. The batch size is probably very small and it only makes sense for demonstration purposes. Committer function can detect if the commit fails so we can handle the situation.

# Example 20.4: Confluent Kafka asynchronous consumer.

```
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
    fmt.Printf("offset: %v\n", offsets[].String())
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
            fmt.Printf("%v\n", e)
        case kafka.Error:
            fmt.Printf("Error: %v\n", err)
        }
    }
```

![](bbox=[0.715, 0.256, 0.885, 0.343])