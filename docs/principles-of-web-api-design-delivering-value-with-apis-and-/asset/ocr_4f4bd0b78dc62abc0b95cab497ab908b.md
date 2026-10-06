# CHAPTER 9 ASYNC APIs FOR EVENTING AND STREAMING

![](bbox=[0.13, 0.116, 0.765, 0.473])

**Figure 9.5** A fanout topic that dispatches each message to all subscribed message receivers.

# A Note about Message Broker Terminology

The terms queues and topics used in this chapter, are commonly found in resources about distributed messaging. Keep in mind that some vendors, such as RabbitMQ, offer more distinct options for topics. Options range from general broadcasting of messages, termed fanout, to selective broadcasting, which they term topics. Be sure to read the vendor documentation carefully to understand the terminology vendors prefer to achieve the desired goals.

# Message Streaming Fundamentals

Message brokers are often transactional and are designed to manage the state of durable subscriptions for failure recovery of offline receivers. While useful for a application and integration solutions, transactional support and other characteristics limit the scalability of traditional message brokers.

Message streaming builds on the decades of message broker expertise but shifts some responsibilities away from the server while adding new capabilities to address today's complex data and messaging needs. It uses a fanout pattern for push