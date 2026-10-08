![](bbox=[0.1, 0.11, 0.88, 0.31])

Figure 9.3 Mapping of tasks and virtual machines.

# 9.3 System Computing Model

It is represented by cloud servers which are communicated in full duplex mode using fast network. Cloud server denoted by $S_G = \{C_s\}$, where $C_s = \{C_1, C_2, \dots, C_p\}$ is a collection of finite pth cloud servers and each cloud server $C_1 = \{\text{VM}_{1,1},\dots,\text{VM}_{1,m}\}$, $C_2 = \{\text{VM}_{2,1},\dots,\text{VM}_{2,m}\}, \dots$, $C_p = \{\text{VM}_{p,1},\dots,\text{VM}_{p,m}\}$ consists of one or more VMs. Here, cloud server's VM are heterogeneous platform and they are worked at a distinct speed. The communication time between two tasks $T_i$ and $T_j$ does not consider if they are communicated in same $S_G$; otherwise, it would be considered.

Figure 9.3 showed that mapping of tasks onto corresponding cloud servers.

# 9.4 Major Objective of Scheduling

The major objective of scheduling of the workflow model is to reduce the overall execution time onto the virtual machine. It is mathematically denoted as follows:

```
Sch$_{\text{length}}$ = Minimum {CTT(Exit Task X$_{\text{exit}}$, Virtual Machine M)}
```

where CCT is completion time of the task.

# 9.5 Task Computational Attributes for Scheduling

These attributes have major role while allocation of the tasks onto VM and details of seven attributes discussed as below [26]: