
## 11.3.2 Problem formulation

The TS problem in CFC aims to efficiently allocate computational resources to execute a set of tasks while minimizing response time, maximizing resource utilization, and meeting task deadlines. Formally, let T represent the set of tasks to be scheduled, where each task t_i is characterized by its computational requirements C_i, deadline D_i, priority P_i, and sensitivity to delay. Additionally, let F denote the set of fog nodes and C represent the set of cloud data centers available in the system. The objective is to assign each task to a suitable computing resource (either fog node or cloud data center) and determine the optimal scheduling strategy to minimize overall response time and maximize resource utilization, while ensuring that all task deadlines are met.

The time complexity of the HSMAO algorithm mainly depends on the number of iterations required to converge to an optimal solution. Typically, the time complexity of HSMAO can be expressed as O(N·M), where N represents the population size and M denotes the maximum number of iterations. Additionally, the complexity of individual operations within HSMAO, such as evaluating the fitness function and updating solution vectors, may vary depending on the specific implementation details.

In the hybrid approach combining HS and Mexican Axolotl Optimization (MAO), the time complexity is influenced by the iterations performed by each algorithm and the interactions between them. Assuming N_HS and N_MAO as the population sizes for HS and MAO, respectively, and M_HS and M_MAO as the maximum number of iterations for each algorithm, the overall time complexity can be expressed as shown below. Additionally, the computational overhead incurred by the interaction between HS and MAO should also be considered in the time complexity analysis.

O((N_HS + N_MAO)·(M_HS + M_MAO)) (11.4)

### 11.3.2.1 Objective function

The objective function for TS in CFC using the HSMAO algorithm aims to minimize overall response time while maximizing resource utilization and meeting task deadlines. Mathematically, the objective function f can be defined as follows:

f = Σ_{i=1}^{n} ( w_1·R_i + w_2·U_i + w_3·E_i + w_4·(1 - D_i/C_i) ) (11.5)

where

- n is the total number of tasks.
- R_i represents the response time of task i, which is the time taken for the task to be completed.
- U_i denotes the resource utilization of the computing resource allocated to task i.
- E_i is the consumed energy of task i.
- D_i is the deadline of task i.
- C_i represents the computational requirement of task i.
- w1, w2, w3, and w4 are weighting factors that determine the relative importance of response time, resource utilization, and meeting deadlines, respectively.

The objective function aims to strike a balance between minimizing response time, resource utilization, and energy consumption, and ensuring timely completion of tasks. The weighting factors w1, w2, w3, and w4 can be adjusted based on the specific requirements and priorities of the CFC environment. Optimizing this objective function using the HSMAO algorithm will result in an efficient TS strategy that enhances system performance and meets the desired quality of service objectives.

### 11.3.2.2 Resource utilization

Resource utilization, U_i, is mathematically defined as the ratio of the computational requirement of task i, denoted by C_i, to the total available computational resource of the allocated computing resource, represented as C_total.

$U_i = \frac{C_i}{C_{total}}$ (11.6)

The above equation quantifies the proportion of the allocated computational resource utilized by task i. This ratio serves as a measure of how efficiently the computing resource is being utilized for task execution. A resource utilization value close to 1 indicates optimal utilization, where the task fully consumes the allocated resource, while a value closer to 0 suggests underutilization. Efficient resource utilization is crucial for maximizing system performance and ensuring effective allocation of computing resources in CFC environments.

### 11.3.2.3 Energy consumption

The mathematical equation for energy consumption, E_i, in CFC can be expressed as the product of the power consumption rate of the computing resource allocated to task i and the execution time of the task.

$E_i = P_i \times T_i$ (11.7)

where P_i represents the power consumption rate and T_i denotes the execution time of task i. This equation quantifies the energy consumed by task i during its execution. By considering both the power consumption rate and the execution time, the equation provides a comprehensive measure of energy consumption for individual tasks in CFC environments. Reducing energy consumption is critical for improving the sustainability and cost-effectiveness of CFC systems, making this equation valuable for optimizing energy efficiency in TS decisions.

### 11.3.2.4 Response time

The mathematical equation for response time, $R_i$, in CFC is defined as the total time taken for task $i$ to complete its execution, including both processing time and waiting time.

$R_i = W_i + T_i$ (11.8)

where $T_i$ represents the processing time of task $i$ and $W_i$ denotes the waiting time, which is the time spent in queues or waiting for resources to become available. This equation provides a comprehensive measure of the time taken for a task to be fully executed, taking into account both computational processing and queuing delays. Minimizing response time is essential for improving system performance and meeting the responsiveness requirements of applications and end-users in CFC environments. Therefore, optimizing this equation is a key objective in TS decisions to enhance overall system efficiency and user experience.

### 11.3.2.5 Proposed algorithm

The below algorithm presents the pseudo-code for the proposed HSMAO algorithm.

- **Input:** task characteristics, energy consumption, resource utilization, and response time.
- Initialize population of harmonies and axolotls.
- Evaluate fitness of each harmony and axolotl based on objective function.
- Repeat until convergence:
  Perform HS phase:
    Update harmonies using pitch adjustment and memory consideration.
    Evaluate fitness of updated harmonies.
  Perform MAO phase:
    Update axolotls using cooperation and adaptation principles.
    Evaluate fitness of updated axolotls.
  Combine harmonies and axolotls.
- Evaluate fitness of combined solutions.
- Select the best solutions for next iteration.
- Determine allocation of tasks to fog and cloud VMs based on solution obtained.
- Execute allocated tasks on respective VMs.
- Repeat scheduling process as needed to adapt to changing workload conditions.

Output: the Best solution obtained.

## 11.4 RESULTS AND DISCUSSION

### 11.4.1 Results

The results obtained from the CloudSim toolkit simulations reveal the performance metrics of VMs deployed in both cloud and fog computing environments. For cloud VMs, the total number of VMs varies from 15 to 25, with computing power ranging from 2,000 to 4,000 MIPS. RAM capacities for cloud VMs span from 5,000 to 20,000 MB, while bandwidth varies from 512 to 4,096 Mbps. Conversely, for fog VMs, the total VM count ranges from 10 to 20, with computing power and RAM capacity similar to cloud VMs, i.e., 2,000–4,000 MIPS and 250–5,000 MB, respectively. However, fog VMs exhibit lower bandwidth, ranging from 128 to 1,024 Mbps, reflecting the constraints of edge computing resources.

In our proposed approach, we compare the results obtained using the HSMAO algorithm with existing optimization algorithms including MAO, Harmony Search Optimization (HSO), and Ant Colony Optimization (ACO). Through comprehensive evaluations, we analyze various performance metrics such as response time, resource utilization, and meeting task deadlines. Our results demonstrate that HSMAO outperforms existing algorithms by efficiently allocating tasks based on their characteristics and system constraints. HSMAO effectively balances workload distribution between cloud and fog resources, optimizing resource utilization while ensuring timely task completion and meeting quality of service requirements.

### 11.4.1.1 Resource utilization

In terms of resource utilization, our proposed approach utilizing the HSMAO algorithm has yielded notably superior results when compared to existing optimization algorithms such as MAO, HSO, and ACO. Through meticulous evaluations, HSMAO has demonstrated its efficacy in optimizing resource allocation by efficiently distributing tasks across cloud and fog computing environments. By dynamically adapting to changing
