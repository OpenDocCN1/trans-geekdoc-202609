Data traffic management in AI-IoT network 167

of traffic. Congestion may be reduced by using traffic engineering, which optimizes resource allocation and makes real-time changes to traffic. To avoid overload, admission control limits the number of concurrent sessions or connections [125]. Devices may regulate transmission rates to technologies that detect and communicate congestion circumstances. Load balancing spreads traffic among many counts or servers to avoid overload. The discard policy determines which packets should be lost due to congestion. Multipath routing makes use of several pathways to distribute and safeguard traffic. Upgrading infrastructure and using new technologies to increase available bandwidth helps reduce congestion. These congestion management and mitigation measures help the network function effectively and reliably [126].

# 8.8.1 Congestion control algorithms for AI-IoT networks

Congestion control algorithms are crucial in managing network congestion in AI-IoT networks. Due to the large number of devices and the diverse traffic patterns in AI-IoT environments, traditional congestion control mechanisms may not be directly applicable [8].

Here are some congestion control algorithms designed explicitly for AI-IoT networks.

# 8.8.1.1 Random early detection

Random early detection (RED) is a commonly used congestion control algorithm that can also be adapted for AI-IoT networks. It monitors the queue length at routers and selectively drops packets when the queue exceeds a certain threshold. RED can help regulate traffic and prevent congestion by signaling the end points to reduce their transmission rates [127].

# 8.8.1.2 Congestion control for small packets

Congestion control for small packets (CCSP) is an algorithm designed to handle the unique characteristics of AI-IoT networks, which often involve small-sized packets with low data rates. To maintain fairness and prevent congestion by regulating the transmission rates of devices based on their packet sizes and delay requirements [128].

# 8.8.1.3 Adaptive beacon congestion control

Adaptive beacon congestion control (ABCC) is a congestion control algorithm designed explicitly for wireless AI-IoT networks. It utilizes periodic beacon messages exchanged between devices to estimate the congestion level in the network.