
In a single packet window (also sometimes called a ping pong), the transmitter sends a packet only when the receiver has acknowledged (shown as an `ack` in the illustration) the receipt of the last packet transmitted. If the packet is not received, the receiver will not acknowledge it. On sending a packet, the sender sets a timer, normally called the `retransmit timer`; once this timer wakes up (or expires), the sender will assume the receiver has not received the packet, and resend it.

### How long should the sender wait?
There are a number of possible answers to this question, but essentially the sender can either wait a fixed amount of time, or it can set a timer based on information inferred from previous transmissions and network conditions. A simple (and naïve) scheme would be to

• Measure the length of time between sending a packet and receiving an acknowledgment, called the Round Trip Time (`RTT`, though normally written in the lowercase, so `rtt`).

• Set the `retransmit timer` to this number plus some small amount of buffer time to account for any variability in the `rtt` over multiple transmissions.

### Note
More information about various ways to calculate the `retransmit timer` are considered in [Chapter 5](#ch05.xhtml#ch05).

It is also possible for the receiver to receive two copies of the same information:

1\. A transmits a packet and sets its `retransmit timer`.

2\. B receives the packet, but

a. Is not able to acknowledge receipt because it is out of memory or is experiencing high processor utilization or some other condition.

b. Sends an acknowledgment, but the acknowledgment is dropped by a network device.

3\. The `retransmit timer` at A times out, so the sender transmits another copy of the packet.

4\. B receives this second copy of the same information.

### How can the receiver detect duplicated data?
It does seem possible for the receiver to compare the packets received to see if there is duplicate information, but this will not always work—perhaps the sender *intended* to send the same information twice. The usual method of detecting duplicate information is by including some sort of sequence number in transmitted packets. Each packet is given a unique sequence number while being built by the sender; if the receiver receives two packets with the same sequence number, it assumes the data is duplicated and discards the copies.

A window size of 1, or a ping pong, requires one round trip between the sender and the receiver for each set of data transmitted. This would generally result in a very slow transmission rate. If you think of the network as the end-to-end railroad track, and each packet as a single train car, the most efficient use of the track, and the fastest transmission speed, is going to be when the track is always full. This is not physically possible, however, in the case of a network because the network is used by many sets of senders and receivers, and there are always network conditions that will prevent the network utilization from reaching 100%. There is some balance between the increased efficiency and speed of sending more than one packet at a time, and the multiplexing and “safety” of sending fewer packets at a time (such as one). If a correct balance point can be calculated in some way, a fixed window flow control scheme may work well. [Figure 2-12](#ch02.xhtml#ch02fig12) illustrates.

![Image](graphics/02fig12.jpg)

**Figure 2-12** *An Example of Fixed Window Flow Control*

In [Figure 2-12](#ch02.xhtml#ch02fig12), assuming a three-packet fixed window:

• At `T1`, `T2`, and `T3`, A transmits packets; A does not need to wait for B to acknowledge anything to send these three packets, as the window size is fixed at 3.

• At `T4`, B acknowledges these three packets, which allows A to transmit another packet.

• At `T5`, B acknowledges this new packet, even though is it only one packet. B does not need to wait until A has transmitted three more packets to acknowledge a single packet. This acknowledgment allows A to have enough *budget* to send three more packets.

• At `T5`, `T6`, and `T7`, A sends three more packets, filling its window. It must now wait until B acknowledges these three packets to send more information.

• At `T8`, B acknowledges the receipt of these three packets.

In windowing schemes where the window size is more than one, there are four kinds of acknowledgments a receiver can send to the transmitter:

• **Positive acknowledgment:** The receiver acknowledges the receipt of each packet individually. For instance, if sequence numbers 1, 3, 4, and 5 have been received, the receiver will acknowledge receiving those specific packets. The transmitter can infer which packets the receiver has not received by noting which sequence numbers have not been acknowledged.

• **Negative acknowledgment:** The receiver sends a negative acknowledgment for packets it infers are missing, or were corrupted when received. For instance, if sequence numbers 1, 3, 4, and 5 have been received, the receiver may infer that sequence number 2 is missing and send a negative acknowledgment for this packet.

• **Selective acknowledgment:** This essentially combines positive and negative acknowledgment, as above; the receiver sends both positive and negative acknowledgments for each sequence of received information.

• **Cumulative acknowledgment:** Acknowledgment of the receipt of a sequence number implies receipt of all information with lower sequence numbers. For instance, if sequence number 10 is acknowledged, the information contained in sequence numbers 1–9 is implied, as well as the information contained in sequence number 10.

A third windowing mechanism is called sliding window flow control. This mechanism is very similar to a fixed window flow control mechanism, *except the size of the window is not fixed*. In sliding window flow control, the transmitter can dynamically modify the size of the window as network conditions change. The receiver does not know what size the window is, only that the sender transmits packets, and, from time to time, the receiver acknowledges some or all of them using one of the acknowledgment mechanisms described in the preceding list.

Sliding window mechanisms add one more interesting question to the questions already considered in other windowing mechanisms: What size should the window be? A naïve solution might just calculate the `rtt` and set the window size to some multiple of the `rtt`. More complex solutions have been proposed; some of these will be considered in [Chapter 5](#ch05.xhtml#ch05), in the discussion of the Transmission Control Protocol (`TCP`).

#### Negotiated Bit Rates
Another solution, more often used in circuit switched rather than packet switched networks, is for the sender, receiver, and network to negotiate a bit rate for any particular flow. A wide array of possible bit rates have been designed for a number of different networking technologies; perhaps the “most complete set” is for *Asynchronous Transfer Mode* (`ATM`)—look for ATM networks in your nearest networking history museum, because ATM is rarely deployed in production networks any longer. The ATM bit rates are:

• **Constant Bit Rate (CBR):** The sender will be transmitting packets (or information) at a constant rate; hence, the network can plan around this constant bandwidth load, and the receiver can plan around this constant bit rate. This bit rate is normally used for applications requiring time synchronization between the sender and receiver.

• **Variable Bit Rate (VBR):** The sender will be transmitting traffic at a variable rate. This rate is normally negotiated with several other pieces of information about the flow that help the network and the receiver plan resources, including:

• The peak rate, or the maximum packets per second the sender plans to transmit

• The sustained rate, or the rate at which the sender plans to transmit normally
