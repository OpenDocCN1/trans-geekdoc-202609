token, or token for short if it is clear from the context. The membership protocol also relies on similar form of control messages, and it is referred to as commit token.

A regular message takes the form <type, v, s, i, m>, where type is either AGREED indicating the agreed delivery order, or SAFE indicating the safe delivery order, v is a view number (it is referred to as ring-id in Totem [3]), s is the (global) sequence number for the message, i is the sender node id, and m is the message payload.

A regular token message takes the form <REGULAR, v, token_seq, seq, aru, aru_id, rtr>, where token_seq is the sequence number of the token (this is needed for the receiving node to tell whether it is the original token, or a retransmitted one), seq is the high watermark of the sequence number, i.e., the largest sequence number that has been assigned to a broadcast message in the view, aru and aru_id indicate all received up to sequence number as reported by a node with id aru_id, and finally, rtr is a retransmission list.

Each node maintains two message queues, one for the regular messages received (received_message_queue), and the other for the messages that are originated at the node and are to be broadcast to other nodes (new_message_queue) The latter queue is not for the purpose of retransmission, but rather to store messages prior to the receiving of the regular token. Once the node receives a regular token and broadcasts a message in the new message queue, it transfer the message to the received message queue. A node will not delete a message in the received message queue unless it knows that the message is safe (i.e., the message has been received by all nodes in the view). A node also keeps a copy of the last regular token it has forwarded to the next node in the logical ring for retransmission and for determining whether or not a message is safe.

In addition, each node maintains the following local variables for the total ordering protocol:

+   my_aru: it stores the highest sequence number for the regular messages the node has received without a gap.

+   my_aru_count: it stores the number of times that the node has received the regular token with the same obsolete aru field (i.e., aru is smaller than the high watermark seq in the regular token).