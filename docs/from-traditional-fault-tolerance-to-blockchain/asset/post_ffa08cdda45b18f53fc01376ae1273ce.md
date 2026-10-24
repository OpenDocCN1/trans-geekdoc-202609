
the node assumes that the node that has id token.aru_id has failed and it initiates a view change.

- Deliver messages in safe order, if any. A regular message that should be delivered in safe order is always queued to meet the safe delivery order criteria. A node can deliver a message in safe order provided that the message's sequence number is smaller than or equal to both _last_token.aru_ and _token.aru_ (i.e., it takes two token rotations to deliver a message in safe order). Furthermore, the message is removed from the received message queue because no node would request for a retransmission of the message any more.

- Transmits the token to the next node in the logical ring, and keeps a copy of the token for retransmission and record keeping.

## 5.3.1.2 Rules on receiving a regular message

Upon receiving a regular message, a node stores the message in the received message queue unless the node has already received the message. If the message's sequence number is one higher than _my_aru, then the message can be delivered in agreed order if all previously ordered messages have been delivered, and _my_aru is incremented by one. If there are buffered messages in the received message queue and the newly received message completely fills a hole, additional messages may be delivered in agreed order and _my_aru may be continuously incremented until all messages received have been delivered, or another hole in the received message queue is encountered. There are other scenarios when a node receives a regular message and they will be discussed in the examples in Section 5.3.1.4. Note that if a previously ordered message is a safe message and has not been delivered yet, the newly received message cannot be delivered even if it is an agreed message.

## 5.3.1.3 Rules on regular token retransmission

To minimize the likelihood of triggering a view change (which is expensive) due to the loss of the regular token message, a token retransmission timer is started every time a node passes on a regular token to the next node. On a token retransmission timeout, a node retransmits the token to the next node (this implies that the node must keep a copy of the last token it has transmitted).

To make it possible to distinguish the expected regular token from a retransmitted one, the token includes the field token_seq and each node uses a local variable my_token_seq. For each new regular message sent, a node increments the token.token_seq field by one and sets my_token_seq to token.token_seq (if a node has no new message to send, it nevertheless still increments token.token_seq and sets my_token_seq to token.token_seq before forwarding the token to the next node). Therefore, if the token is not lost, when a node receives a new regular token, token.token_seq must be greater than my_token_seq, and when it receives a retransmitted token, token.token_seq must be smaller or equal to my_token_seq. Hence, a node discards a regular token received if token.token_seq is smaller or equal to my_token_seq.

## 5.3.1.4 Examples

Here we show several examples on how a node updates its my_aru low watermark, and how the aru field may be changed during a token rotation. These issues are critical to understand when a message can be delivered in safe order, and hence, can be garbage collected.

### EXAMPLE 5.5

*Receiving an originally transmitted regular message.* If the message is a first transmission by the message's originator, there are two scenarios:

The most straightforward scenario is when a node has received all previously broadcast messages and just received the next expected regular message. For example, if the last message that the node received carries a sequence number 100, the local variable at the node my_aru is set to 100. When a message with sequence number 101 arrives at the node, it is the next expected message and hence, the node updates its my_aru variable to 101.

The node has a hole in its received message queue, i.e., the sequence number of the message is not equal to my_aru + 1. The message is an out-of-ordered message and stored in the received message queue. The local variable my_aru is not changed. For example, the node has received messages with sequence numbers 99 and 101 when a message with sequence number 102 arrives, the node cannot increment its my_aru variable due to the missing message with sequence number 100. It is also possible that the node has received messages with sequence numbers 99 and 100 when a message with sequence number 102 arrives, the node cannot increment its my_aru variable either due to the same reason.

### EXAMPLE 5.6

Receiving a retransmitted regular message. There are several scenarios when a node receives a retransmitted regular message:

- The node has already received the message, i.e., the message is already in the received message queue. In this case, the message is discarded and my_aru is not changed.
- The message is new to the node, however, its sequence number of the message is greater than my_aru + 1, in which case, the message is buffered in the received message queue, but my_aru is not changed. For example, the node has already received messages with sequence numbers 99, 102 when a message with sequence number 101 is received, the node cannot change my_aru because it is still waiting for the message with sequence number 100.
- The message is new to the node, and its sequence number s is equal to my_aru + 1. Furthermore, the message with sequence number my_aru + 2 is still missing. The node increments my_aru by one and stores the message in its received message queue. If the node has already delivered all messages with a sequence number up to my_aru prior to the receiving of this message, it may deliver this message in agreed order. For example, the node has already received message with sequence numbers 99, 102 when a message with sequence number 100 arrives, the node would update its my_aru to 100, but not any further because it is still waiting for the message with sequence number 101.
- The message is new to the node with sequence number s = my_aru + 1, and the node has received a message with sequence number s = my_aru + 2, we say that the message fills a hole and my_aru will be updated accordingly. For example, the node has already received messages with sequence numbers 99, 101, 102 when the message with sequence number 100 arrives, the node would update my_aru to 102.

### EXAMPLE 5.7

We provide a number of examples to illustrate how the aru field in the regular token is updated during a token rotation. We assume a logical ring with 5 nodes N1, N2, N3, N4, and N5, and the token is passed from N1 to N2, from N2 to N3, from N3 to N4, from N4 to N5, and N5 back to N1. We further assume that N1 has just received the token. Before N1 transmits any new messages, N1.my_aru = 100, N2.my_aru = 100, N3.my_aru = 100, N4.my_aru = 100, and N5.my_aru = 99. We know token.aru must be set to 99 and token.aru_id must be set to 5 (representing N5) because N5's my_aru = 99 is smaller than token.aru = 100 when it receives the token.

N1 retransmits the message with sequence number 100 (N5 must have requested this message in the token.rtr field) and sends 3 new regular messages with sequence numbers 101, 102, and 103, respectively, during this token visit. At the end of the token visit, N1.my_aru = 103.

In one scenario, we assume that all nodes received all four messages transmitted by N1 during this token visit. It is easy to see that all other nodes will update their my_aru to 103 as well. Consequently, when N1 receives the token again, token.aru must be set to 103 (if none of the other nodes sends any new message) or higher (if some of them transmitted one or more messages).

In another scenario, if N5 does not receive the retransmitted message with sequence number 100, or missed some of the new messages, its my_aru will be smaller than 103. Hence, N5 will lower token.aru to its my_aru value and sets token.aru_id to 5 during the next token visit. Hence, when N1 receives the token again, it will notice that token.aru is lowered than that when it forwards the token the last time. In this scenario, however,
