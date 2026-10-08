

| | VM$_1$ | 0~21 * | 21~32 X$_3$ | 32~44 X$_5$ | 44~51 * | 51~56 X$_8$ | 56~63 X$_7$ |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| CS$_1$ | VM$_2$ | 0~18 * | 18~26 X$_4$ | 26~44 * | 44~56 * | 56~63 * | 63~70 X$_{10}$ |
| | VM$_3$ | 0~9 X$_1$ | 9~27 X$_2$ | 27~36 X$_6$ | | | |
| CS$_2$ | | | | | | | |

图 9.10 任务分配的甘特图。

最早完成时间 EFT [26, 27] 定义如下：

$EFT(X_i, VM_j) = ECT_{ij} + EST(X_i', VM_j')$

### 示例说明

按照优先级排序，图 9.5 中 DAG$_1$ 的任务顺序为 X$_1$、X$_9$、X$_2$、X$_3$、X$_6$、X$_5$、X$_7$、X$_8$、X$_7$ 和 X$_{10}$。任务对应的 ECT 值列于表 9.1 中，这些值用于将任务分配至虚拟机。在此，我们考虑两个云服务器 CS$_1$ 和 CS$_2$。CS$_1$ 包含两个虚拟机 VM$_1$ 和 VM$_2$，而 CS$_2$ 包含一个虚拟机 VM$_3$。为此，使用甘特图 [23] 来表示任务在虚拟机上的分配情况，如图 9.10 所示。对于包含 10 个任务的给定 DAG，PETS 算法生成了 70 个单位的调度长度。

## 9.8 性能分析与结果

使用两个有向图 DAG$^1$ 和 DAG$^2$（如图 9.5 和 9.11 所示），对 HEFT、CPOP、ALAP 和 PETS 四种启发式算法进行了分析。本文在前一节中讨论了六项性能指标，并将其用作比较这四种启发式算法的依据。根据各算法，在章节开头计算了 DAG$^1$ 的所有启发式算法的调度长度。其他性能指标，如效率、加速比、SLR 和资源利用率，均基于调度长度。DAG$^1$ 的成本表如表 9.10 所示 [25]。

同样，计算了 DAG$^2$ 的所有四种启发式算法的调度长度，其余指标的值也列在表格中。DAG$^1$ 和 DAG$^2$ 的 ECT 表分别如表 9.1 和表 9.11 所示，而 DAG$^2$ 的成本表如表 9.12 所示。

六项性能指标的值显示在表 9.13 中 [25]。四种启发式算法所有性能指标的图形表示如图 9.12 至 9.17 所示。

![](img/cbc35e0d02425baa6028b87d56263a7f_241_0.png)

**图 9.11** 包含 15 个任务的 DAG$_2$ 模型。

**表 9.10** DAG$^1$ 的虚拟机速率。

| 虚拟机 (VM) | VM$_1$ | VM$_2$ | VM$_3$ |
| :--- | :---: | :---: | :---: |
| 成本/单位时间 | 1.71 | 1.63 | 1.21 |

**表 9.11** DAG$_2$ 模型的 ECT [15, 27] 矩阵。

| | $X_1$ | $X_2$ | $X_3$ | $X_4$ | $X_5$ | $X_6$ | $X_7$ | $X_8$ | $X_9$ | $X_{10}$ | $X_{11}$ | $X_{12}$ | $X_{13}$ | $X_{14}$ | $X_{15}$ |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| CS$_1$VM$_1$ | 17 | 14 | 19 | 13 | 19 | 13 | 15 | 19 | 13 | 19 | 13 | 15 | 18 | 20 | 11 |
| CS$_1$VM$_2$ | 14 | 17 | 17 | 20 | 20 | 18 | 15 | 20 | 17 | 15 | 22 | 21 | 17 | 18 | 18 |
| CS$_2$VM$_3$ | 13 | 14 | 16 | 13 | 21 | 13 | 13 | 13 | 13 | 16 | 14 | 22 | 16 | 13 | 21 |
| CS$_3$VM$_1$ | 22 | 16 | 12 | 14 | 15 | 18 | 14 | 18 | 19 | 13 | 12 | 14 | 14 | 16 | 17 |

**表 9.12** DAG$^2$ 的虚拟机成本。

| 虚拟机(VM) | VM$_1$ | VM$_2$ | VM$_3$ | VM$_4$ |
| :--- | :---: | :---: | :---: | :---: |
| 成本/单位时间 | 1.72 | 1.52 | 1.69 | 1.65 |

**表 9.13** 对比结果。

| | **性能指标结果** | | | | | |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **DAG 模型** | **调度算法** | **调度长度** | **加速比** | **效率 (%)** | **SLR** | **资源利用率 (%)** | **成本/单位时间** |
| | HEFT | 73 | 1.74 | 58.00 | 1.78 | 77.12 | 258.65 |
| **DAG$^1$** | CPOP | 86 | 1.48 | 49.22 | 2.09 | 77.51 | 301.12 |
| | ALAP | 73 | 1.74 | 58.00 | 1.78 | 77.16 | 258.65 |
| | PETS | 70 | 1.81 | 60.33 | 1.71 | 80.47 | 265.39 |
| | HEFT | 152 | 1.52 | 38.00 | 1.71 | 69.73 | 702.75 |
| **DAG$^2$** | CPOP | 164 | 1.41 | 35.25 | 1.84 | 64.93 | 694.92 |
| | ALAP | 155 | 1.49 | 37.25 | 1.74 | 72.74 | 751.53 |
| | PETS | 152 | 1.52 | 38.00 | 1.71 | 65.13 | 666.43 |

![](img/cbc35e0d02425baa6028b87d56263a7f_242_0.png)

**图 9.12** 调度长度。

