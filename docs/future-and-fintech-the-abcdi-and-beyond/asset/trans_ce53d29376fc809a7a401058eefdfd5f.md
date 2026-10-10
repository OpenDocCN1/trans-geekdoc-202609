

对于涉及敏感数据的隐私保护计算，除了哈希/加密工具和差分隐私库之外，用户还可以利用主要云平台提供的机密计算服务。对于多方安全计算（MPC），`Tensorflow Federated` 可作为开源库使用，`Private Join and Compute` 可在命令行安装并运行，而云合作伙伴解决方案（如 `Enveil ZeroReveal` 和 `Inpher XOR`）则可在云市场上获取。前文讨论的 UC Berkeley RISE Lab MC2 套件中的多个开源合作竞争学习协议也可部署在云端。此外，另一个 RISE 协议 `Delphi` 可用于促进深度学习推理，其中云端持有模型而用户持有输入向量，双方无需共享模型或输入数据。

## 9.6 案例研究：Capital One 向云端迁移数据的历程

Capital One 是一家财富 500 强金融服务公司，提供信用卡、消费银行（如消费贷款和汽车贷款）及商业银行服务。2020 年，Capital One 完成了从本地数据中心到公有云的全面迁移 [[16]](#chap9.xhtml#rref16)。他们的云迁移历程可供其他组织借鉴学习。

2015 年，Capital One 确立了“云优先”战略。他们决定为云端重新架构现有应用程序，同时在云端开发所有新应用程序。自此，该公司从未回头。他们首先将本地数据服务组件与云数据服务组件进行匹配，并采取“提升并迁移”方法将应用程序迁移到云端。随后，他们转向云原生数据服务——这些服务在本地要么不存在，要么构建/搭建成本高昂，并利用这些服务充分发挥云平台的最大潜力。他们意识到，云端赋予的强大能力和灵活性，若利用不当也会带来更高风险。他们遵循 `AWS Well-Architected framework`（AWS 优化架构框架）的指导方针在云端构建应用程序和基础设施。该框架涵盖五大支柱：(i) 运营卓越性，(ii) 安全性，(iii) 可靠性，(iv) 性能效率，和 (v) 成本优化。从一开始就更专注于前两大支柱，使 Capital One 能够在此过程中为其他三大支柱打下坚实基础。

随着云平台通过现有服务的增强和新服务的增加而持续演进，Capital One 一直密切关注云技术的最新进展，并改进其自身的云基础服务。他们还大量利用云 DevOps 工具来促进 `Infrastructure as Code (IaC)`（基础设施即代码）、`Microservices`（微服务）、`Continuous Integration and Continuous Delivery (CI/CD)`（持续集成和持续交付）以及 `Monitoring and Logging`（监控和日志记录）的使用，这在持续反馈循环中极大地增强了他们的数据和软件生命周期管理。他们敏捷的云端 DevOps 流程使他们能够快速开发新功能和产品，高效地近实时处理大量数据，并提供一个高效平台来生成业务分析、训练机器学习模型并驱动数据驱动决策。

尽管取得了显著成就，他们的云端之旅远非一帆风顺。包括 2019 年 7 月发生的大规模数据泄露事件在内的某些挫折，曾引发质疑并动摇了公众对其执行云战略能力的信心。然而，他们吸取教训，强化云治理框架，坚定不移地继续云端征程，并最终取得成功。借助云端的强大力量，Capital One 在金融行业引领潮流，为客户提供全新的银行体验，并建立高效的数字银行基础设施，助力塑造数字银行的未来。

## 9.7 结束语

云及相关技术作为高效企业数据集成的强大赋能者。云提供了更强的可扩展性、可靠性、可用性、灵活性、移动性、协作性、可访问性，以及更多的自由度和解决方案选择。如何将这些工具的潜力发挥到极致，取决于我们自己。

## 参考文献

[1](#chap9.xhtml#ref1). “AWS Documentation”. Amazon Web Services. [https://docs.aws.amazon.com/index.html](https://docs.aws.amazon.com/index.html). Accessed: November 20, 2021.

[2](#chap9.xhtml#ref2). “Azure documentation”. Microsoft. [https://docs.microsoft.com/en-us/azure/](https://docs.microsoft.com/en-us/azure/). Accessed: November 20, 2021.

[3](#chap9.xhtml#ref3). “Google Cloud Documentation”. Google. [https://cloud.google.com/docs](https://cloud.google.com/docs). Accessed: November 20, 2021.

[4](#chap9.xhtml#ref4). L. Wang, J. Near, N. Somani, P. Gao, A. Low, D. Dao and D. Song, Data Capsule: A New Paradigm for Automatic Compliance with Data Privacy Regulations. Accessed: August 30, 2019. [Online]. Available: [https://arxiv.org/abs/1909.00077](https://arxiv.org/abs/1909.00077)

[5](#chap9.xhtml#ref5). “Helping organizations do more without collecting more data”. Google Security Blog. [https://security.googleblog.com/2019/06/helping-organizations-do-more-without-collecting-more-data.html](https://security.googleblog.com/2019/06/helping-organizations-do-more-without-collecting-more-data.html). Accessed: June 19, 2019.

[6](#chap9.xhtml#ref6). F. Turan, S. Roy and I. Verbauwhede, “HEAWS: An Accelerator for Homomorphic Encryption on the Amazon AWS FPGA,” *IEEE Transactions on Computers,* Volume 69, Issue 8, pp. 1,185–1,196, 2020.

[7](#chap9.xhtml#ref7). N. Kumar, M. Rathee, N. Chandran, D. Gupta, A. Rastogi and R. Sharma, CrypTFlow: Secure TensorFlow Inference. Accessed: March 19, 2020. [Online]. Available: [https://arxiv.org/abs/1909.07814](https://arxiv.org/abs/1909.07814)

[8](#chap9.xhtml#ref8). “Introducing Google Cloud Confidential Computing with Confidential VMs”. Google Security and Identity Blog. [https://cloud.google.com/blog/products/identity-security/introducing-google-cloud-confidential-computing-with-confidential-vms](https://cloud.google.com/blog/products/identity-security/introducing-google-cloud-confidential-computing-with-confidential-vms). Accessed: July 14, 2020.

[9](#chap9.xhtml#ref9). “Announcing General Availability of AWS Nitro Enclaves”. Amazon Web Services. [https://aws.amazon.com/about-aws/whats-new/2020/10/announcing-general-availability-of-aws-nitro-enclaves/](https://aws.amazon.com/about-aws/whats-new/2020/10/announcing-general-availability-of-aws-nitro-enclaves/). Accessed: October 28, 2020.

[10](#chap9.xhtml#ref10). “Confidential computing on Azure”. Microsoft. [https://docs.microsoft.com/en-us/azure/confidential-computing/overview](https://docs.microsoft.com/en-us/azure/confidential-computing/overview). Accessed: November 11, 2021.

[11](#chap9.xhtml#ref11). A. Dave, C. Leung, R. Popa, J. Gonzalez and I. Stoica, “Oblivious coopetitive analytics using hardware enclaves,” *Proc. 15th European Conf. Computer Systems,* Article No.: 39, pp. 1–17, April, 2020.

[12](#chap9.xhtml#ref12). W. Zheng, R. Popa, J. Gonzalez and I. Stoica, Helen: Maliciously Secure Coopetitive Learning for Linear Models. Accessed: September 3, 2019. [Online]. Available: [https://arxiv.org/abs/1907.07212](https://arxiv.org/abs/1907.07212)

[13](#chap9.xhtml#ref13). W. Zheng, R. Deng, W. Chen, R. Popa, A. Panda and I. Stoica, Cerebro: A Platform for Multi-Party Cryptographic Collaborative Learning. *30th USENIX Security Symposium (USENIX Security 21),* pp. 2723–2740, August, 2021.

[14](#chap9.xhtml#ref14). “TensorFlow Privacy”. Google *et al*. [https://github.com/tensorflow/privacy](https://github.com/tensorflow/privacy). Accessed: December 21, 2020.

