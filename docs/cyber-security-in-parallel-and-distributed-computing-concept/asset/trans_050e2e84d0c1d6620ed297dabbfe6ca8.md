
- 15. AVISPA：HLPSL教程，互联网安全协议建模与分析初学者指南，文档版本：1.1，2006，http://www.avispa-project.org/，访问日期：2018年4月30日。
- 16. Gritzalis, D. (1997). 分布式医疗信息系统的基础安全策略. Computers & Security, 16(8), 709-719.
- 17. Lopriore, L. (2013). 分布式系统中的对象保护. Journal of Parallel and Distributed Computing, 73(5), 570-579.
- 18. Malina, L., Dzurenda, P., Hajny, J., & Martinasek, Z. (2018). 用于访问控制系统的安全高效双因素零知识认证解决方案. Computers & Security, 77, 500-513.
- 19. Tsai, J. L., & Lo, N. W. (2015). 一种面向分布式移动云计算服务的隐私感知认证方案. IEEE Systems Journal, 9(3), 805-815.
- 20. Odelu, V., Das, A. K., Kumari, S., Huang, X., & Wazid, M. (2017). 分布式移动云计算服务中可证明安全的认证密钥协商方案. Future Generation Computer Systems, 68, 74-88.
- 21. Xie, T., & Qin, X. (2007). 安全异构分布式系统中新调度算法的性能评估. Journal of Parallel and Distributed Computing, 67(10), 1067-1081.
- 22. Smith, M., Friese, T., Engel, M., & Freisleben, B. (2006). 使用沙箱和可信计算技术应对面向服务按需网格计算中的安全威胁. Journal of Parallel and Distributed Computing, 66(9), 1189-1204.
- 23. Cheng, N., Govindan, K., & Mohapatra, P. (2011). 基于会合的信任传播以增强分布式网络安全. International Journal of Security and Networks, 6(2-3), 112-122.
- 24. Khattab, S., Melhem, R., Moss, D., & Znati, T. (2006, April). 蜜罐反向传播以缓解欺骗性分布式拒绝服务攻击. 载于2006年第20届国际并行与分布式处理研讨会（IPDPS 2006）（第8页起）. IEEE.
- 25. Liu, H., Abraham, A., Snel, V., & McLoone, S. (2012). 分布式数据密集型计算环境中具有安全约束的工作流应用的群体调度方法. Information Sciences, 192, 228-243.
- 26. Colom, J. F., Gil, D., Mora, H., Volckaert, B., & Jimeno, A. M. (2018). 异构网络架构上分布式入侵检测系统的调度框架. Journal of Network and Computer Applications, 108, 76-86.
- 27. Jakbik, A., Grzonka, D., & Palmieri, F. (2017). 面向分布式云组织的非确定性安全驱动元调度器. Simulation Modelling Practice and Theory, 76, 67-81.
- 28. Zeng, L., Veeravalli, B., & Li, X. (2015). SABA：云环境中一种安全感知且预算感知的工作流调度策略. Journal of Parallel and Distributed Computing, 75, 141-151.
- 29. Khan, A. U., & Bagchi, S. (2018). 面向地理分布式移动计算系统的可靠RPC的软件架构与算法. Future Generation Computer Systems, 86, 185-198.
- 30. Sujithra, M., Padmavathi, G., & Narayanan, S. (2015). 移动设备数据安全：通过将移动数据外包到云的密码学方法. Procedia Computer Science, 47, 480-485.
- 31. Nam, H., & Lysecky, R. (2018). 分布式可重构嵌入式系统的安全感知多目标优化. Journal of Parallel and Distributed Computing.
- 32. Mahmud, R., Kotagiri, R., & Buyya, R. (2018). 雾计算：分类、综述与未来方向. 载于《万物互联》（第103-130页）. Springer, Singapore.

胜任地处理变量。最后，与以往方法相比，出色地传达结果。

## 9.2 领域相关的背景工作

