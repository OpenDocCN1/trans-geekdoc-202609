166 Artificial intelligence for intelligent systems

# 8.7.6 Flow-level monitoring

Flow-level monitoring involves analyzing network flows, representing a series of related packets between specific source and destination end points. By examining flow-level information, such as flow rate, duration, or size, congestion patterns and potential congested flows can be identified. Flow-monitoring tools or network flow analyzers can assist in flow-level congestion detection [118, 121].

# 8.7.7 Anomaly detection

Anomaly detection techniques involve identifying deviations from normal behavior, which can indicate congestion or other network issues. By establishing models of normal network behavior and comparing current observations with these models, anomalies related to congestion can be detected. Machine learning algorithms or statistical analysis can be applied for anomaly detection [118].

# 8.7.8 Real-time monitoring and alerts

Real-time monitoring of crucial congestion indicators, such as packet loss, latency, or queue lengths, can trigger alerts or notifications when congestion thresholds are exceeded. Network management systems can be configured to generate alerts, allowing network administrators to take immediate action to address congestion issues [118, 122].

# 8.7.9 Probing and active measurement

Probing techniques involve injecting traffic or specific probe packets into the network to measure performance or detect congestion. Active measurement tools can send probe packets and monitor their behavior to assess network conditions and congestion levels. Combining multiple congestion detection and monitoring techniques can provide a comprehensive view of network congestion in AI-IoT networks and enable timely responses to alleviate congestion-related issues. By leveraging these techniques, network operators can optimize network performance, improve user experiences, and ensure the efficient operation of AI-IoT applications [123].

# 8.8 CONGESTION CONTROL AND MITIGATION STRATEGIES

Network performance management and reliable data transfer rely heavily on congestion control and mitigation measures. Congestion occurs when network resources are overtaxed, which results in subpar performance, packet loss, and increased delay. There are several approaches to deal with this problem. Network workload overflow is avoided through traffic shaping, which controls data flow inside a network [124]. QoS techniques prioritize mission-critical data over other forms