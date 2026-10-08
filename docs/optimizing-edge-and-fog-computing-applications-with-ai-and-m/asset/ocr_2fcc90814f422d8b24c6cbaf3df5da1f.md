# 9.5.3 Deployment

# 9.5.3.1 Overview

After training, the DRL model is deployed across edge nodes, where it dynamically schedules tasks in real time. The model continuously improves as it interacts with new data, adapting to changing workloads, resource availability, and environmental conditions.

# 9.5.3.2 Steps in Deployment

+   - **Model Distribution** – The trained DRL model is either deployed directly on edge nodes or in a hybrid setup (partially on the cloud, partially on the edge).
- **Real-Time Decision-Making** – The model schedules tasks dynamically on real-time system states.
- **Continuous Learning and Fine-Tuning** – Edge nodes periodically update the continuous model using new data from ongoing operations, ensuring improved performance over time.

# 9.5.3.3 Deployment Strategies

# Table 9.3 Different Deployment Strategies

| Strategy | Description | Best Use Case |
|---|---|--|
| On-Device Deployment | DRL model runs locally on edge nodes | Applications requiring ultra-low latency, such as autonomous vehicles |
| Cloud–Edge Hybrid Deployment | Model runs partially in the cloud and partially on the edge | Systems balancing computational efficiency and response time, such as smart grids |
| Federated Learning Deployment | Edge nodes train their own models and periodically update a global model | Privacy-sensitive applications like personalized healthcare |

# 9.5.3.4 Example: Autonomous Vehicles

In self-driving cars, onboard edge devices sensor data from cameras, LiDAR, and radar to make real-time driving decisions.

+   - The DRL scheduler decides which computations should be processed locally (e.g., obstacle detection and lane changes) and which can be offloaded to nearby edge servers (e.g., high-definition map updates).
- An FL approach allows multiple vehicles to collaboratively train a shared DRL model, improving overall road safety without sharing sensitive user data as shown in Table 9.3.