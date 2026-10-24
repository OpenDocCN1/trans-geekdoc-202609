Totem consists of the following protocols and the flow control mechanism to ensure high throughput under heavy load:

+   - Total ordering protocol: This protocol is used to totally order broadcast messages and ensure reliable delivery of these messages during normal operation.
+   - Membership protocol: This protocol is used to handle the failure of nodes and the addition of new nodes to the system. The outcome of the membership protocol is a new logical ring imposed on the nodes in the membership and a distinct leader.
+   - Recovery protocol: This protocol is used to deliver as many messages as possible in a total order while ensuring virtual synchrony during recovery.
+   - The flow control mechanism: This mechanism controls the number of messages that a node can send during each token possession such that no node is overwhelmed by the messages broadcast.

# 5.3.1 Total Ordering Protocol

The total ordering protocol provides two types of message delivery services:

+   - Agreed delivery: This is a form of nonuniform total ordering. A node can deliver a broadcast message as soon as it has delivered all messages that are ordered ahead of the message. At the time of the delivery, there is no guarantee that other nodes have received the message.
+   - Safe delivery: Safe delivery ensures uniform total ordering. A node can deliver a broadcast message only if it has learned that all other nodes in the membership has received the same message and all previously ordered messages.

The total ordering protocol involves two types of messages: regular message that contains the application payload to be reliably totally ordered, and a regular token message that contains important control information for total ordering.

In Totem, a node gains the privilege for broadcasting messages with a sender determined total order when it receives a special control message that carries a logical regular token. For convenience, we simply refer to the special control message as regular