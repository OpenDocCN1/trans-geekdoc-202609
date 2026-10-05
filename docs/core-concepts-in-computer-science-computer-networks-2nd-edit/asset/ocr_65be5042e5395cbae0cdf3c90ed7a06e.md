coded transmission can be used to recover the lost packet. So, we can build protocols that are not necessarily blocked by acknowledgments to send new data.

![](bbox=[0.168, 0.131, 0.833, 0.269])

Scalability: network coding enables more efficient usage of network resources (bandwidth), therefore allowing the network to scale better. In particular case of these are multicast/broadcast networks, where coded packets can be used by multiple users to recover from different losses, therefore making an effective use of the available bandwidth, which means more users can use the network with

![](bbox=[0.133, 0.385, 0.866, 0.833])

Network resilience: due to its design, network coding also enables a high degree of network resilience. Think about a network where a node goes down. All the packets flowing through that route will be lost, therefore forcing the sender to resend them. With network coding, all these packets