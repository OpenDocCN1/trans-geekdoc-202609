
addressing the critical monitoring and orchestration challenges relating to slice lifecycle management.

## 8.2.7 Demonstration of Resource Orchestration Using Big Data Analytics for Dynamic Slicing in 5G Networks

Raza et al. (2018) demonstrates the center SDN/NFV-based orchestrator, which utilizes big data analytics for dynamic slicing with the goal of maximizing the use of infrastructure resources and increasing revenue for infrastructure providers.

## 8.2.8 Ovnes: Demonstrating 5G Network Slicing Overbooking on Real Deployments

L. Zanzi et al. (2018) demonstrates centralized orchestration in 5G network slicing, including slice brokerage and resource allocation challenges. The above research and development led to development of OVNES, a real-world testbed to implement a 5G Network Slice Broker for optimization-related experiments.

## 8.2.9 End-to-End 5G Service Deployment and Orchestration in Optical Networks with QoE Guarantees

Montero et al. (2018) describes an architecture for end-to-end provisioning and monitoring of 5G services in optical networks, with a focus on ensuring QoS and managing dynamic network slices with a centralized orchestrator.

## 8.2.10 Assessment of Deep Learning Methodology for Self-Organizing 5G Networks

Asghar et al. (2019) introduces an autoencoder-based deep learning approach for self-organizing networks that not only improve detection accuracy and adaptability but also facilitate smart, self-healing, and self-optimizing behavior of networks against cell outages compared to traditional methods.

## 8.2.11 Summary

Building on insights from existing literature, the proposed system addresses and overcomes limitations in current 5G network management for healthcare by integrating AI analytics, edge computing, and dynamic resource allocation.

# Building network slice for healthcare equipment over 5G services 159

## 8.2.11.1 Key benefits of proposed system

The system overcomes the limitations and provides novelty such as:

- **Real-Time Adaptability and Scalability:** The system uses mathematically modeled genetic algorithm (GA) and reinforcement learning (RL) to dynamically adjust bandwidth, latency, and security based on device data characteristics. A hybrid cloud setup using AWS microservices and containerization enables seamless scaling to meet evolving healthcare demands.

- **Enhanced Security and Efficiency:** With Zero Trust Architecture and advanced IAM protocols, patient data remains secure. AI-driven analytics optimizes network slicing and resource allocation, ensuring efficient device operation and reduced downtime.

## 8.3 METHODOLOGY AND WORKING PRINCIPLE

The system is designed to optimize performance, enhance security, and ensure real-time adaptability for modern healthcare demands. Edge nodes, placed near healthcare facilities, manage latency-sensitive and data-intensive tasks, while the cloud layer handles large-scale data storage, centralized processing, and AI models. Table 8.1 outlines typical 5G use cases.

At the core of this system is the GA with RL; the orchestrator predicts network traffic, workload, and potential bottlenecks and allocates resources dynamically with each slice tailored to the specific needs of healthcare applications with these specifically modified algorithms. Security is paramount in this architecture, which integrates a Zero Trust Architecture (ZTA) alongside advanced Identity and Access Management (IAM) protocols. The core orchestrator structure of the proposed solution is given as the UML diagram, as shown in Figure 8.1.

Moreover, the proposed system includes AWS infrastructure using services like VPC, CloudWatch, and Fargate for efficient network provisioning and monitoring. Pseudo Real-time simulated environment conditions, including spikes in telemedicine or large-scale data transfers and trials in pilot healthcare facilities confirmed its performance, consistently meeting or exceeding benchmarks for latency, throughput, resource utilization, and security, validating its readiness for large-scale deployment.

### 8.3.1 Core AI models and their working principles

- 1. Dynamic Resource Allocation: RL algorithms, particularly those based on Proximal Policy Optimization (PPO) and Deep Q-Networks (DQN), are implemented and adapt to the current state of the network, making real-time decisions on resource distribution across network slices using a reward-based system where actions lead to optimized latency, throughput, and resource utilization are positively reinforced and adjusted to demands.

### Table 8.1 5G network slicing use cases

| Type | Use case | Peak data rate | Typical data rate | Latency | Device density | Reliability | Mobility |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| eMBB | High speed data, video streaming, VR, high-capacity apps | up to 20 Gbps | 100 Mbps–1 Gbps | ~10 ms | Medium (~10,000 devices per km²) | Medium | High (up to 500 km/h) |
| mMTC | IoT devices, sensors, smart cities | Lower (~100 kbps) | Very low (~10 kbps) | ~1–10 seconds | Very high (~1,000,000 devices per km²) | Low | Low |
| uRRLC | Autonomous vehicles, remote surgery | Up to 10 Gbps | 50 Mbps–10 Gbps | <1 ms | Medium (~10,000 devices per km²) | Extremely high (99.999%) | Medium (up to 100 km/h) |

# Building network slice for healthcare over 5g services

![](img/bb14ad24e4d4babb616ee31f6e899c86_177_0.png)

Figure 8.1 Core orchestrator UML

2. Network Slicing and Virtualization: The system leverages Network Function Virtualization (NFV) and Software-Defined Networking (SDN) to implement network slicing. Each slice tailored to the specific requirements of healthcare applications.

3. Genetic Algorithms for Slice Optimization: GAs are employed to optimize network slicing by natural evolution, selecting the best-performing slices.

4. Edge Computing Integration: Edge computing nodes are deployed close to healthcare facilities to process data locally, reducing the load on central cloud and minimizing latency. The architecture is shown in Figure 8.2.

### 8.3.2 AWS architecture and cloud services

Virtual Private Cloud (VPC) enables the creation of isolated network environments, hosting multiple slices to securely segregate scenarios. The topology of a network slice for healthcare use cases is shown in Figure 8.3.

# 162 Transforming Healthcare

![](img/bb14ad24e4d4babb616ee31f6e899c86_178_0.png)

Figure 8.2 Core orchestrator UML for the solution.

AWS Identity and Access Management (IAM), a Zero Trust Security Model, ensuring authorized access from various simulated devices. AWS CloudWatch continuously monitors metrics and logs, feeding data into the AI-driven analytics platform for real-time decision-making. Detected anomalies can trigger automated responses, such as resource scaling or network slice adjustments. AWS Lambda, as part of an event-driven architecture, executes code in response to events, enabling automated adaptation without manual intervention. Elastic Kubernetes Service (EKS) manages the deployment and scaling of containerized microservices, with Docker containers orchestrated to diverse

# Building network slice for healthcare over 5G services

![](img/bb14ad24e4d4babb616ee31f6e899c86_179_0.png)

Figure 8.3 Typical topology of a network slice.

The system begins by collecting data from various healthcare devices and its characteristics, such as MRI machines and remote monitoring sensors. This data is processed at the edge, where initial analytics and decision-making take place to reduce latency and optimize bandwidth. Edge nodes communicate with the central cloud infrastructure, where complex models run to predict network conditions and manage resource allocation. Based on real-time data and predictions, the AI-driven orchestrator dynamically provisions network slices using NFV and SDN technologies. These slices for the specific requirements of different healthcare applications are made, and the RL model monitors the performance of these slices, making adjustments as network performance. The UML diagram in Figure 8.5 explains the process of the proposed system.

![](img/bb14ad24e4d4babb616ee31f6e899c86_179_1.png)

**Figure 8.5** Class diagram for HC service over 5G.
