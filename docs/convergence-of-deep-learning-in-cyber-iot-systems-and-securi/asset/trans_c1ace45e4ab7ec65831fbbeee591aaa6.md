

# 140 深度学习在网络-IoT系统与安全中的收敛

![](img/081dc7f102a3793cb08980a6e19b8f17_163_0.png)

**图 6.3** Q学习算法的实现——交互图。

用例。连续实时数据从工业端到 Azure IoT 设置，随后通过多个组件的帮助进行进一步处理，例如：

- 强化学习
- 洞察 (Insights)
- Azure functions
- 流分析 (Stream analytics)
- Hub
- 其他 Azure 服务

调查与饮用水框架相关的供水质量等，正逐渐远离买者的真实医疗流程。具有处理能力的私有 IoT 边缘设备可以实现持续的质量维护 [8] 并提供支持。它可以处理过滤边界、增值物质的混合比例，或者根据供水边界、生态元素以及用户的使用，利用机器学习 (ML) 和边缘分析计算来增加的抽吸和注水（图 6.4）。

# 基于深度-Q 学习的智能 IoT 边缘解决方案 141

![](img/081dc7f102a3793cb08980a6e19b8f17_164_0.png)

遥测数据（输入）
反向动作
强化学习
洞察 (Insights)
Azure Function
Azure Runtime – IoT Edge
Azure IoT Edge 设备
处理后的输出
配置详情
Hub
流
Azure 服务

图 6.4 Azure IoT 边缘实时数据传输。

# 142 深度学习在网络-IoT系统与安全中的收敛

![](img/081dc7f102a3793cb08980a6e19b8f17_165_0.png)

传感器输入
输出命令
从传感器收集的数据
命令控制
流分析
命令路由
边缘运行时
强化学习
应用洞察 (App Insight)
洞察 (Insights)
配置数据

**图 6.5** 通过公有云边缘处理流分析的实时消息流。

# 基于深度-Q 学习的智能 IoT 边缘解决方案 143

强化学习和 IoT 边缘分析可以通过减少决策的延迟来传递可量化的业务优势和利益。这是通过在实际设备附近准备原始信息，并通过扩展逻辑枢纽来解决数据传输问题实现的 [16]（图 6.5）。

优势：

- 在本地收集信息，不会因为不规则的网络通道而遗漏任何内容
- 通过整合更精细的 AI 编程/机器学习/强化学习模块来降低延迟
- 通过仅发送所需的业务经验、处理设备行为的云端 IoT 设置，来减少传输成本。
- 通过简单的配置和手段升级/重新设计 ML/边缘分析模块。
- 针对性地对边缘源收集的大量无关信息进行专门处理。
- 边缘分析流快速限制引人的信息以进行丰富的分析。

## 6.4.1.2.5.8 Azure Containerizer Docker 服务

容器是程序包的标准组合，包含了应用程序代码、与之连接的配置文档和库，以及运行应用程序所需的条件。这允许工程师和 IT 专家在不同环境中一致地部署应用程序。

Docker 容器镜像是一个轻级、独立、可执行的程序包，包含了运行应用程序所需的所有内容：运行时、框架设备、框架库和设置 [15]。

一些云提供者有能力在他们的框架上运行您的 Docker 镜像，Microsoft Azure 就是其中之一。通过将您当前的应用程序迁移到容器并组装微服务应用程序为客户传递价值，节省成本。利用端到端设计器和 CI/CD 设备创建、刷新和部署您的容器化应用程序。使用与 Azure Active Directory 集成的完全托管 Kubernetes 配置来扩展容器。在您的应用程序现代化应用的的任何地方，在满足安全需求的同时加速您的容器化应用程序开发 [14]（图 6.6）。

![](img/081dc7f102a3793cb08980a6e19b8f17_167_0.png)

## 6.5 结论

在本章中，我们探讨了 Q 学习及其对应的 Q 学习。这是强化学习算法中两种非常流行的算法。我们包含了一个关于优化仓库自主智能体收集货物路径的案例研究，使得整个销售和交付过程对终端客户来说得到了优化。我们使用 Q 学习开发了这个案例研究，并试图证明 Q 学习可以以非常有效的方式确定最短路径，并确定特定代理的最大奖励。我们展示了在任何边缘设备上部署可序列化机器学习算法的参考架构。我们以 Azure 云计算平台为例，在 Azure IoT 边缘上部署代理，这反过来为代理在仓库的任何自主设备中的运行提供了重用性。在本章中，我们还展示了如何通过各种 Azure 云服务确保安全的同时，使该云计算模块可用且持久。部署使用了 docker 进行了容器化。

## 6.6 未来工作

- i) 我们将使用 TensorFlow 2.0 和 Terrace Framework 将此工作扩展到深度 Q 学习。我们还将尝试使用 Pytorch 作为此特定案例研究的深度学习部署平台。
- ii) 我们将在使用数字孪生概念的实际模拟环境中使用案例。我们将利用 Azure 平台探索这一概念。
- iii) 我们将使用其他各种深度强化学习技术来模拟这一环境。
- iv) 我们未来还将探索混合和预测计算使用参考架构的可能性。

# 参考文献

- 1. van Hasselt, H., Guez, A., Silver, D., Deep Reinforcement Learning with Double Q-Learning. 第十届人工智能会议, vol.30, 2016.
- 2. Droszer, S., Raedt, L., Driessens, K., Rational Reinforcement Learning. Machine Learning, 43, 1, 2–7, 2001.
- 3. Sutton, R.S., Introduction: The Challenge of Reinforcement Learning, in: Machine Learning, vol.8, pp.225–227, Kluwer Publishers, Boston, 1992.
- 4. Smith, T.W. and Colby, S.A., Teaching for Deep Learning. Clearing House, 80, 5, 205–210, 2007.
- 5. Schmidh, J., Deep learning in neural networks: An overview. 61, 95–117, 2015.
- 6. White, D.J., a Survey of Applications of Markov Decision Processes, J. Oper. Res. Soc., 44, 11, 1073–1096, 1993. http://www.jstor.org/stable/258387.
- 7. Kapuruge, M., Colman, S., Han, J., Bouguetta, A., Hauswitz, M., Liu, L., Achieving Multi-tenanted Business Processes in SaaS Applications, in: Enterprise Information Systems, pp.143–157, Springer, Berlin Germany 2011.
- 8. Reddy, G. and Subashini, N., A New Innovation On User’s Level Security For Storage Data In Cloud Computing. Int. J. Eng. Res. Technol. (IJERT), 3, 1, 1810–1814, 2014.
- 9. Schubert, P. and Adisa, F., Cloud Computing for Standard ERP Systems: Reference Framework and Research Agenda, in: Arbeitsbereiche aus Fachbereich Informatik, vol.4, p.29, 2019.
- 10. Na, S., Kim, K., Huh, E., A Methodology for Evaluating Cloud Computing Security-Level Agreements. IJACT, 5, 13, 140–142, 2013.
- 11. Müller, J., Krüger, J., Ender, S., Holm, M., Meier, A., Customizing enterprise software as a service applications: Back-end extension in a multi-tenancy environment, in: Enterprise Information Systems, pp.66–77, Springer, Berlin Germany, 2009.
- 12. Mushtaque, M.A. and Sindhu, R., A New Innovation On User’s Level Security For Storage Data In Cloud Computing. Int. J. Grid Distrib. Comput., 7, 3, 213–220, 2014.
- 13. Lenart, A., ERP in the Cloud–Benefits and Challenges, in: Research in Systems Analysis and Design: Models and Methods, pp.39–50, Springer, Berlin Germany, 2011.

