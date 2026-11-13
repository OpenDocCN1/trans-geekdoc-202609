# ## Multilevel queue scheduling

Multilevel queue scheduling is a scheduling algorithm that partitions the ready queue into several separate queues, each with its own scheduling algorithm and priority level. Processes are permanently assigned to one of these queues based on certain characteristics, such as process type, priority or memory requirements. Each queue may use a different scheduling algorithm, such as FCFS or round robin, and the queues themselves are scheduled in a specific order, often based on priority.

In this approach, higher-priority queues are given more CPU time compared to lower-priority queues. For example, interactive processes might be placed in a high-priority queue scheduled with round robin, while batch processes are placed in a lower-priority queue scheduled with FCFS. The CPU scheduler selects processes from the highest-priority queue first, moving to lower-priority queues only when the higher-priority queues are empty.

| Advantages | Disadvantages |
| :--- | :--- |
| Flexibility in handling different types of processes | Starvation of lower-priority processes if higher-priority queues are frequently occupied |
| Prioritizes critical and interactive processes, improving responsiveness for important tasks | Complex implementation and management |
| Different scheduling algorithms can be tailored to the needs of each queue | Processes are permanently assigned to queues, which might not be optimal if their behaviour changes over time |

In this example, processes in the high-priority queue (P1 and P2) are scheduled first using round robin. Both P1 and P2 complete. The scheduler then moves to the medium-priority queue (P3), and then to the low-priority queue (P4) only when the high-priority queue does not have processes ready to run. However, it frequently checks back to the high-priority queue, which is why P2 (high) runs again after P4 (low).

| Queue priority | Process type | Scheduling algorithm | Process queue |
| :--- | :--- | :--- | :--- |
| Q1 – High | Interactive | Round robin (time quantum = 2) | P1, P2 |
| Q2 – Medium | Batch | FCFS | P3 |
| Q3 – Low | Background / idle | FCFS | P4 |

| Process | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| P1 (High) | | | | | | | | | | | | | |
| P2 (High) | | | | | | | | | | | | | |
| P3 (Medium) | | | | | | | | | | | | | |
| P4 (Low) | | | | | | | | | | | | | |

**Common mistake**

Don't forget that context switching – when the CPU switches from one task to another – can slow things down. Even though it allows for multitasking, too much switching can reduce how efficiently the system runs because the CPU spends time saving and restoring tasks.