![](img/cbc35e0d02425baa6028b87d56263a7f_243_0.png)

**图 9.13** 加速比。

![](img/cbc35e0d02425baa6028b87d56263a7f_243_1.png)

**图 9.14** 效率。

![](img/cbc35e0d02425baa6028b87d56263a7f_243_2.png)

**图 9.15** SLR。

![](img/cbc35e0d02425baa6028b87d56263a7f_243_3.png)

**图 9.16** 资源利用率。

![](img/cbc35e0d02425baa6028b87d56263a7f_244_0.png)

**图 9.17** 成本。

## 9.9 结论

本章讨论了 HEFT、CPOP、ALAP 和 PETS 四种启发式算法。这些算法被用作标准算法，以便与任何新提出的算法进行比较。所有四种启发式算法都通过 DAG 进行了详细研究和说明，其中 DAG$^2$ 分别包含 10 个和 15 个任务。这些算法利用多种属性来确定给定 DAG 中任务的优先级。基于六项性能指标，对包含 10 个和 15 个任务的两种 DAG 分别进行了启发式算法的比较研究。

## 参考文献

- 1. Hashizume, K., Rosado, D.G., Fernández-Medina, E., Fernandez, E.B., An analysis of Security Issues for Cloud Computing. J. Internet Serv. Appl., 4, 1, 5, 1–13, 2013.
- 2. Pachghare, V.K., Cloud Computing, PHI, Delhi India, 2016.
- 3. Zhao, G., Liu, J., Tang, Y., Sun, W., Zhang, F., Ye, X., Tang, N., Cloud Computing: A Statistics Aspect of Users. First International Conference on Cloud Computing (CloudCom), Beijing, China, Springer Berlin, Heidelberg, pp. 347–358, 2009.
- 4. Zhang, S., Zhang, S., Chen, X., Huo, X., Cloud Computing Research and Development Trend. Second International Conference on Future Networks (ICFN’10), Sanya, Hainan, China, IEEE Computer Society, Washington, DC, USA, pp. 93–97, 2010.
- 5. Gary, M.R. and Johnson, D.S., Computer and Intractability: A Guide to the theory of NP Completeness, W.H freeman, San Francisco CA, 1989.
- 6. Yadav, A.K. and Mandoria, H.L., Study of Task Scheduling Algorithms in the Cloud Computing Environment: A Review. Int. J. Comput. Sci. Inf. Technol., 8, 4, 462–468, 2017.
- 7. Kaur, R. and Kaur, R., Multiprocessor Scheduling using Task Duplication Based Scheduling Algorithms: A Review Paper. Int. J. Appl. Innov. Eng. Manage., 2, 4, 311–317, April, 2013.
- 8. Chung, Y.-C. and Ranka, S., Applications and Performance Analysis of a Compile-Time Optimization Approach for List Scheduling Algorithms on Distributed Memory Multiprocessors. Supercomputing '92: Proceedings of the 1992 ACM/IEEE Conference on Supercomputing, Minneapolis, MN, USA, pp. 512–521, 1992.
- 9. Srinivas, G.N. and Musicus, B.R., Generalized Multiprocessor Scheduling for Directed Acyclic Graphs, in: Third Annual ACM Symposium on Parallel Algorithms and Architectures, pp. 237–246, 1994.
- 10. Zanywayingona, F.N. and Yang, Y., Effective Task Scheduling and Dynamic Resource Optimization based on Heuristic Algorithms in Cloud Computing Environment. KSIITrans. Internet Inf. Syst., 11, 12, 5780–5802, 2017.
- 11. Haidri, R.A., Katti, C.P., Saxena, P.C., Cost Effective Deadline Aware Scheduling Strategy For Workflow Applications on Virtual Machines in Cloud Computing. J. King Saud Univ. – Comp. Info. Sci., 32, 6, July 2020.
- 12. Kwok, Y.-K. and Ahmad, I., Static Scheduling Algorithms for Allocating Directed Task Graphs to Multiprocessors. ACM Comput. Surv., 31, 4, 1–88, December, 1999.
- 13. Sinnen, O., Task Scheduling for Parallel Systems, Wiley Interscience Pulation, Hoboken, New Jersey, 2007.
- 14. Kumar, M.S., Gupta, I., Jana, P.K., Delay-based workflow scheduling for cost optimization in heterogeneous cloud system. Tenth International Conference on Contemporary Computing (IC3), Noida, pp. 1–6, 2017.
- 15. Gupta, I., Kumar, M.S., Jana, P.K., Efficient Workflow Scheduling Algorithm for Cloud Computing System: A Dynamic Priority-Based Approach. Arab. J. Sci. Eng., 43, 12, 7945–7960, 2018.
- 16. Hwang, K., Advanced Computer Architecture: Parallelism, Scalability, Programmability, TMH Publishing Company, New Delhi, 2005.
- 17. Akbar, M.F., Munir, E.U., Rafique, M.M., Malik, Z., Khan, S.U., Yang, L.T., List-Based Task Scheduling for Cloud Computing. IEEE International Conference on Internet of Things (iThings) and IEEE Green Computing and Communications (GreenCom) and IEEE Cyber, Physical and Social Computing (CPSCCom) and IEEE Smart Data (SmartData), Chengdu, pp. 652–659, 2016.
- 18. Kalra, M. and Singh, S., A Review of Metaheuristic Scheduling Techniques in Cloud Computing. Egypt. Inform. J., 16, 3, 275–295, 2015.
- 19. Benalla, H., Ben Alla, S., Touhafi, A., Ezzati, A., A Novel Task Scheduling Approach Based On Dynamic Queues And HybrId Meta-Heuristic Algorithms for Cloud Computing Environment. Cluster Comput., 21, 4, 1797–1820, 2018.

