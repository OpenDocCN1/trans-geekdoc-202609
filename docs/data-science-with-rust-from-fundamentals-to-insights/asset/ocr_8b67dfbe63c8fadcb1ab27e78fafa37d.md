```
.set("bootstrap.servers", "localhost:9092")
.create()
.expect("Producer creation error");

for i in 0..10 {
 producer.send(BaseRecord::to("test_topic")
 .payload(&format!("Message {}", i))
 .key(&format!("Key {}", i)))
 .expect("Failed to enqueue");
}

producer.flush(std::time::Duration::from_secs(1));
}
```

+   Explanation: This code initializes a Kafka producer that sends ten messages to a topic named "test_topic". The messages are flushed to ensure they are sent before the program exits.

+   Kafka Consumer:

+   Implement a Kafka consumer: \`\`\` rust use rdkafka::consumer::{BaseConsumer, Consumer}; use rdkafka::config::ClientConfig; use std::time::Duration;
+   
+   fn main() {
+   let consumer: BaseConsumer = ClientConfig::new()
+   .set("group.id", "test_group")
+   .set("bootstrap.servers", "localhost:9092")
+   .set("enable.partition.eof", "false")
+   .create()
+   .expect("Consumer creation error");
+   
+   consumer.subscribe(&["test_topic"]).expect("Subscription error");
+   
+   loop {
+   match consumer.poll(Duration::from_secs(1)) {
+   Some(Ok(message)) => {