### 9.2.1 云计算基础

分布式计算的基本思想是将计算资源作为云上的服务提供。用户无需投资购买功能强大的个人电脑来开展业务；相反，他们可以根据需求获得分布式计算服务 [8]。基础硬件主要托管在大型数据中心，使用复杂的虚拟化技术实现弹性资源供给、灵活性和可访问性。如上所述，服务器的易用性取决于灵活性，而这种灵活性无需为服务器托管付费。在这方面，需要以配置的方式来提供和使用相关事物 [13]。

云服务器取决于我们投入到服务器中的预算，有三种不同的模式，即 PaaS、SaaS、IaaS [17]。针对云的不同服务，Amazon 提供了多种框架，例如 EC2、S3 等。EC2 是一种以 99.99% 的最佳可用性提供更优质服务的服务。效率。服务器的可用性取决于我们在服务器和可用性上的预算投入。这类服务器主要用于私有云服务，即用于特定组织等场景 [1, 3-5]。

### 9.2.2 联邦云

在标准云环境中，云服务依赖于云服务提供商（CSP）。云服务提供商又依赖于服务提供商及其服务。在单云的情况下，整个云应存储在单个云中。CSP 应提供良好的服务、灵活性、易用性、便捷访问、随时可用等。CSP 的输出带来了良好的服务质量（QoS）。应用程序编程接口（API）是服务的基本需求。

### 9.2.3 云资源管理

资源管理定义了开发和维护服务器所需的最少资源数量。资源管理应确保无论有多少请求，都能维持服务器容量 [6-9, 11-15]。云资源方法取决于服务的模式，例如 SaaS、PaaS、IaaS。

对于我们所使用的云服务器，我们可以根据需求扩展或缩减服务、存储等。PaaS 提供商（例如 Google App Engine）提供了自动扩展能力。由于可用标准的缺乏和不足，IaaS 的自动扩展十分困难。在分布式计算中，无论是单一云还是联邦云，工作负载都是不可预测且多变的，集中式组织与控制可能无法提供持续服务和有效的保证。因此，统一组织无法为云资源管理方法提供充分的响应（见表9.1）。

![](img/57d9c6707468cbe6ea69c555dd9498fc_158_0.png)

图9.2 MQMCE 调度器过程。

最后，任务被区分为三种类型，即：

- 1. 任务分配。
- 2. 任务调度。
- 3. 任务执行。

图9.2 展示了调度策略。这三项是 QoS 所必需的。预处理是任务出现之前可以执行的工作。QoS 用于说明底层质量。任务执行说明了在框架上执行任务的逐步过程。工作流程 W(i) 由 5 类元组表示。

$W(i)[T(i j), (TQ)_i, (CQI), RLQ_i, A(vK)]$ (9.1)

其中，

- $T(i j)$ 是受限任务的数量。
- $TQ(i)$ 是工作流程的时间份额。
- $(CQI)$ 是工作流程所产生的显著成本。
- $A(vK)$ 是客户必需品的总体效益可用性。
- $RLQ(i)$ 是应用的可靠性质量度量。

此外，尽管资源数量增加，总成本和总能耗通常并未减少，如图9.4所示。

![](img/57d9c6707468cbe6ea69c555dd9498fc_160_0.png)

图9.4 混合工作流获得的非支配解。

从该图可以看出，随着资源数量增加到 6，QoS 测度一开始就会下降。这可以解释为：在扩展资源数量的同时，每个资源上执行的任务减少了；因此，任务可以延长其执行时间，资源也有更大的机会降低电压和频率，这可以非常有效地降低总能耗。在达到 6 个资源后，QoS 测度开始上升；其原因在于执行时间受处理器间通信主导，从而减少了降低资源电压和频率的机会。因此，可以获得使 QoS 测度最小化的最优资源数量。

![](img/57d9c6707468cbe6ea69c555dd9498fc_160_1.png)

图9.5 合成工作流获得的非支配解。

