any new algorithms using various performance metrics. All four heuristic algorithms are based on the priority attribute of the tasks and according to their priority; it will be allocated to the machines. Details of the algorithms are presented in subsequent sections.

# 9.7.1 Heterogeneous Earliest Finish Time (HEFT) Algorithm

HEFT [20] is a type of list scheduling for heterogeneous platform and it gives good performance with ideal scheduling length. It is worked in two different phase which is as follows:

First Phase: Task Priority

The order of the tasks either ascending or descending is known as the priority for any task. HEFT algorithm uses an upward rank method to compute the tasks’ priority of the given DAG. This method is also called a b-level (bottom level) attribute. It is denoted by $U^{Rank}$ and it is based on average execution time and average communication time of the tasks. The computation of the priority of the tasks will start from the exit task and move to upward of the DAG. Formally, it is expressed [20] by:

```
$$U^{Rank}(X_i)=\begin{cases} AET(X_i)+\max_{X_j\in\mathrm{SUC}(X_i)}\left(CT_{i,j}+U^{Rank}(X_j)\right)&\text{if }X_i\neq X_{exit}\\ AET(X_{exit})&\text{if }X_i=X_{exit}\end{cases}$$
```

where:

+   $X_i$ is the tasks of the given DAG
$X_{exit}$ is the last task of the given DAG
$CT_{i,j}$ is the communication time between the tasks $X_i$ and $X_j$
SUC is a finite set of immediate successor of $X_i$
AET is the average execution time of the task $X_i$ and it can be expressed by:

```
$$AET(X_i)=\frac{\sum_{j=1}^{m} ECT_{i,j}}{m}$$
```

An Illustrative Example

This section is discussed in detail elaboration of the task priority phase with an example of DAG$_1$ [14, 26, 27] as shown in Figure 9.5 and ECT