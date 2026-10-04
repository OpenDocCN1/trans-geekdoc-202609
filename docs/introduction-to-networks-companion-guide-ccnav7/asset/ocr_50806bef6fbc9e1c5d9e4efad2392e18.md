Video

# Video—TCP Reliability—Data Loss and Retransmission (14.6.4)

Refer to the online course to view this video. Play the video and click the link to download the PDF file. The video and PDF file examine TCP data loss and retransmission.

# TCP Flow Control—Window Size and Acknowledgments (14.6.5)

TCP provides mechanisms for flow control, which has to do with the amount of data the destination can receive and process reliably. Flow control helps maintain the reliability of TCP transmission by adjusting the rate of data flow between source and destination for a given session. To accomplish this, the TCP header includes a 16-bit field called the *window size*.

Figure 14-26 shows an example of window size and acknowledgments.

![](bbox=[0.22, 0.42, 0.86, 0.8])

Figure 14-26 TCP Window Size Example

The window size determines the number of bytes that can be sent before an acknowledgment should be expected. The acknowledgment number is the number of the next expected byte.

The window size is the number of bytes that the destination device of a TCP session can accept and process at one time. In this example, the PC B initial window size for the