

# 390 第 11 章：MLOps：从开发到部署的转型

基于加密协议，由个人对数据子集进行计算，使得访问敏感和私有数据变得困难。

在实施 MLOps 过程中，与标准软件工程实践的一个区别是需要启用对 ML 产物的自动化测试。在实施 MLOps CI/CD 步骤阶段，必须跟踪这些产物。ML 产物的示例如 [5]：

- 模型代码及其预处理
- 模型超参数及相关的模型配置
- 用于训练和模型验证的数据
- 完成测试阶段后的模型
- 测试场景的代码和数据
- 创建模型时使用的特定版本库和环境变量
- 文档

这些产物是成功实施 MLOps 过程的关键组成部分，因为需要使应用程序模块化。微服务是一种解决方案，允许将应用程序拆分为许多组件，这些组件可以作为一组较小服务的集合进行更改、管理和部署，而不是作为一个大型、复杂的单体应用。微服务由容器驱动，容器提供了一种封装可执行代码、库、通过 API 使用第三方应用和其他技术的方法，以实现敏捷的 DevOps 开发。微服务允许你将应用程序分解为更小的服务。容器允许你将微服务实例化为自包含的镜像。Docker 是一种被广泛接受的创建容器的技术，而 K8s 是流行的容器编排类型之一，适用于本地部署或商业云。

本章中讨论的技术和方法必须由商用 MLOps 平台提供支持，并随时由内部基础设施（例如专有数据）进行补充。在整个章节中，我们使用了以下 MLOps 平台的定义，该定义与我们的 AI 系统架构框架和 AI 生态系统一致：

MLOps 平台：一种能够实现 AI 产品或服务全生命周期的环境，支持第 10 章图 10.3 所示的 AI 系统架构框架，并满足图 10.4 所示 AI 生态系统的一部分、具有表 10.6 描述特征的 AI 平台的要求。

AI 能力的发展可能非常耗时且昂贵。因此，AI 组织对具有 AutoML 能力的 MLOps 平台非常感兴趣。人们对让非专家也能使用的 ML 模型实现民主化也有浓厚兴趣。AutoML 促进了 AI 能力的快速开发和部署，从数据摄取阶段开始，持续到 ML 模型开发和部署。

AI 社区引起极大关注的另一种方法是在 ML 模型开发中使用 LCNC（低代码无代码）。LCNC 允许 AI 开发者轻松地拖放一次性构建块来构建 AI 能力。

我们在本章结束时，为读者提供了在 AI 开发和部署阶段经常经历的七个常见陷阱：

- 常见陷阱 1：业务目标和利益相关者需求定义不明。
- 常见陷阱 2：缺乏结构良好的开发和部署环境。
- 常见陷阱 3：AI 产品和服务被作为单体应用开发，导致集成、验证和校验关键子系统组件极度困难。
- 常见陷阱 4：缺乏对 MVP（最小可行性产品）的早期演示，正如敏捷开发过程所提倡的、成本优化以及所有属性（即运营卓越性、可靠性和安全性、性能指标、风险管理和质量保证）的合规性，这些显示在 AI 系统架构实现框架的外围（见图 10.3 和表 11.1）。
- 常见陷阱 5：当所有开发都在企业级场景中进行演示时，无法在高度受限的环境（如边缘端）中运行。
- 常见陷阱 6：忽视开发和部署 AI 系统的环境-社会-治理影响，导致当 AI 产品或服务未被市场接受时，企业产生成本和收入损失。
- 常见陷阱 7：忽略了成功设计、实施、集成和过渡 AI 能力所需的领导力和技术人才水平。

我们还讨论了关于如何克服这些陷阱的建议。

## 11.7 练习题

- 1. 详述我们的 MLOps 定义如何适应 DevOps 过程的背景。
- 2. 发明（invention）和创新（innovation）之间的区别是什么？
- 3. DevOps 和 MLOps 的步骤两个是部署和监控。
  a. 正确
  b. 错误
- 4. 安全在 MLOps 步骤中不需要考虑。
  a. 正确
  b. 错误
- 5. 识别并简述图 10.3 所示 AI 系统架构框架外围的属性。
- 6. AI 系统工程师/架构师的角色是什么？
- 7. 详述在 AI 系统工程特征的背景下，系统分析权衡（trade-offs）的含义。
- 8. 成功的 MLOps 实现要求所有步骤必须按顺序执行，并在进行 IV&V（验证与确认）之前完成。
  a. 正确
  b. 错误
- 9. I-V&V 测试必须在什么种级别的 AI 子系统或系统进行？选择最合适的答案。
  a. 单元测试
  b. 子系统
  c. 在线端到端 AI 系统
  d. 内联端到端 AI 系统
  e. 以上所有
- 10. 技术债（technical debt）是指什么？
- 11. 解释在数据使用期间实施安全多方计算方案的益处。
- 12. 必要在完成测试阶段后跟踪 ML 模型，而不将训练和验证数据作为 ML 产物之一。
  a. 正确
  b. 错误

## 11.8 参考文献

- 13. 什么是微服务？
- 14. 使用容器的价值是什么？描述创建容器时使用的一种技术。
- 15. 虚拟机（VMs）和容器之间的主要区别是什么？
- 16. 描述使用 Kubernetes (K8s) 作为一种编排的好处。
- 17. AutoML 是一种无需 AI 团队干预即可自动任务制定和预测工程的技术。
  a. 正确
  b. 错误
- 18. 在 LCNC 方法的实施中，什么是公民开发者（citizen developer）？
- 19. 选择七个常见陷阱之一，详述其意义以及避免它的建议。
- 20. 假设你被任命为 AI 架构师，根据本章描述的工具、技术和方法，在一个资源有限的小型公司工作，你会如何缓解本章讨论的常见陷阱？

- 1. Khalajadeh, H., M. Abdelrazek, J. Grundy, et al., Survey and analysis of current end-user data analytics tool support, in IEEE Transactions on Big Data, 2019.
- 2. Ng, A., Data-centric AI. 2022.
- 3. Strickland, E. and Andrew Ng, AI minimalist: The machine-learning pioneer says small is the big, IEEE Spectrum, 2022. 59(4): 22–50.
- 4. Gift, N. and A. Deza, Practical MLOps. 2021, O'Reilly Media
- 5. Trevel, M. N. Omont, C. Sternac, et al., Introducing MLOps. 2020
- 6. Walker, B., Innovation versus invention: Make the leap and reap the rewards. 2015, WIRE.
- 7. Ng, A., MIT technology review: AI-focused EmTech digital. 2021.
- 8. Kelleher, J. D., B. Mac Namee, and A. D'atcy, Fundamentals of machine learning for predictive data analytics: Algorithms, worked examples, and case studies. 2020, MIT Press.
- 9. Baier, L., E. Jöh, and S. Seebacher. Challenges in the deployment and operation of machine learning in practice, in Proceedings of the 27th European Conference on Information Systems (ECIS), Stockholm and Uppsala, Sweden, June 8–14, 2019. https://aisel.aisnet.org/ecis2019_rp/163.

