

通过根据本地数据重要性或当前资源可用性等因素仔细选择参与者。例如，自适应联邦学习系统可以允许边缘设备独立更新本地模型，从而适应间歇性连接和波动的资源限制。通过实施这些策略，联邦学习（FL）系统可以在雾节点和边缘设备上良好运行，鼓励在资源有限的环境下采用去中心化学习。

## 6.5 联邦学习在预测性维护中的应用

预测性维护（PdM）旨在通过分析从机械收集的数据来预测设备故障，从而优化维护计划并减少意外停机。联邦学习已成为该领域的一项关键技术，能够在保护数据隐私的同时，实现跨去中心化设备的协作模型训练。本节将探讨联邦学习在 PdM 中的应用，重点关注设备监控、故障诊断和能量优化。

### 6.5.1 设备监控

在工业环境中，持续的设备监控对于维持运行效率至关重要。传统的集中式状态监测方法通常需要将大量的传感器数据传输到中央服务器，这给数据隐私和网络可靠性带来了挑战。联邦学习通过在机器附近的边缘设备上直接进行机器学习模型的去中心化训练，解决了这些问题。例如，Becker 等人 [29] 提出了一种基于自动编码器的联邦学习方法，利用旋转机械的传感器数据。这种方法实现了本地的分布式训练，允许在不共享原始数据的情况下跨组织边界进行传输，从而保护了隐私并减轻了网络负载。

### 6.5.2 故障诊断

准确的故障诊断对于防止设备故障和确保安全至关重要。联邦学习通过在来自多个源的多样化数据集上训练鲁棒模型，且不损害机密性，增强了故障诊断。通过聚合来自各种工业环境的知识，基于联邦学习的模型可以获得更好的泛化和故障检测能力。这种协作方法允许识别在孤立数据集中可能无法发现的故障模式，从而实现更可靠、及时的故障诊断。

### 6.5.3 能量优化

能量消耗是工业操作中备关注的问题，无论是从成本还是环境角度来看。联邦学习通过促进分析运行数据以识别节约机会的模型开发，有助于能量优化。通过在不同设施之间协作训练模型，组织可以发现导致能源消耗减少的最佳实践和操作调整。这种去中心化的方法确保敏感的运行数据留在本地，在解决隐私担忧的同时，促进了整个行业的能效实践。联邦学习通过为设备监控、故障诊断和能量优化提供协作、保护隐私的模型训练，为 PdM 提供了一种变革性的方法。它在工业环境中的应用不仅提高了预测模型的准确性，而且在不损害数据安全的情况下促进了组织协作。

## 6.6 主要研究空白与未来方向

联邦学习因其在不损害数据隐私的情况下实现协作训练的潜力而受到了广泛关注。然而，仍存在一些研究差距阻碍了其广泛应用和效率。本节深入探讨了需要进一步探索的三个关键领域：自适应聚合机制、增强的隐私措施和扩展性挑战。

### 6.6.1 自适应聚合机制

在联邦学习中，中央服务器聚合来自分布式客户端的更新以形成全局模型。传统的聚合方法（如 FedAvg）通常假设类别之间的数据分布是同的。但在实际场景中，数据通常是非独立同分布（non-IID），导致模型性能欠优。为了解决这个问题，研究人员提出了考虑数据异性的自适应聚合技术。例如，Yeganah 等人 [30] 引入了反距离聚合方法，根据本地与全局模型参数之间的距离为客户端更新分配权重，从而减轻了离群值的影响并增强了收敛速度。

### 6.6.2 增强的隐私机制

虽然联邦学习通过将原始数据留在本地设备上固有促进了数据隐私，但仍然存在漏洞，特别是关于从模型更新中重建敏感信息的推理攻击。为了加强隐私，研究人员探索了多种技术。差分隐私（DP）在模型更新中引入噪声，掩盖单个数据的贡献。安全多方计算（SMC）允许在不暴露个人输入的情况下进行协作计算。尽管有了这些进展，隐私与模型效用计算效率之间的挑战依然存在。最近的综述提供了这些隐私保护方法的全面概述，并强调了需要能够在联邦学习框架内有效整合 DP 和 SMC 的新型解决方案。

### 6.6.3 扩展性挑战

