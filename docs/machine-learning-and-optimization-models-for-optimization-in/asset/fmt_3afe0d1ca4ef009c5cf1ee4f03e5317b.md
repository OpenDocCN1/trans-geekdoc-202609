
# FIGURE 2.7
(a) Comparison of average start time vs five virtual machines. (b) Comparison of average start time vs ten virtual machines.

# FIGURE 2.8
(a) Comparison of average finish time vs five virtual machines. (b) Comparison of average finish time vs ten virtual machines.

# FIGURE 2.9
(a) Comparison of execution time vs five virtual machines. (b) Comparison of execution time vs ten virtual machines.

![Image 20](index-43_1.png)

**28** ◾ ML and Optimization Models

# TABLE 2.1 Simulation Parameters

| Hyper parameters | Value |
| :--- | :--- |
| Hidden layer | 1, hidden units = 3, Learning rate = 0.2 |
| Mutation rate | 0.15 |
| Evolution | 100 |
| Population size | 100 |
| Number of hidden layers | 3 |
| Neurons in output layer | 50/100 |
| Neurons in each hidden layer | 50 |
| Activation function | Leaky ReLU Activation function = `f(x) = { a * x if x ≤ 0, x if x > 0 }` where `a = .01` |

as a performance matrix. The results are computed with increasing task load and scaling the resources in terms of the virtual machine (Table 2.1).

The proposed algorithm performs better as compared to existing approaches in in-network and fault-aware environments.

Figures 2.10 (a) and (b) show the comparative results over the number of tasks completed as a performance matrix. The results are computed with increasing task load and scaling the resources in terms of the virtual machine. Figures 2.11 (a) and (b) show the comparative results over the number of tasks failed as a performance matrix, where the fault in the system occurs randomly using Poisson distribution. This performance matrix shows that the proposed algorithm reduces the network load and execution time as shown in Figure 2.12 which improves the system performance and quality of service as compared to existing algorithms.

# FIGURE 2.10
(a) Comparison of task completed count vs five virtual machines. (b) Comparison of task completed count vs ten virtual machines.

![Image 21](index-44_1.png)
![Image 22](index-44_2.png)

Deep Learning-Based Optimization ◾ **29**

# FIGURE 2.11
(a) Comparison of task failure count vs five virtual machines. (b) Comparison of task failure count vs ten virtual machines.

# FIGURE 2.12
Comparison of simulation time vs five virtual machines.

shows the comparative results over simulation time in milliseconds as a performance matrix. The results are computed with increasing task load and the performance of the proposed BB–BC ANN improves as compared to the traditional algorithm because the traditional algorithm needs a large number of iterations to find the best solution whereas the proposed algorithm is a trained neural network which needs to be trained once for a scenario.

**30** ◾ ML and Optimization Models

# 2.5 CONCLUSION

This work presented an astronomy- and neural-inspired virtual machine assignment to the user requests approach based on the features of the human brain and optimization method. The proposed algorithm tries to improve the fault tolerance of the cloud environment and to improve the performance of the system at the same time using machine learning techniques. The results and discussions section illustrates that BB–BC ANN performs better than existing meta-heuristic techniques. The study of the proposed algorithm is performed with scaling task load and resources.

Future work may focus on virtual machine allocation in a data center network. The drawback of the proposed algorithm is that the neural network needs to be trained after some time with updated upcoming tasks to overcome the decay of the trained model. This training time will, however, be much shorter than the total sum of the simulation time of the existing algorithm. In the future, the algorithm may improve the power consumption and scalability in the cloud environment. The proposed algorithm proved to perform better in the COVID-19 situation with overloaded and underloaded conditions in the cloud and performs better than any existing algorithm in both underloaded and loaded conditions.

# REFERENCES

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
