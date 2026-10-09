
## P45. Consider Figure 3.54.

Suppose that at $t_3$, the sending rate at which congestion loss next occurs drops to $0.75 \cdot W_{max}$ (unknown to the TCP senders, of course). Show the evolution of both TCP Reno and TCP CUBIC for two more rounds each (*Hint: note that the times at which TCP Reno and TCP CUBIC react to congestion loss may not be the same anymore*).

## P46. Consider Figure 3.54 again.

Suppose that at $t_3$, the sending rate at which congestion loss next occurs increases to $1.5 \cdot W_{max}$. Show the evolution of both TCP Reno and TCP CUBIC for two more rounds each (*Hint: see the hint in P45*).

## P47. Recall the macroscopic description of TCP throughput.

In the period of time from when the connection’s rate varies from $W/(2 \cdot RTT)$ to $W/RTT$, only one packet is lost (at the very end of the period).

- a. Show that the loss rate (fraction of packets lost) is equal to

$$
L = \text{loss rate} = \frac{1}{\frac{3}{8}W^2 + \frac{3}{4}W}
$$

- b. Use the result above to show that if a connection has loss rate $L$, then its average rate is approximately given by

$$
\approx \frac{1.22 \cdot MSS}{RTT \sqrt{L}}
$$

## P48. Consider that only a single TCP (Reno) connection uses one 10 Mbps link which does not buffer any data.

Suppose that this link is the only congested link between the sending and receiving hosts. Assume that the TCP sender has a huge file to send to the receiver, and the receiver’s receive buffer is much larger than the congestion window. We also make the following assumptions: each TCP segment size is 1,500 bytes; the two-way propagation delay of this connection is 150 msec; and this TCP connection is always in congestion avoidance phase, that is, ignore slow start.

- a. What is the maximum window size (in segments) that this TCP connection can achieve?
- b. What is the average window size (in segments) and average throughput (in bps) of this TCP connection?
- c. How long would it take for this TCP connection to reach its maximum window again after recovering from a packet loss?

## P49. Consider the scenario described in the previous problem.

Suppose that the 10 Mbps link can buffer a finite number of segments. Argue that in order for the link to always be busy sending data, we would like to choose a buffer size that is at least the product of the link speed $C$ and the two-way propagation delay between the sender and the receiver.

## P50. Repeat Problem 46, but replacing the 10 Mbps link with a 10 Gbps link.

Note that in your answer to part c, you will realize that it takes a very long time for the congestion window size to reach its maximum window size after recovering from a packet loss. Sketch a solution to solve this problem.

## P51. Let $T$ (measured by RTT) denote the time interval that a TCP connection takes to increase its congestion window size from W/2 to W, where W is the maximum congestion window size.

Argue that T is a function of TCP’s average throughput.

## P52. Consider a simplified TCP’s AIMD algorithm where the congestion window size is measured in number of segments, not in bytes.

In additive increase, the congestion window size increases by one segment in each RTT. In multiplicative decrease, the congestion window size decreases by half (if the result is not an integer, round down to the nearest integer). Suppose that two TCP connections, $C_1$ and $C_2$, share a single congested link of speed 30 segments per second. Assume that both $C_1$ and $C_2$ are in the congestion avoidance phase. Connection $C_1$’s RTT is 50 msec and connection $C_2$’s RTT is 100 msec. Assume that when the data rate in the link exceeds the link’s speed, all TCP connections experience data segment loss.

- a. If both $C_1$ and $C_2$ at time $t_0$ have a congestion window of 10 segments, what are their congestion window sizes after 1000 msec?
- b. In the long run, will these two connections get the same share of the bandwidth of the congested link? Explain.

## P53. Consider the network described in the previous problem.

Now suppose that the two TCP connections, C1 and C2, have the same RTT of 100 msec. Suppose that at time $t_0$, C1’s congestion window size is 15 segments but C2’s congestion window size is 10 segments.

- a. What are their congestion window sizes after 2200 msec?
- b. In the long run, will these two connections get about the same share of the bandwidth of the congested link?
- c. We say that two connections are synchronized, if both connections reach their maximum window sizes at the same time and reach their minimum window sizes at the same time. In the long run, will these two connections get synchronized eventually? If so, what are their maximum window sizes?
- d. Will this synchronization help to improve the utilization of the shared link? Why? Sketch some idea to break this synchronization.

## P54. Consider a modification to TCP’s congestion control algorithm.