扩展性仍然是联邦学习中的备受关注的问题，特别是在处理大量客户端和大型模型尺寸时。同步聚合方法可能会导致通信瓶颈和延迟增加，因为中央服务器必须等待更新。异步聚合提供了一个潜在的解决方案，允许服务器在客户端更新到达时立即更新全局模型，而无需等待。Nguyen 等人 [31] 提出了一种缓冲异步方法 FedBuff，它结合了同步和异步方法的优点。FedBuff 维护一个输入更新的缓冲区，在保持与安全聚合等技术兼容的同时实现了高效聚合。实验结果表明 FedBuff 增强了联邦学习的效率和扩展性。解决这些研究差距对于联邦学习在各个领域的进展和实际部署至关重要。未来的工作应侧重于开发稳健的聚合策略，在不损害模型性能的情况下增强隐私保护机制，并设计能够处理多样化大规模客户端网络的可扩展联邦学习架构。

## 6.7 结论

联邦学习已成为 PdM 中的一种变革性方法，能够在保护数据隐私的同时实现跨去中心化设备的协作模型训练。通过促进无需中心化数据存储即可进行的设备分析，联邦学习解决了与数据机性和网络可靠性相关的关键问题。研究已经证明了联邦学习在各种工业应用中的有效性。尽管 FL 固有地通过将原始数据留在本地设备上促进了数据隐私，但仍然存在漏洞，特别是关于可以从模型更新中重建敏感信息的推理攻击。为了加强隐私，探索了多种技术。隐私与模型效用和计算效率之间的挑战依然存在。提供了这些隐私保护方法的全面概述，并强调需要能够在 FL 框架内有效集成 DP 和 SMC 的新解决方案。扩展性仍然是 FL 中的一个备受关注的问题，特别是在处理大量客户端和大型模型尺寸时。同步聚合方法可能会导致通信瓶颈和延迟增加，因为中央服务器必须等待更新。异步聚合提供了一个潜在的解决方案，允许服务器在客户端更新到达时立即更新全局模型，而无需等待。Nguyen 等人 [31] 提出了一种缓冲异步方法 FedBuff，它结合了同步和异步方法的优点。FedBuff 维护一个输入更新的缓冲区，在保持与安全聚合等技术兼容的同时实现了高效聚合。实验结果表明 FedBuff 增强了 FL 的效率和扩展性。解决这些研究差距对于 FL 跨多个领域的进展和实际部署至关重要。未来的工作应侧重于开发稳健的聚合策略，在不损害模型性能的情况下增强隐私保护机制，并设计能够处理多样化和大规模客户端网络的可扩展 FL 架构。FL 已成为 PdM 中的一种变革性方法，能够在保护数据隐私的同时实现跨去中心化设备的协作模型模型训练。通过促进无需中心化数据存储即可进行的设备分析，FL 解决了与数据机性和网络可靠性相关的关键问题。研究已经证明了 FL 在各种工业应用中的有效性。

## 参考文献

- 1. McMahan, B., et al. (2017). Communication-efficient learning of deep networks. AIST.
- 2. Kairouz, P., et al. (2021). Advances and open problems in federated learning. Foundations and Trends in Machine Learning 14(1–210).
- 3. Zhao, Y., et al. (2018). Federated learning with non-IID data. NeurIPS.
- 4. Li, T., et al. (2018). Federated learning in heterogeneous networks. MLSys.
- 5. Yang, Q., Liu, Y., Chen, T. and Tong, Y. (2019). Federated learning: Concept and applications. ACM Transactions on Intelligent Systems and Technology (TIST) 10(2), 1–19.
- 6. Bonawitz, K., et al. (2019). Towards federated learning at scale: System design.
- 7. Du, J., Qin, N., Huang, D., Jia, X. and Zhang, Y. (2023). Lightweight FL: A Low-Cost Federated Learning Framework for Mechanical Fault Diagnosis with Training Optimization and Model Pruning. IEEE Transactions on Instrumentation and Measurement 73, 1–14.
- 8. de Melo Rosa, G. L., Mohanram, P., Gilerson, A. and Schmitt, R. H. (2023). Architecture for edge-based predictive maintenance of machines using federated learning and multi sensor platforms. Preprints.org: preprints2023053.1563v1. DOI: 10.20944/
- 9. Han, P., Wang, S. and Leung, K. K. (2020, November). Gradient sparsification for federated learning: An online learning approach. In 2020 IEEE 40th International Conference on Distributed Computing Systems (ICDS) (pp. 300–310). IEEE.
- 10. Felbab, V., Kiss, P. and Horváth, T. (2019, September). Optimization in federated learning. In ITAT (pp. 58–66).
- 11. Sun, W., Lei, S., Wang, L., Liu, Z. and Zhang, Y. (2020). Adaptive federated learning and digital twin for industrial internet of things. IEEE Transactions on Industrial Informatics 17(8), 5605–5614.
- 12. Wangni, J., Wang, J., Liu, J. and Zhang, T. (2018). Gradient sparsification for communication-efficient distributed optimization. Advances in Neural Information Processing Systems 31, 1–11.
