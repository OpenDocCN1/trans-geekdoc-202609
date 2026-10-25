```
\#[tokio::main]
async fn main() {
    // Set up producer
    let producer: FutureProducer = ClientConfig::new()
        .set("bootstrap.servers", "localhost:9092")
        .create()
        .expect("Producer creation error");

    // Set up consumer
    let consumer: StreamConsumer = ClientConfig::new()
        .set("group.id", "example_group")
        .set("bootstrap.servers", "localhost:9092")
        .set("auto.offset.reset", "earliest")
        .create()
        .expect("Consumer creation error");

    // Subscribe to topic
    consumer.subscribe(&["example_topic"]).expect("Subscription error");

    // Produce message
    let payload = serde_json::json!({ "key": "value" }).to_string();
    producer.send(
        FutureRecord::to("example_topic")
            .payload(&payload)
            .key("key"),
        0,
    ).await.expect("Failed to produce message");

    // Consume messages
    let mut message_stream = consumer.start();
    while let Some(message) = message_stream.next().await {
        match message {
            Ok(m) => {
                let payload = m.payload().unwrap_or(&[]);
                let key = m.key().unwrap_or(&[]);
                println!("Received message: key = {:?}, payload = {:?}", key,
                payload);
            }
        }
    }
}
```