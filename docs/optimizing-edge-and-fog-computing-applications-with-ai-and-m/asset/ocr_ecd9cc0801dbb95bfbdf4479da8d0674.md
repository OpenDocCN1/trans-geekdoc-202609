computing, where resources are centralized and scalable, edge computing requires efficient and adaptive task scheduling to optimize performance while addressing several critical challenges. [2–5]

# 9.2.1 Resource Constraints

# 9.2.1.1 Limited Computational Power

Edge computing devices vary widely in terms of computational capacity, ranging from low-power IoT devices (e.g., sensors and embedded systems) to powerful edge servers. Unlike cloud data centers that have virtually unlimited processing power, edge nodes have finite CPU (Central processing unit), GPU (Graphical processing unit), and memory resources. Inefficient scheduling can lead to computational overload, reducing overall system performance and causing task execution delays.

+   - Example: In an industrial IoT (IIoT) set, smart cameras real-time video streams for defect detection may struggle to handle multiple high-resolution video feeds due to limited processing power. A poor scheduling decision could cause delays in detecting manufacturing defects.

# 9.2.1.2 Storage Limitations

Edge devices have constrained storage capacities, making it challenging to store large datasets locally. Unlike cloud environments that provide vast storage resources, edge nodes manage their data carefully, ensuring that storage limitations do not hinder processing efficiency.

+   - Solution: Effective task scheduling should include data-aware strategies, where tasks are assigned based on the availability of storage and the ability to process or offload data efficiently.

# 9.2.1.3 Power and Energy Constraints

Many edge nodes rely on battery-powered or low-energy devices, making energy efficiency a key challenge. Continuous high-power computation can drain batteries quickly, reducing the lifespan of edge devices and affecting system reliability.

+   - Example: In a remote environmental monitoring system, sensors and drones collecting climate data must balance task execution efficiency with power consumption to avoid frequent battery replacements.

+   - Solution: Energy-aware scheduling algorithms can dynamically adjust task allocation based on the energy levels of each node, ensuring that critical tasks are executed while conserving power.