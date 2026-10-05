# Building network slice for healthcare equipment over 5G services 159

# 8.2.11.1 Key benefits of proposed system

The system overcomes the limitations and provides novelty such as:

**Real-Time Adaptability and Scalability:** The system uses mathematically modeled genetic algorithm (GA) and reinforcement learning (RL) to dynamically adjust bandwidth, latency, and security based on device data characteristics. A hybrid cloud setup using AWS microservices and containerization enables seamless scaling to meet evolving healthcare demands.

**Enhanced Security and Efficiency:** With Zero Trust Architecture and advanced IAM protocols, patient data remains secure. AI-driven analytics optimizes network slicing and resource allocation, ensuring efficient device operation and reduced downtime.

# 8.3 METHODOLOGY AND WORKING PRINCIPLE

The system is designed to optimize performance, enhance security, and ensure real-time adaptability for modern healthcare demands. Edge nodes, placed near healthcare facilities, manage latency-sensitive and data-intensive tasks, while the cloud layer handles large-scale data storage, centralized processing, and AI models. Table 8.1 outlines typical 5G use cases.

At the core of this system is the GA with RL; the orchestrator predicts network traffic, workload, and potential bottlenecks and allocates resources dynamically with each slice tailored to the specific needs of healthcare applications with these specifically modified algorithms. Security is paramount in this architecture, which integrates a Zero Trust Architecture (ZTA) alongside advanced Identity and Access Management (IAM) protocols. The core orchestrator structure of the proposed solution is given as the UML diagram, as shown in Figure 8.1.

Moreover, the proposed system includes AWS infrastructure using services like VPC, CloudWatch, and Pseudo for efficient network provisioning and monitoring. Pseudo Real-time simulated environment conditions, including spikes in telemedicine or large-scale data transfers and trials in pilot healthcare facilities confirmed its performance, consistently meeting or exceeding benchmarks for latency, throughput, resource utilization, and security, validating its readiness for large-scale deployment.

# 8.3.1 Core AI models and their working principles

+   1. Dynamic Resource Allocation: RL algorithms, particularly those based on Proximal Policy Optimization (PPO) and Deep Q-Networks (DQN), are implemented and adapt to the current state of the network, making real-time decisions on resource distribution across network slices using a reward-based system where actions lead to optimized latency, throughput, and resource utilization are positively reinforced and adjusted to demands.