```
func main() {
	 c, err := kafka.NewConsumer(&kafka.ConfigMap{
		"bootstrap.servers": "localhost:9092",
		"group.id": "helloGroup",
		"auto.offset.reset": "earliest",
	})
	if err != nil {
		panic(err)
	}
	cfer c.Close()

	c.Subscribe("helloTopic", nil)
	for {
		ev := c.Poll(1000)
		switch e := ev.(type) {
			case kafka.Message:
				c.Commit()
				fmt.Printf("On %s: %s\n", e.Partition, string(e.Value))
			case kafka.PartitionEOF:
				fmt.Printf("%v\n", e)
				case kafka.Error:
				fmt.Printf("Error: %v\n", e)
				break
			default:
				fmt.Printf("Ignored: %v\n", e)
		}
	}
}
```

The Example receives the messages from the producer defined in Example 20.1. Remember that in case the enable.auto.commit configuration parameter is set to false, consumers must commit to ensure the correctness of the received messages. This can be done using the Commit method as shown in the Example.

# 20.2.3 Asynchronous producer

Our Example of a synchronous producer is not a good idea if we want to get a better throughput for our solution. Actually, Kafka is prepared to receive batches of events to be processed. Normally, producers should send batches of events and wait until they are processed. We can use the delivery channel from the `Produce` function to write a non-blocking handler to observe if everything is working correctly.

Example 20.3 rewrites the producer with a goroutine that handles the production process without blocking the execution. In this case, to ensure that we wait until all the messages are sent, the `Flush` function blocks the execution until everything is flushed out.

# Example 20.3: Confluent Kafka asynchronous producer.