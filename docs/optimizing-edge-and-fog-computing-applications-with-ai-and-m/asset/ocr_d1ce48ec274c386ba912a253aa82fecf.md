+   * Data Privacy Concerns: Industrial and enterprise data often contain sensitive information that organizations are unwilling or unable to share due to regulatory and competitive constraints.

+   * High Data Transmission Costs: Continuously sending large volumes of sensor and log data to a central location increases bandwidth usage and storage costs.

+   * Scalability Limitations: As the number of connected devices grows, the computational and network burden on central servers becomes unsustainable.

To address these issues, Federated Machine Learning (FML) [1] has emerged as a promising alternative. FML enables multiple edge devices, such as industrial Internet of Things (IoT) sensors, manufacturing robots, and predictive maintenance systems, to collaboratively train a shared ML model without exchanging raw data. Each device trains a local model using its own data and only shares updates (e.g., gradients or weights) with a central server or aggregator, ensuring data privacy while maintaining accuracy.

One of the keys in FML-based predictive maintenance is aggregating the locally trained models from different devices effectively. The choice of aggregation strategy significantly impacts the final model's performance, robustness, and adaptability to heterogeneous data distributions across different devices.

This document explores various aggregation strategies used in FML for collaborative predictive maintenance, analyzing their strengths, limitations, and applicability in real-world industrial environments. By selecting an appropriate aggregation approach, organizations can enhance the accuracy, reliability, and efficiency of PdM solutions while maintaining data security and minimizing communication overhead.

# 7.2 Challenges in Federated Predictive Maintenance

While FML [2] offers a decentralized approach to predictive maintenance, its implementation comes with several challenges that must be addressed to ensure effective model training and deployment. These challenges stem from industrial constraints such as data security, network limitations, and the variability in sensor-generated data across different machines.

# 7.2.1 Data Privacy and Security

One of the primary motivations for using FML in predictive maintenance is the need to preserve data privacy and security. Industrial environments generate vast