target-storage attachment. The iFCP protocol lets Ethernet-based hosts attach to FC SANs through iFCP-to-FC SAN gateways. These gateways and protocols were not widely adopted except for SAN extension because of their complexity, lack of scalability, and cost.

Now that 10 GbE is becoming more widespread, FCoE is the next attempt to converge block storage protocols onto Ethernet. FCoE takes advantage of 10 GbE performance and compatibility with existing Fibre Channel protocols. It relies on an Ethernet infrastructure that uses the IEEE Data Center Bridging (DCB) standards. The DCB standards can apply to any IEEE 802 network, but most often the term DCB refers to enhanced Ethernet. The DCB standards define four new technologies:

+   - **Priority-based Flow Control (PFC)** – 802.1Qbb allows the network to pause different traffic classes.
+   - **Enhanced Transmission Selection (ETS)** – 802.1Qaz defines the scheduling behavior of multiple traffic classes, including strict priority and minimum guaranteed bandwidth capabilities. This should enable fair sharing of the link, better performance, and metering.
+   - **Quantized Congestion Notification (QCN)** – 802.1Qau supports end-to-end flow control in a switched LAN infrastructure and helps eliminate sustained, heavy congestion in an Ethernet fabric. Before the network can use QCN, you must implement QCN in all components in the Converged Enhanced Ethernet (CEE) data path (Converged Network Adapters (CNAs), switches, and so on). QCN networks must also use PFC to avoid dropping packets and ensure a lossless environment.
+   - **Data Center Bridging Exchange Protocol (DCBX)** – 802.1Qaz supports discovery and configuration of network devices that support PFC, ETS, and QCN.

# Fibre Channel over Ethernet (FCoE)

In legacy Ethernet networks, dropped frames occur under collision or congestion situations. The networks rely on upper layer protocols such as TCP to provide end-to-end data recovery. FCoE is a lightweight encapsulation protocol and lacks the reliable data transport of the TCP layer. Therefore, FCoE must operate on DCB-enabled Ethernet and use lossless traffic classes to prevent Ethernet frame loss under congested network conditions.

FCoE on a DCB network mimics the lightweight nature of native FC protocols and media. It does not incorporate TCP or even IP protocols. This means that FCoE is a layer