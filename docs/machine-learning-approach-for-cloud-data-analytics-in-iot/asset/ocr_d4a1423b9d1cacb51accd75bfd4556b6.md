![](bbox=[0.16, 0.09, 0.88, 0.2])

Figure 9.9 Gantt chart for task allocation.

# 9.7.4 Performance Effective Task Scheduling (PETS) Algorithm

PETS [21] algorithm is worked in three phases such as sorting of task level, prioritization of task, and VM selection.

First Phase: Sorting of Task Level

This phase is used to find levels with their respective tasks and it is traversed from top to bottom of the given DAG. Each level consists of multiple tasks which are independent and these tasks would be sorted and grouped as appeared in their level. For example, task level sorting of the given DAG as shown in Figure 9.5 is divided into four levels. Level_1 consists of entry task X_1, Level_2 consists of intermediate tasks X_2, X_3, X_4, X_5, X_6, and so on for the other two levels. Sorting of task level is shown in Table 9.6.

Second Phase: Prioritization of Task

This phase is used to compute the priority and assign to the tasks of the given DAG_1. There are three attributes [21] that are designed to compute the priority of the tasks and the attributes are average execution time (AET), data communication time (DCT), and predecessor task rank (PTR). Details of these attributes are given below:

AET of the task T_i is defined as by AET(X_i) = \frac{\sum_{j=1}^{m} ECT_{i,j}}{m}. For example, the AET of the tasks of the given DAG shown in Figure 9.5 and using

Table 9.6 Sorting of task level.

| Level | Task Group |
| :--- | :--- |
| 1 | {X_1} |
| 2 | {X_2,X_3,X_4,X_5,X_6} |
| 3 | {X_7,X_8,X_9} |
| 4 | {X_{10}} |