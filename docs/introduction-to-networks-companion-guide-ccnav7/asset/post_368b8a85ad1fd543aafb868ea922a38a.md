
The 6 bits in the Control Bits field of the TCP segment header are also known as *flags*. A flag is a bit that is set to either on or off.

The six control bits flags are as follows:

- **URG:** Allows an application to process this data immediately.
- **ACK:** Acknowledgment flag used in connection establishment and session termination
- **PSH:** Push function
- **RST:** Flag used to reset the connection when an error or timeout occurs
- **SYN:** Flag used to synchronize sequence numbers used in connection establishment
- **FIN:** Flag indicating no more data from sender; used in session termination

Search the internet to learn more about the PSH and URG flags.

**Video—TCP 3-Way Handshake (14.5.5)**
Refer to the online course to view this video.

**Check Your Understanding—TCP Communication Process (14.5.6)**
Refer to the online course to complete this activity.

## Reliability and Flow Control (14.6)

Reliability and flow control are two of the main features of TCP that are not present in UDP.

### TCP Reliability—Guaranteed and Ordered Delivery (14.6.1)

The reason that TCP is the better protocol for some applications is because, unlike UDP, it re-sends dropped packets and numbers packets to indicate their proper order before delivery. TCP can also help maintain the flow of packets so that devices do not become overloaded. This section covers these features of TCP in detail.

There may be times when TCP segments do not arrive at their destination. Other times, TCP segments might arrive out of order. For the original message to be understood by the recipient, all the data must be received, and the data in the segments must be reassembled into the original order. Sequence numbers are assigned in the header of each packet to achieve this goal. The sequence number is the first data byte of a TCP segment.

During session setup, an initial sequence number (ISN) is set. This ISN represents the starting value of the bytes that are transmitted to the receiving application. As data is transmitted during the session, the sequence number is incremented by the number of bytes that have been transmitted. This data byte tracking enables each segment to be uniquely identified and acknowledged. Missing segments can then be identified.

The ISN does not begin at 1 but is effectively a random number. This prevents certain types of malicious attacks. For simplicity, we use an ISN of 1 for the examples in this chapter.

Segment sequence numbers indicate how to reassemble and reorder received segments, as shown in Figure 14-23.

![](img/e71dc48d3ae3db3394e5857ab2acae75_523_0.png)

### Figure 14-23 TCP Segments Are Reordered at the Destination

The receiving TCP process places the data from a segment into a receiving buffer. Segments are then placed in the proper sequence and are passed to the application layer when reassembled properly. Any segments that arrive with sequence numbers that are out of order are held for later processing. Then, when the segments with the missing bytes arrive, the segments are all processed in order.

### Video—TCP Reliability—Sequence Numbers and Acknowledgments (14.6.2)

Refer to the online course to view this video.

### TCP Reliability—Data Loss and Retransmission (14.6.3)

No matter how well designed a network is, data loss occasionally occurs. TCP provides methods of managing segment losses. Among these is a mechanism to retransmit segments for unacknowledged data.

The sequence (SEQ) number and acknowledgment (ACK) number are used together to confirm receipt of the bytes of data contained in the transmitted segments. The SEQ number identifies the first byte of data in the segment being transmitted. TCP uses the ACK number sent back to the source to indicate the next byte that the receiver expects to receive. This is called *expectational acknowledgment*.

Prior to later enhancements, TCP could only acknowledge the next byte expected. For example, in Figure 14-24, using segment numbers for simplicity, Host A sends segments 1 through 10 to Host B. If all the segments arrive except for segments 3 and 4, Host B replies with an acknowledgment specifying that the next segment expected is segment 3. Host A has no idea if any other segments arrived or not. Therefore, Host A re-sends segments 3 through 10. If all the re-sent segments arrive successfully, segments 5 through 10 are duplicates. This can lead to delays, congestion, and inefficiencies.

**Note**
For simplicity, segment numbers are used here instead of the byte numbers.

![](img/e71dc48d3ae3db3394e5857ab2acae75_524_0.png)

Figure 14-24 Data Retransmission

