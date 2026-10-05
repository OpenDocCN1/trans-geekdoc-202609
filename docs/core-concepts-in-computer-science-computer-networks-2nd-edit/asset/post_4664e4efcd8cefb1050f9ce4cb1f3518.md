
![](img/f7819d05465fc14719b3ebbba980271a_270_0.png)

So, by now it should be clear, if I was the only guy using the Internet, things would be great! (apart from being lonely would suck). I would send/receive my packets at a nice rate, devices could store-and-forward them without any errors (as long as my sending/receiving rate would not surpass the underlying end-to-end bandwidth.

However the reality is very different from this - there is a lot of competition for bandwidth, which ends up creating unintended effects on the network such as packet loss and latency. Now, I'm sure you're wondering, can we do better at scaling network communications? Turns out we can.

## Network coding "back-to-basics"

Network coding was firstly described at the turn of the century. This was easily illustrated by the (now) well-known butterfly network example.

![](img/f7819d05465fc14719b3ebbba980271a_270_1.png)

Suppose we have a network as illustrated above. We have a source node (e.g. server) that is trying to send information (two packets) to two destination nodes (e.g. two mobile devices) - this is a typical multicast example.

In a store-and-forward network, you would send packets 1 and 2 over possible routes and the network to handle the delivery of both packets to each receiving nodes. We can see that packet 1 could reach the destination node 1 via route s -> r1 -> d1. Similarly, packet 2 could reach destination node 2 via route s -> r2 -> d2. However, for the destination node 1 to get packet 2, we would need to rely on node r3 to send it to the destination node. Likewise, to deliver packet 1 to destination node 2, we would rely on r3 to send it to the destination node. This makes node r3 a bottleneck.

In a coded network, the flow of information would be very similar. However, the data flowing through the network would be substantially different. What network coding proposes is nodes in a network can mix packets together (e.g. creating a packet that contains the XOR of multiple packets) and send these packets to the next node. This next node could again mix the packets it receives and send them to the next node. The process repeats until packets have reached their destination.

What changed? Well, some relevant things. First, nodes in the network do not store-and-forward anymore but rather operate over the packets they receive, generating coded packets (the mixed packets). Second, the destination nodes do not receive the data packets as they were originally generated (now they receive coded packets!), so destination nodes must be able to “decode” these packets. How would they do that, may you ask? Let's go for an example.

In algebraic formulations of network codes (e.g. linear network codes), coded packets are generated as linear combinations of packets (coded packets are of the form p=al1 + al2 + ... + an, where the a's are called coding coefficients, p's are data packets and n is the total number of packets we're mixing). Our goal is to recover p1, p2, ..., pn. So, what we need to do is to get enough packets, that we can solve a system of linear equations. If you remember from your algebra classes, this amounts to receiving n linearly independent combinations of packets (spoiler alert: this means that the way you choose your coefficients is really important to achieve high efficiency).

So, let's get back to our butterfly network. How would the information flow through the network? Well, exactly in the way we are. Now, how would the bottleneck r3 generate coded packets?

So instead of using two-time slots to send packets 1 and 2, node r3 can combine these two packets together and send this linear combination to the next node. The node r4 sends this coded packet to destination nodes d1 and d2.

What happens at node d1? Well, it has received two packets: packet 1 via the route s -> r1 -> d1 and packet 3 (which contains packets 1 and 2) via the route s -> r4 -> d1. Since d1 received two linearly independent packets, it can now decode packets 1 and 2 by solving the following system of equations:

![](img/f7819d05465fc14719b3ebbba980271a_272_0.png)

p1 = p1
p2 = p3 + p1

We save a time slot by allowing intermediate nodes to code these packets.
Hopefully, at this point, you’re convinced that network coding can effectively increase network throughput.

You may (understandably) be worried that this would only happen in multicast scenarios. No to worry, in unicast scenarios network coding can also increase network throughput. 

Consider the following scenario: source node s1 wants to send packet 1 to destination d2 and source node s2 wants to send packet 1 to destination node d1. There is no direct route s1 → d2 nor s2 → d1. In a store-and-forward network, r3 need to make two transmissions packets 1 and 2 would be sent in different time slots. However, if we allow r3 to encode packets, we could benefit from the direct link between s1 → d1 and s2 → d2 to send information that would allow r3 to send single packet. If s1 send packet 1 to d1 and s2 send packet 2 to d2, then r3 may only send the combination of these packets onwards, as both destination nodes would be able to recover their packet from the coded packet and the other packet received from a source node.

## 262
Core Concepts in Computer Science: Computer Networks

![](img/f7819d05465fc14719b3ebbba980271a_273_0.png)

That's beautiful, but it seems that you're using a simple error correction code over a network

Well, there's a reason you feel this way. What network coding does is very similar to an error-correcting code. However, the properties of the network code are fairly different from your traditional error-correcting code.

Point-to-point communication, also known as P2P communication, is a type of communication where data is exchanged directly between two specific endpoints or nodes without involving any intermediate devices or additional participants.

Keep in mind that error-correcting codes are designed for point-to-point communications (check this video if the above does not ring a bell). They do not care at all about the network. Data is encoded at the source, replayed at intermediate nodes, and decoded at the destination. Parity bits are added to the original data stream to allow for recovering any bit flips or erasures (see the illustration below).

![](img/f7819d05465fc14719b3ebbba980271a_273_1.png)
Message Bits | Parity Bits
1 0 1 0

![](img/f7819d05465fc14719b3ebbba980271a_273_2.png)

In network coding, however, intermediate nodes operate over the packets, generating coded packets (the mixed packets). This is because the because each hop is a link with some loss probability. This parameterization of error-correcting codes is hard to generalize. You can have low overhead and small error-correcting capabilities or you have higher overhead, recover everything, but suffer the efficiency of sending more data than needed. When thinking about the multiple links in a network, the underlying concept of error-correcting codes just does not fit. Your code can be very efficient over one link but very inefficient over the other (not even thinking about the variability of a single link).

On the other hand, the concept proposed by network coding abstracts from all of this. you just send packets and the receiver needs to collect enough packets on its end to recover the original data. So you don't necessarily need to parameterize for a specific link error rate - although you have to design your code to be efficient in terms of generating linearly independent combinations, i.e. you have to worry about every transmission useful to the client, but that would take another look.

So, bottom line, network codes serve a different purpose than error-correcting codes and should be designed based on different criteria. But one does not replace the other!

## Network Coding Bring to the Table

Well, let us some of the other benefits of network coding:

- Latency: network coding enables low latency communication by the simple fact that it does not need to rely on ARQ systems. Store-and-forward systems generally rely on ARQ, and therefore the sender needs to wait for feedback to be able to send new data (it needs to know if and what packets were lost). Coding solutions do not have this constraint. They can recover from packet loss even without knowing which particular packet was lost - “any"

![](img/f7819d05465fc14719b3ebbba980271a_274_0.png)
