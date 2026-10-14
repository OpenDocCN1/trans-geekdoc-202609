

# 图 2.7
(a) 平均启动时间与五台虚拟机的对比。(b) 平均启动时间与十台虚拟机的对比。

# 图 2.8
(a) 平均完成时间与五台虚拟机的对比。(b) 平均完成时间与十台虚拟机的对比。

# 图 2.9
(a) 执行时间与五台虚拟机的对比。(b) 执行时间与十台虚拟机的对比。

![Image 20](index-43_1.png)

**28** ◾ ML and Optimization Models

# 表 2.1 仿真参数

| 超参数 | 值 |
| :--- | :--- |
| 隐藏层 | 1，隐藏单元 = 3，学习率 = 0.2 |
| 变异率 | 0.15 |
| 进化代数 | 100 |
| 种群大小 | 100 |
| 隐藏层数量 | 3 |
| 输出层神经元数 | 50/100 |
| 每个隐藏层神经元数 | 50 |
| 激活函数 | Leaky ReLU 激活函数 = `f(x) = { a * x if x ≤ 0, x if x > 0 }` 其中 `a = .01` |

作为性能矩阵。结果是在任务负载不断增加并按虚拟机扩展资源的情况下计算得出的（表 2.1）。

与现有方法相比，所提出的算法在网络内和故障感知环境中表现更好。

图 2.10 (a) 和 (b) 显示了以完成任务数作为性能矩阵的对比结果。结果是在任务负载不断增加并按虚拟机扩展资源的情况下计算得出的。图 2.11 (a) 和 (b) 显示了以任务失败数作为性能矩阵的对比结果，其中系统故障使用泊松分布随机发生。该性能矩阵表明，如图 2.12 所示，所提出的算法减少了网络负载和执行时间，从而提高了系统性能和服务质量，优于现有算法。

# 图 2.10
(a) 完成任务数与五台虚拟机的对比。(b) 完成任务数与十台虚拟机的对比。

![Image 21](index-44_1.png)
![Image 22](index-44_2.png)

Deep Learning-Based Optimization ◾ **29**

# 图 2.11
(a) 任务失败数与五台虚拟机的对比。(b) 任务失败数与十台虚拟机的对比。

# 图 2.12
仿真时间与五台虚拟机的对比。

显示了以毫秒为单位的仿真时间作为性能矩阵的对比结果。结果是在任务负载不断增加的情况下计算得出的，所提出的 BB–BC ANN 的性能优于传统算法，因为传统算法需要大量迭代来寻找最佳解，而所提出的算法是一个训练好的神经网络，针对某一场景只需训练一次。

**30** ◾ ML and Optimization Models

# 2.5 结论

本文提出了一种基于人脑特征和优化方法的、受天文学和神经科学启发的虚拟机分配给用户请求的方法。所提出的算法试图利用机器学习技术提高云环境的容错能力，同时提高系统性能。结果与讨论部分表明，BB–BC ANN 优于现有的元启发式技术。对所提出算法的研究是在扩展任务负载和资源的情况下进行的。

未来的工作可侧重于数据中心网络中的虚拟机分配。所提出算法的缺点是神经网络需要在一段时间后使用更新的即将到来的任务进行重新训练，以克服训练模型的衰减。然而，与现有算法的总仿真时间之和相比，该训练时间将短得多。未来，该算法可能改善云环境中的功耗和可扩展性。所提出的算法被证明在 COVID-19 形势下云环境的过载和欠载条件下表现更好，并且在欠载和负载条件下均优于任何现有算法。

# 参考文献

1. A. Beegom and M. Rajasree, A particle swarm optimization based pareto optimal task scheduling in cloud computing, in International Conference in Swarm Intelligence. Springer, 2014, pp. 79–86.
2. N. A. B. M. Shaari, T. F. Ang, L. Y. Por, and C. S. Liew, Dynamic pricing scheme for resource allocation in a multi-cloud environment, *Malaysian Journal of Computer Science*. 30(1) (2017), 1–11.
3. A. Liu and Z. Wang, Grid task scheduling based on adaptive ant colony algorithm, in International Conference on Management of e-Commerce and e-Government, 2008. ICMECG’08. IEEE, 2008, pp. 415–418.
4. C. Zhao, S. Zhang, Q. Liu, J. Xie, and J. Hu, Independent tasks scheduling based on the genetic algorithm in cloud computing, in 5th International Conference on Wireless Communications, Networking, and Mobile Computing, 2009. WiCom’09. IEEE, 2009, pp. 1–4.
5. A. Suresh and R. Varatharajan, Competent resource provisioning and distribution techniques for cloud computing environment, *Cluster Computing*. (2017), 1–8.
6. B. Kruekaew and W. Kimpan, Virtual machine scheduling management on cloud computing using artificial bee colony, In Proceedings of the International MultiConference of engineers and computer scientists, 1 (2014), 1–5.
7. Jin X, Zhang F, Wang L, Hu S, Zhou B, and Liu Z, Joint optimization of operational cost and performance interference in cloud data centers, *IEEE Transactions on Cloud Computing*. 5(4) (Jun 25, 2015), 697–711.
8. J. Yu and R. Buyya, Scheduling scientific workflow applications with deadline and budget constraints using genetic algorithms, *Scientific Programming*. 14(3–4) (2006), 217–230.
9. S. G. Domanal and G. R. M. Reddy, An efficient cost optimized scheduling for spot instances in a heterogeneous cloud environment, *Future Generation Computer Systems*. 84 (2018), 11–21.
10. J. Gu, J. Hu, T. Zhao, and G. Sun, A new resource scheduling strategy based on a genetic algorithm in cloud computing environment, *Journal of Computers*. 7(1) (2012), 42–52.
11. Domanal SG and Reddy GR. Optimal load balancing in cloud computing by efficient utilization of virtual machines. In 2014 Sixth International Conference on Communication Systems and Networks (COMSNETS), Jan 6, 2014, pp. 1–4.
12. K. Kaur, A. Chhabra, and G. Singh, Heuristics based genetic algorithm for scheduling static tasks in the homogeneous parallel system, *International Journal of Computer Science and Security (IJCSS)*. 4(2) (2010), 183–198.
13. X. Lu and Z. Gu, A load-adaptive cloud resource scheduling model based on ant colony algorithm, in IEEE International Conference on Cloud Computing and Intelligence Systems (CCIS). IEEE, 2011, pp. 296–300.
14. J. J. Liang, A. K. Qin, P. N. Suganthan, and S. Baskar, Comprehensive learning particle swarm optimizer for global optimization of multimodal functions, *IEEE Transactions on Evolutionary Computation*. 10(3) (2006), 281–295.
15. M. Kalra and S. Singh, “A review of metaheuristic scheduling techniques in cloud computing,” *Egyptian Informatics Journal*. 16(3), 275–295.

Deep Learning-Based Optimization ◾ **31**

