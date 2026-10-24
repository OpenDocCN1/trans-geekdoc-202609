node retransmits the token to the next node (this implies that the node must keep a copy of the last token it has transmitted).

To make it possible to distinguish the expected regular token from a retransmitted one, the token includes the filed token_seq and each node uses a local variable my_token_seq. For each new regular message sent, a node increments the token.token_seq field by one and sets my_token_seq to token.token_seq (if a node has no new message to send, it nevertheless still increments token.token_seq and sets my_token_seq to token.token_seq before forwarding the token to the next node). Therefore, if the token is not lost, when a node receives a new regular token, token.token_seq must be greater than my_token_seq, and when it receives a retransmitted token, token.token_seq must be smaller or equal to my_token_seq. Hence, a node discards a regular token received if token.token_seq is smaller or equal to my_token_seq.

# 5.3.1.4 Examples

Here we show several examples on how a node updates its my_aru low watermark, and how the aru field may be changed during a token rotation. These issues are critical to understand when a message can be delivered in safe order, and hence, can be garbage collected.

+   EXAMPLE 5.5
+   
+   *Receiving an originally transmitted regular message.* If the message is a first transmission by the message's originator, there are two scenarios:

+   The most straightforward scenario is when a node has received all previously broadcast messages and just received the next expected regular message. For example, if the last message that the node received carries a sequence number 100, the local variable at the node my_aru is set to 100. When a message with sequence number 101 arrives at the node, it is the next expected message and hence, the node updates its my_aru variable to 101.

+   The node has a hole in its received message queue, i.e., the sequence number of the message is not equal to my_aru + 1. The message is an out-of-ordered message and stored in the received message queue. The local variable my_aru is