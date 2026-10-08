
在保留模型效用的同时，保护客户端数据。PFA 通过在客户端之间存在异构隐私预算时，通过优化通信效率和提高全局模型的准确性来改进这一点。尽管计算成本高昂，但同态加密仍然为敏感应用（如医学图像分析）提供了稳健的隐私保障，尽管对于此类应用，必须在计算成本和隐私利益之间进行高标准的权衡。现实世界的应用证明了这些技术的可行性和益处。例如，基于 CNN 的联邦学习（FL）已广泛应用于医学分类任务，如肺癌亚型的组织病理学分型，其中 DP-SGD 确保了对 HIPAA 等隐私法规的合规。同样，使用 LDP（局部差隐私）的隐私保护框架已应用于各种视频监控系统和工业故障检测场景，同时确保了去中心化数据集之间的安全协作。

表 10.1 提供了跨 FL、DP、CNN 和元学习领域的几项现有研究工作的对比分析。文中对它们的主要方法论以及可能遇到的关键优势和局限性进行了总结。这凸显了目前仍然存在的差距和局限性，这些问题可能可以通过其他研究工作得以克服。

## 10.9 结论

综而言，FL 为去中心化机器学习提供了一个相对很有前景的框架，通过避免共享原始数据来确保隐私。然而，对抗性攻击、隐私泄露和数据异质性的挑战构成了巨大的障碍。本章研究了潜在的解决方案，特别是 DP 和元学习，它们在增强安全性和适应性方面显示出前景。DP 的集成通过引入噪声来保护敏感信息，而元学习提供了对多样化客户端数据的适应性。此外，在图像分类的 CNN 领域，这些技术可以为平衡隐私和适应性需求铺平道路。然而，在保持 CNN 分类理想模型准确率的同时，如何维持这些因素方面仍存在不确定性。未来，安全性、适应性和性能之间的平衡将至关重要。需要进一步研究以在 CNN 背景下，优化 FL 架构和算法中 DP 与元学习的联合应用点。

## 参考文献

- 1. Yu, F., Lin, H., Wang, X., Garg, S., Kaddoum, G., Singh, S., & Hassan, M. M. (2023). Communication-efficient personalized federated meta-learning in Optimizing Edge and Fog Computing Applications with AI. IEEE Transactions on Network and Service Management, 20(2). https://doi.org/10.1109/TSNM.2023.3263831
- 2. Zhou, J., Wu, N., Wang, Y., Gu, S., Cao, Z., Dong, X., & Choo, K-K. R. (2022). A differentially private federated learning model for poisoning attacks in edge computing, IEEE Transactions on Dependable and Secure Computing, 20(3), 1941–1951. https://doi.org/10.1109/TDSC.2022.3168556, Learning on Heterogeneous Data. AISTATS Conference, Vol. 151.
- 3. Anonymous. (n.). Feasibility: A benchmark for attacks and defenses in federated learning LLMs. As a paper at ICLR 2024.
- 4. Dong, F., Ge, X., L., Q., Zhang, J., Shen, D., Liu, S., Liu, X., G., Wu, F., & Luo, J. (2023). PADFedMeta: A scalable and adaptive differentially private federated meta learning for AoT. Journal of Systems Architecture, 134, Art. 12754. https://doi.org/10.1016/j.sysarc.2022.102754
- 5. Huang, A., & WeBank AI Lab (2020). Dynamic backdoor attacks against federated learning. arXiv.
- 6. Dwork, C. (2006). Differential Privacy. International Colloquium on Automata, Languages and Programming (ICALP), vol. 2006, pp. 1–12. https://link.springer.com/chapter/10.1007/978-11787006-1
- 7. Truong, N., Kan, S., Wang, F., Data Science Institute, Imperial College London, Department of Computer Science, & Hong Kong Baptist University. (2021). Privacy preservation in federated learning: An insightful survey over the GDPR privacy. Computers & Security, 110, 102402. https://doi.org/10.1016/j.cose.2021.102402
- 8. Fu, J., Hong, Y., Lin, X., Ran, X., Sun, Z., Chen, W., & Cao, Y. (2024). Differentially private federated learning: A systematic review. arXiv, 2405.
- 9. Zhao, Y., Zhao, J., Wang, M., Wang, T., Lyu, L., Naito, M. (2021). Local differential privacy-based federated learning for internet of things. IEEE Internet of, 8(1).
- 10. Li, T., Falt, B. (2019). Federated learning of deep networks. arXiv.
- 11. McMahon, H. B., Moorte, E., Ramage, D., Hamilton, S., & Google, Inc. (2017). Communication-efficient learning of deep networks from decentralized data. In Proceedings of the 20th International Conference on Artificial Intelligence and Statistics (AIATS) 2017 (Vol. 54).
- 12. Hanzely, F., Richtár, P., & King Abdullah University of Science and Technology. (2021). Federated learning of a mixture of global and local models.
- 13. Finn, C., Abbeel, P., Levine, S., University of California, Berkeley, & OpenAI. (2017). Model-agnostic meta-learning for fast adaptation of deep networks. In Proceedings of the 34th International Conference on Machine Learning: Vol. PMLR 70.
- 14. Xu, Z., Zhang, Y., Han, L., Sig, F. (2023). Federated learning with noise-free privacy. arXiv.
- 15. Madhusdan, H. S., Gupta, P., Saini, D. K., & Tan, Z. (2023). Dynamic virtual machine allocation in cloud computing using elephant herd optimization scheme. Journal of Circuits, Systems and Computers, 32(11), 2351088.
- 16. Rawat, P. S., Gaur, S., Barthwal, V., Gupta, P., D, D., Gupta, D., & Rodrigues, J. J. C. (2025). Efficient virtual machine placement in cloud environment using BSO-ANN hybrid technique. Alexandria Engineering Journal, 110, 145–152.
- 17. HS, M., & Gupta, P. (2024). Federated learning inspired Antlion based orchestration for Edge computing environment. PLOS One, 19(6), e0304067.