Instead of additive increase, we can use multiplicative increase. A TCP sender increases its window size by a small positive constant $a$ ($0 < a < 1$) whenever it receives a valid ACK. Find the functional relationship between loss rate $L$ and maximum congestion window $W$. Argue that for this modified TCP, regardless of TCP’s average throughput, a TCP connection always spends the same amount of time to increase its congestion window size from $W/2$ to $W$.

## P55. In our discussion of TCP futures in Section 3.7, we noted that to achieve a throughput of 10 Gbps, TCP could only tolerate a segment loss probability of $2 \cdot 10^{-10}$ (or equivalently, one loss event for every 5,000,000,000 segments).

Show the derivation for the values of $2 \cdot 10^{-10}$ (1 out of 5,000,000,000) for the RTT and MSS values given in Section 3.7. If TCP needed to support a 100 Gbps connection, what would the tolerable loss be?

## P56. In our discussion of TCP congestion control in Section 3.7, we implicitly assumed that the TCP sender always had data to send.

Consider now the case that the TCP sender sends a large amount of data and then goes idle (since it has no more data to send) at $t_1$. TCP remains idle for a relatively long period of time and then wants to send more data at $t_2$. What are the advantages and disadvantages of having TCP use the $cwnd$ and $ssthresh$ values from $t_1$ when starting to send data at $t_2$? What alternative would you recommend? Why?

## P57. In this problem, we investigate whether either UDP or TCP provides a degree of end-point authentication.

- a. Consider a server that receives a request within a UDP packet and responds to that request within a UDP packet (for example, as done by a DNS server). If a client with IP address $X$ spoofs its address with address $Y$, where will the server send its response?
- b. Suppose a server receives a SYN with IP source address $X$ and, after responding with a SYNACK, receives an ACK with IP source address $Y$ with the correct acknowledgment number. Assuming the server chooses a random initial sequence number and there is no “man-in-the-middle,” can the server be certain that the client is indeed at $Y$ (and not at some other address $X$ that is spoofing $Y$)?

## P58. In this problem, we consider the delay introduced by the TCP slow-start phase.

Consider a client and a Web server directly connected by one link of rate $R$. Suppose the client wants to retrieve an object whose size is exactly equal to $15S$, where $S$ is the maximum segment size (MSS). Denote the round-trip time between client and server as RTT (assumed to be constant). Ignoring protocol headers, determine the time to retrieve the object (including TCP connection establishment) when

- a. $4S/R + RTT > 2S/R$
- b. $S/R + RTT > 4S/R$
- c. $S/R > RTT$.

---

# Programming Assignments

## Implementing a Reliable Transport Protocol

In this laboratory programming assignment, you will be writing the sending and receiving transport-level code for implementing a simple reliable data transfer protocol. There are two versions of this lab, the alternating-bit-protocol version and the GBN version. This lab should be fun—your implementation will differ very little from what would be required in a real-world situation.

Since you probably don't have standalone machines (with an OS that you can modify), your code will have to execute in a simulated hardware/software environment. However, the programming interface provided to your routines—the code that would call your entities from above and from below—is very close to what is done in an actual UNIX environment. (Indeed, the software interfaces described in this programming assignment are much more realistic than the infinite loop senders and receivers that many texts describe.) Stopping and starting timers are also simulated, and timer interrupts will cause your timer handling routine to be activated.

The full lab assignment, as well as code you will need to compile with your own code, are available at this book's Web site: www.pearsonhigher-ed.com/cs-resources.

## Wireshark Lab: Exploring TCP

In this lab, you'll use your Web browser to access a file from a Web server. As in earlier Wireshark labs, you'll use Wireshark to capture the packets arriving at your computer. Unlike earlier labs, you'll also be able to download a Wireshark-readable packet trace from the Web server from which you downloaded the file. In this server trace, you'll find the packets that were generated by your own access of the Web server. You'll analyze the client- and server-side traces to explore aspects of TCP. In particular, you'll evaluate the performance of the TCP connection between your computer and the Web server. You'll trace TCP's window behavior, and infer packet loss, retransmission, flow control and congestion control behavior, and estimated roundtrip time.

As is the case with all Wireshark labs, the full description of this lab is available at this book's Web site, www.pearsonhigher-ed.com/cs-resources.

## Wireshark Lab: Exploring UDP

In this short lab, you'll do a packet capture and analysis of your favorite application that uses UDP (for example, DNS or a multimedia application such as Skype). As we learned in Section 3.3, UDP is a simple, no-frills transport protocol. In this lab, you'll investigate the header fields in the UDP segment as well as the checksum calculation.

As is the case with all Wireshark labs, the full description of this lab is available at this book's Web site, www.pearsonhigher-ed.com/cs-resources.
