There is another way to end a session or even to reject opening one. At any point, either party can send a RST (reset) message. An RST message ends the conversation abruptly. There is not even an acknowledgment. It is like hanging up in a telephone conversation.

Attackers often preface an attack by attempting to identify the IP addresses of running hosts—much like thieves casing a neighborhood. One way to do this is to send TCP SYN segments to hosts. If hosts reject the SYN segment, they often send back an RST message. As noted earlier, TCP segments are carried in the data fields of IP packets. The source IP address in the packet delivering the TCP RST segment will be that of the internal host. Whenever the attacker receives an RST segment, this verifies the existence of a working host at that packet’s IP address. Firewalls often stop RST segments from leaving a site to prevent them from reaching the attacker.

# 5.6.2 Reliability.

In addition to being connectionless or connection-oriented, protocols are either reliable or unreliable. An unreliable protocol does not detect and correct errors. Some unreliable protocols do not even check for errors. Others check for errors but simply discard a message if they find that it contains an error.

TCP is a reliable protocol. It actually corrects errors. The TCP checksum field is calculated using values from other fields. The sender places the result of its calculation in the checksum field. The receiver redo es the calculation and compares it with the transmitted value. If the receiving transport layer process finds that a message is correct (the values are the same), it sends an acknowledgment message. However, if the receiver detects an error in the TCP segment it receives (the values are different), it discards the segment and does nothing else.

How does a receiver know that there is an error in the message? The sender computes a value based on the other bits in the TCP segment (not just the header). The receiver redo es the calculation. If the two values match, the receiver sends an acknowledgment. If they do not match, the receiver merely drops the segment and does not send an acknowledgment.

If the segment arrives correctly, the original sender receives an acknowledgment. However, if the segment never arrives or is discarded because of damage, no reply is sent. If the original sender does not receive an acknowledgment in a specified period of time, it will resend the original segment. It will even use the original sequence number.

# 5.6.3 Flag Fields.

Flag field is a general name for a 1-bit field that is logical (true or false). To say that a flag field is set means that its value is 1. To say that a flag field is not set means that its value is 0.

The TCP header contains a number of flag fields. One of these is SYN. To request a connection opening, the sender sets the SYN bit. The other sends a SYN/ACK segment, in which both the SYN and ACK bits are set. Other commonly used flags are FIN, RST, URG, and PSH.

The URG flag indicates the presence of urgent data that should be handled before earlier data octets. The urgent pointer field indicates the location of the urgent data. If an application message is large, TCP will divide the application message into multiple TCP segments and send the segments individually. To help the receiving TCP process, the sending transport process may set the PSH (push) bit in the application message’s last segment. This tells the receiving transport process to push the data up to the application program immediately without buffering and delays.