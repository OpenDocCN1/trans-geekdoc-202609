# 6.3.2 Nature of Data

This category outlines the characteristics of dataset formats and the inclusion of metadata.

+   1. **Metadata:** Understanding packet-based or flow-based network traffic can be difficult for external analysts. To enhance clarity, datasets should include metadata that provides contextual details about elements such as network topology, IP addresses, and attack scenarios. This attribute indicates whether a dataset contains such additional descriptive information to support analysis.
+   2. **Format:** Intrusion detection datasets come in different formats, generally classified into three main types. Flow-based traffic (e.g., NetFlow) retains only metadata related to network connections. Packet-based traffic (e.g., PCAP) captures network activity along with payload details. Additionally, some datasets combine flow-based data with attributes derived from packet-level traffic or host-based log files to provide enhanced insights.
+   3. **Anonymity:** Due to privacy concerns, intrusion detection datasets are often not publicly released or may be provided in an anonymized format. This attribute specifies whether data anonymization has been applied and which elements are affected. A value of “none” indicates that no anonymization is present, while “yes (IPs)” means IP addresses have been altered or removed. Similarly, “yes (payload)” signifies that payload information has been obscured or excluded from packet-based traffic to protect sensitive data.

# 6.3.3 Data Volume

This category defines datasets based on their size and the time span they cover.

+   1. **Count:** This property represents the size of the dataset, which can be expressed as its physical size in gigabytes (GB) or as the number of flows, packets, or data points it contains.
+   2. **Duration:** To capture periodic patterns, such as differences between daytime and nighttime or weekdays and weekends [11], datasets should span a significant time frame. The duration property specifies the time period over which the network traffic was recorded.

# 6.3.4 Recording Environment

This section defines the network environments and circumstances in which datasets are obtained.

+   1. **Kind of Traffic:** This property specifies the origin of the network traffic, categorized as real, emulated, or synthetic. “Real” traffic is collected from