Host operating systems today typically employ an optional TCP feature called *selective acknowledgment (SACK)*, which is negotiated during the three-way handshake. If both hosts support SACK, the receiver can explicitly acknowledge which segments (bytes) were received, including any discontinuous segments. The sending host therefore needs to retransmit only the missing data. For example, in Figure 14-25, again using segment numbers for simplicity, Host A sends segments 1 through 10 to Host B. If all the segments arrive except for segments 3 and 4, Host B can acknowledge that it has received segments 1 and 2 (ACK 3) and selectively acknowledge segments 5 through 10 (SACK 5-10). Host A needs to re-send only segments 3 and 4.

![](img/e71dc48d3ae3db3394e5857ab2acae75_525_0.png)

### Figure 14-25 Selective Acknowledgment

### Note

TCP typically sends ACKs for every other packet, but other factors beyond the scope of this section may alter this behavior.

TCP uses timers to know how long to wait before re-sending a segment.

Video

### Video—TCP Reliability—Data Loss and Retransmission (14.6.4)

Refer to the online course to view this video. Play the video and click the link to download the PDF file. The video and PDF file examine TCP data loss and retransmission.

### TCP Flow Control—Window Size and Acknowledgments (14.6.5)

TCP provides mechanisms for flow control, which has to do with the amount of data the destination can receive and process reliably. Flow control helps maintain the reliability of TCP transmission by adjusting the rate of data flow between source and destination for a given session. To accomplish this, the TCP header includes a 16-bit field called the *window size*.

Figure 14-26 shows an example of window size and acknowledgments.

![](img/e71dc48d3ae3db3394e5857ab2acae75_526_0.png)

Figure 14-26 TCP Window Size Example

The window size determines the number of bytes that can be sent before an acknowledgment should be expected. The acknowledgment number is the number of the next expected byte.

The window size is the number of bytes that the destination device of a TCP session can accept and process at one time. In this example, the PC B initial window size for the TCP session is 10,000 bytes. Starting with the first byte, byte number 1, the last byte PC A can send without receiving an acknowledgment is byte 10,000. This is known as the *send window* of PC A. The window size is included in every TCP segment, so the destination can modify the window size at any time, depending on buffer availability.

The initial window size is agreed upon when the TCP session is established during the three-way handshake. The source device must limit the number of bytes sent to the destination device, based on the window size of the destination. Only after the source device receives an acknowledgment that the bytes have been received can it continue sending more data for the session. Typically, the destination does not wait for all the bytes for its window size to be received before it replies with an acknowledgment. As the bytes are received and processed, the destination sends acknowledgments to inform the source that it can continue to send additional bytes.

For example, it is typical that PC B would not wait until all 10,000 bytes have been received before sending an acknowledgment. This means PC A can adjust its send window as it receives acknowledgments from PC B. As shown in Figure 14-26, when PC A receives an acknowledgment with the acknowledgment number 2921, which is the next expected byte, the PC A send window increments 2920 bytes. This changes the send window from 10,000 bytes to 12,920. PC A can now continue to send up to another 10,000 bytes to PC B, as long as it does not send more than its new send window of 12,920.

A destination sending acknowledgments as it processes bytes received and the continual adjustment of the source send window is known as *sliding window*. In the previous example, the send window of PC A increments, or slides over, another 2921 bytes, from 10,000 to 12,920.

If the availability of the destination's buffer space decreases, the destination may reduce its window size to inform the source to reduce the number of bytes it should send without receiving an acknowledgment.

### Note

Devices today use the sliding window protocol. The receiver typically sends an acknowledgment after receiving every two segments. The number of segments received before acknowledgment occurs may vary, however. The advantage of the sliding window is that it allows the sender to continuously transmit segments, as long as the receiver is acknowledging previous segments. The details of the sliding window are beyond the scope of this book.

### TCP Flow Control—Maximum Segment Size (MSS) (14.6.6)

In Figure 14-27, the source is transmitting 1460 bytes of data within each TCP segment. This is typically the maximum segment size (MSS) that the destination device
