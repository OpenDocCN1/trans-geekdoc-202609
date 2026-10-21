# 14.2.5 PERFORMANCE METRICS

Packet delivery ratio, packet loss, throughput, and average end-to-end delay were all factors taken into account in the development of this model (E2E).

# 14.2.5.1 Packet Delivery Ratio (PDR)

The PDR is the percentage of datagram created by CBR sources that were successfully delivered to the locations they were intended for. The service quality of the routing protocol is improved by a higher delivery ratio. The calculation of the Packet Delivery Ratio is shown in Equation (14.1)

Packet Delivery Ratio = Received packets / Sent packets ×100 (14.1)

# 14.2.5.2 Packet Loss

The MAC layer, as well as the network layer, may experience mobility-related packet loss (Ritu and Bhambri, 2023). Here, network layer packet loss is the main focus. When a packet reaches the network layer and a viable path to the receiver is identified. In the absence of a route, the packet is buffered. When a packet needs to be buffered but the buffer is already full, the packet is dropped. It can also be dropped when the buffer time is too long. Packet loss is determined as shown in Equation (14.2):

PER = Total Packet Sent – Total Packet received (14.2)

# 14.2.5.3 Average End to End delay

It comprises retransmission delays at the MAC, interface queue queuing, and data packet buffering during route discovery (Sangwan et al., 2021). It is the interval of time between the source node’s packet sending and the destination node’s packet receiver.

# 14.2.5.4 Throughput

The ratio of total data sent from a transmitter to a receiver is known as throughput (Ritu and Bhambri, 2022). The throughput measures how quickly the most recent communication is delivered to the recipient. Bits per second, or bytes (byte/sec or bit/sec), are used to measure throughput. In every network, a high throughput is the only option.