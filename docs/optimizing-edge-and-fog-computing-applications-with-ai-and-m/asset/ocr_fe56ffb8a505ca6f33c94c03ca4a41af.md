# 9.5 System Architecture

The deployment of DRL for task scheduling in edge computing involves multiple stages, including data collection, model training, and deployment. These steps ensure the scheduler continuously learns and adapts to dynamic workloads, resource availability, and system constraints.

# 9.5.1 Data Collection

# 9.5.1.1 Overview

For a DRL-based task scheduler to make optimal decisions, it requires extensive data from edge nodes. This helps the model understand resource availability, workload patterns, and system performance in real-world scenarios.

# 9.5.1.2 Types of Data Collected

+   1. **Resource Availability** – CPU utilization, memory usage, network bandwidth, and battery levels of edge nodes.
2. **Task Arrivals** – Task frequency, computational complexity, deadlines, and priority levels.
3. **System Performance Metrics** – Task execution time, latency, energy consumption, and successful task completion rates.

# 9.5.1.3 How Data Collection Works in Edge Environments

+   **Real-Time Monitoring** – Each edge node continuously tracks and reports its resource usage and incoming tasks.
**Historical Data Logging** – Data from past scheduling decisions is stored to train and fine-tune the DRL model.
**Cloud-Assisted Data Aggregation** – If edge nodes have limited storage, collected data can be periodically sent to a cloud server for further analysis and model training.

# 9.5.1.4 Example: Smart Healthcare System

In a remote patient monitoring system, wearable IoT devices (e.g., smartwatches and ECG monitors) continuously collect and transmit health data (heart rate, blood pressure, and oxygen levels) to edge servers.

+   - If a patient shows irregular vitals, an urgent task is scheduled for real-time processing at the nearest edge node.
- If data collection is routine, processing can be scheduled with lower priority, optimizing resource use.