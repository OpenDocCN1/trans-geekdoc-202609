are utilized to gauge the relative importance of each factor within the objective function. The optimization of the objective function involves identifying the task allocation solution x* that either minimizes or maximizes the overall system performance based on the specified criteria.

The CSOA is employed to optimize the objective function by iteratively exploring solution spaces and adjusting task allocations to improve system performance. CSOA dynamically adjusts task allocations based on real-time conditions and constraints, aiming to converge on an optimal solution that minimizes task completion time, maximizes resource utilization, and satisfies QoS requirements. Through efficient optimization facilitated by the CSOA, IoT applications can achieve improved system efficiency, reduced response times, and enhanced user experience in CFC environments.

# 1.3.2.2 Task completion time

Task completion time is a critical metric in scheduling IoT tasks in CFC environments, as it directly impacts the responsiveness and efficiency of IoT applications. Mathematically, the task completion time T_c can be represented as the total processing time P_i for each IoT task i, considering the time taken for computation, communication, and any potential queuing delays:

$T_c = \sum_{i=1}^{n} P_i$ (1.3)

In this scenario, let us denote n as the total number of IoT tasks requiring scheduling. The processing time P_i for each task is contingent on multiple factors, such as the computational demands of the task, the processing capabilities of the allocated computing resource, and the communication latency between devices. In CFC environments, where tasks can span across various computing layers, the task completion time is impacted by the efficacy of task allocation strategies and the optimization of resource utilization.

The CSOA plays a crucial role in minimizing the task completion time by dynamically allocating tasks to suitable computing resources based on real-time conditions and constraints. By iteratively exploring solution spaces and optimizing task allocations, CSOA aims to converge on allocation strategies that minimize the overall task completion time while considering factors such as resource availability, communication latency, and QoS requirements. Through efficient TS facilitated by CSOA, IoT applications can achieve reduced response times, improved system performance, and enhanced user experience.

# 1.3.2.3 Resource utilization

Resource utilization is a critical aspect of scheduling IoT tasks in CFC environments, as it directly impacts the efficiency and cost-effectiveness of