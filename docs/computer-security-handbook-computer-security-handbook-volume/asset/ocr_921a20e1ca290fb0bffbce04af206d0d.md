# 5.6.4 Octets and Sequence Number.

The sequence number field value allows the receiver to put arriving TCP segments in order even if the packets carrying them arrive out of order (including when a segment is retransmitted). Sequence numbers are also used in acknowledgments, albeit indirectly. In TCP transmission, every octet that is sent, from the very first, is counted. This octet counting is used to select each segment’s sequence number.

+   - For the first segment, a random initial sequence number (ISN) is placed in the sequence number field.
+   - If the segment contains data, the number of the first octet contained in the data field is used as the segment’s sequence number.
+   - For a purely supervisory message that carries no data, such as an ACK, SYN, SYN/ACK, FIN, or RST segment, the sequence number is increased by 1 over the previous message.

One dangerous attack is TCP session hijacking, in which an attacker takes over the role of one side. This allows the hijacker to read messages and send false messages to the other side. To accomplish session hijacking, the attacker must be able to predict sequence numbers because if a segment arrives with an inappropriate sequence number, the receiver will reject it. TCP session hijacking is likely to be successful only if the initial sequence number is predictable. Few operating systems today pick initial sequence numbers in a predictable way, but predicable sequence numbers were common in earlier operating systems, some of which are still in use.

# 5.6.5 Acknowledgment Numbers.

When a receiver sends an acknowledgment, it sets the ACK bit. It also puts a value in the acknowledgment number field to indicate which segment is being acknowledged. This process is needed because the sender sends many segments and because acknowledgments may be delayed. You might think that the acknowledgment number would be the sequence number of the segment being acknowledged. Instead, it is the number of the last octet in the data field plus 1. In other words, the acknowledgment number gives the octet number of the first octet in the next segment to be sent. This seems a bit odd, but it makes certain calculations easier for the receiver.

# 5.6.6 Window Field.

Flow control limits the rate at which a side sends TCP segments. The TCP window field allows one to limit how many more octets the other side may send before getting another acknowledgment. The process is somewhat complex and has no known security implications at the time of this writing (June 2013). In acknowledgments, the ACK bit is set, and both the acknowledgment and window size fields are filled in.

# 5.6.7 Options.

Like the IPv4 header, the TCP header can have options. However, while IP options are rare and cause for suspicion, TCP uses options extensively. One common option, often sent with the initial SYN or SYN/ACK segment, is the maximum segment size (MSS) option. This gives the other side a limit on the maximum size of TCP segment data fields (not on segment sizes as a whole). The presence of TCP options, then, is not suspicious by itself.