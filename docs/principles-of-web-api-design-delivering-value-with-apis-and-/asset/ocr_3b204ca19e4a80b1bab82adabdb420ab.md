# Messaging Styles and Locality

An application or service may choose from one or more styles of messaging:

+   - Synchronous messaging involves the message producer sending a message and waiting while the receiver processes it and returns a reply.

+   - Asynchronous messaging allows the message producer and receiver to operate in their own time rather than waiting upon one another. The message producer sends the message to the receiver, but the receiver may not be able to process it immediately. The message producer is free to perform other tasks while waiting for a reply from the message receiver.

In addition, messages may be exchanged across different localities:

+   - Local messaging assumes messages are sent and received within the same process. As such, the programming language and host will be the same as well. The Smalltalk programming language was built to support sending and receiving messages between objects. Actor-based frameworks, such as Vlingo¹ also support this. A “mailbox” sits between the code that produces the message and the code that will process the message. The consumer code processes each message as soon as possible, sometimes using threads or dedicated CPU cores to process multiple messages in parallel.

+   - Interprocess messaging exchanges messages between separate processes but on the same host. Examples include UNIX sockets and dynamic data exchange (DDE).

+   - Distributed messaging involves two or more hosts for messaging. Messages are transmitted over a network using the desired protocol. Examples of distributed messaging include message brokers using Advanced Message Queuing Protocol (AMQP), Message Queuing Transport (MQTT), SOAP-based web services, REST-based APIs, and so on.

The combination of synchronous and asynchronous messaging styles, along with the locality of the messaging, determines the possibilities of a message-based solution.

> ¹ https://vlingo.io