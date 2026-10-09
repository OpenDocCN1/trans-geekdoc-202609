![](bbox=[0.15, 0.12, 0.85, 0.39])

![](bbox=[0.15, 0.4, 0.65, 0.66])

# Figure 3.10 ◆ rdt2.0—A protocol for a channel with bit errors

(the notation rdt_rcv(rcvpkt) && isACK(rcvpkt) in Figure 3.10 corresponds to this event), the sender knows that the most recently transmitted packet has been received correctly and thus the protocol returns to the state of waiting for data from the upper layer. If a NAK is received, the protocol retransmits the last packet and waits for an ACK or NAK to be returned by the receiver in response to the retransmitted data packet. It is important to note that when the sender is in the wait-for-ACK-or-NAK state, it *cannot* get more data from the upper layer; that is, the rdt_send() event can not occur; that will happen only after the sender receives an ACK and leaves this state. Thus, the sender will not send a new piece of data until it is sure that the receiver has correctly received the current packet. Because of this behavior, protocols such as rdt2.0 are known as **stop-and-wait** protocols.