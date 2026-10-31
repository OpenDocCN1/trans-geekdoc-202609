
Table 1.2 Simulation configuration setup details

|  |  |  |
|---|---|---|
| Total Virtual machines (VMs) | Cloud | [15,20,25] |
| Computing power (MIPS) |  | [2000:4000] |
| RAM (MB) |  | [5000:20000] |
| Bandwidth (Mbps) |  | [512:4096] |
| Total VMs | Fog | [10,15,20] |
| Computing power (MIPS) |  | [2000:4000] |
| RAM (MB) |  | [250:5000] |
| Bandwidth (Mbps) |  | [128:1024] |

computer equipped with an Intel Core i7-8550U CPU, which possesses 8 cores clocked between 1.80 and 2.0 GHz. Supported by 16 GB of RAM and operating on the Windows 10 OS, this hardware configuration facilitated efficient execution and evaluation of the algorithms, ensuring robustness and reliability in analyzing TS strategies within cloud-fog computing contexts. The investigation into algorithmic performance and deployment strategies was thoroughly validated using the CloudSim 3.0.3 simulator, extensively integrated with Java programming, to replicate cloud-fog computing scenarios. The experimentation took place on a personal computing platform featuring an Intel Core i7-8550U CPU, boasting 8 cores with clock speeds ranging from 1.80 to 2.0 GHz. Supported by 16 GB of RAM and operating on the Windows 10 OS, this hardware configuration enabled rigorous evaluation of the algorithms, ensuring their effectiveness and dependability in orchestrating TS mechanisms within cloud-fog computing environments (Table 1.2).

In configuring the simulations, a custom-developed cloud-fog computing simulator was employed, offering a sophisticated framework for replicating dynamic TS scenarios. The simulator, implemented in CloudSim [24], enables the emulation of diverse network topologies, task workloads, and resource characteristics typical of cloud-fog environments. Key configuration details, including network topology, workload generation patterns, resource heterogeneity, and algorithmic parameters, were carefully chosen to ensure fidelity to real-world conditions. Through this comprehensive simulation setup, we aimed to delve into the intricacies of TS optimization within CFC environments and provide insights into the performance of CSO in addressing these challenges.

### 1.4.1.1 Task completion time

Our proposed CSOA demonstrates superior performance compared to traditional approaches such as Ant Colony Optimization (ACO), Particle Swarm Optimization (PSO), and harmony search optimization (HSO)

![](img/6bf6d18cae16ff5abc8a617b617c781f_28_0.png)

Figure 1.3 Calculation of task completion time.

when evaluated in terms of task completion time. Through extensive simulations and benchmarking, CSOA consistently outperforms these conventional algorithms by effectively leveraging the exploratory and exploitative capabilities inherent in the cuckoo search algorithm. By intelligently balancing exploration and exploitation, CSOA exhibits a remarkable ability to converge toward near-optimal TS solutions swiftly, thereby minimizing task completion time and enhancing overall system efficiency. Moreover, CSOA's adaptability to dynamic environments and robustness against premature convergence further solidify its superiority over ACO, PSO, and HSO, positioning it as a promising optimization technique for addressing TS challenges in CFC environments (Figure 1.3).

### 1.4.1.2 Resource utilization

Our proposed CSOA outperforms traditional methodologies such as ACO, PSO, and HSO significantly in terms of resource utilization. Through rigorous experimentation and comparative analysis, CSOA demonstrates superior efficiency in allocating tasks to available resources within cloud-fog computing environments. By leveraging the inherent exploratory and exploitative capabilities of the cuckoo search algorithm, CSOA optimally balances resource allocation, minimizing resource idle time, and maximizing utilization rates. Due to its adaptive nature, CSOA can dynamically adapt scheduling decisions according to real-time fluctuations in resource availability and workload, thereby ensuring optimal resource utilization

![](img/6bf6d18cae16ff5abc8a617b617c781f_29_0.png)

Figure 1.4 Calculation of resource utilization.

across varying operational scenarios. This characteristic positions CSOA as a resilient and potent solution for optimizing resource utilization within cloud-fog environments, surpassing the performance of ACO, PSO, and HSO in this crucial aspect of TS optimization (Figure 1.4).

## 1.4.2 Discussion

CSO demonstrates notable effectiveness in optimizing TS within cloud-fog environments. By leveraging the evolutionary principles taking cues from the brood parasitism observed in cuckoo species, CSO efficiently explores the solution space, leading to near-optimal task allocation and resource provisioning. This capability is notably apparent in its aptitude for harmonizing exploration and exploitation, leading to competitive performance regarding task completion time and resource utilization.

Moreover, when compared to other optimization techniques such as genetic algorithm (GA), PSO, and ACO, CSO often exhibits superior performance. Its ability to handle complex, nonlinear optimization problems with high-dimensional search spaces makes it well-suited for the dynamic and heterogeneous nature of CFC environments. Additionally, CSO’s simplicity and ease of implementation contribute to its appeal as a practical solution for TS optimization in CFC.

However, despite its strengths, CSO is not without limitations. One notable limitation is its sensitivity to parameter settings, including population size, discovery rate, and abandonment probability. Poorly chosen

parameter values may lead to premature convergence or suboptimal solutions, highlighting the importance of parameter tuning for optimal performance. Furthermore, CSO’s reliance on randomization and stochastic processes can result in non-deterministic behavior, making it challenging to predict its performance accurately in all scenarios.

While CSO presents a promising approach for TS optimization in CFC, further research is needed to address its limitations and enhance its scalability, robustness, and adaptability to diverse operating conditions. By exploring techniques to improve parameter-tuning mechanisms, incorporating domain-specific knowledge, and investigating hybrid optimization approaches, CSO can continue to evolve as a valuable tool for enhancing the efficiency and effectiveness of TS in CFC environments.

### 1.4.2.1 Limitations

- 1. Scalability Challenges: CSO may face scalability issues when dealing with large-scale IoT TS problems involving a high number of tasks and resources. With the escalation of the optimization problem’s size, CSO’s computational complexity could reach a point where it becomes impractical, resulting in lengthier optimization durations and heightened memory demands.
- 2. Sensitivity to Parameter Tuning: The performance of CSO relies heavily on the meticulous selection of algorithmic parameters, such as the population size, step size, and abandonment probability. Finding the optimal parameter configuration for a given IoT TS scenario can be challenging and may require extensive experimentation and fine-tuning.
- 3. Lack of Adaptability to Dynamic Environments: CSO’s effectiveness may diminish in dynamic CFC environments where task characteristics, resource availability, and network conditions are subject to frequent fluctuations. The static nature of CSO might impede its capacity to swiftly adapt to shifting environmental conditions, possibly resulting in suboptimal TS choices.
- 4. Limited Handling of Heterogeneous Resources: CSO may struggle to effectively allocate tasks in environments with heterogeneous computing resources, such as varying processing capabilities, memory capacities, and energy profiles. In such scenarios, CSO may prioritize certain resources over others, leading to uneven resource utilization and potentially degraded system performance.
- 5. Lack of Guarantees on Solution Quality: While CSO often converges to near-optimal solutions, there are no guarantees of optimality or convergence to the global optimum. Depending on the problem instance and parameter settings, CSO may converge to suboptimal solutions or become trapped in local optima, limiting its ability to find the best possible TS solution.
