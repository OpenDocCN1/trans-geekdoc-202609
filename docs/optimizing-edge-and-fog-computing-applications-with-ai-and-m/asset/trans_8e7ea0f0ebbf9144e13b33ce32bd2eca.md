

# 使用 AI 优化边缘与雾计算应用

- 13. Ahn, J., Lee, Y., Kim, N., Park, C. and Jeong, J. (2023). 制造过程中利用时间序列分布偏移进行预测性维护和异常检测的联邦学习。Sensors 23(17), 7331. https://doi.org/10.3390/s23177331
- 14. Pruckovskaja, V., Weissenfeld, A., Hestracher, C., Graser, A., Kafka, J., Leputsch, P., Schall, D. and Kommitz, J. (2023). 工业应用中预测性维护和质量检测的联邦学习。arXiv preprint arXiv:2304.11011. https://arxiv.org/abs/2304.11011
- 15. Ke, A., Han, Y. and Kim, T-K. (2023). 基于编码器的联邦学习增强分布式电力系统的异常检测。PLoS One 18(8), e0290337.
- 16. Ahn, J., Lee, Y., Kim, N., Park, C. and Jeong, J. (2023). 制造过程中利用时间序列分布偏移进行预测性维护和异常检测的联邦学习。Sensors 23(17), 7331.
- 17. Liu, J., Lou, J., Xiong, L., Liu, J. and Meng, X. (2021). 异构差分隐私的投影平均。Proceedings of the VLDB Entertainment 15(4), 828–840.
- 18. Le, K., et al. (2024). 用于联邦泛化的高效组配归一化层和正则化。Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition.
- 19. Ma, X., et al. (2022). 联邦学习中非独立同分布（non-iid）数据解决综述。Generation Computer Systems 135, 244–258.
- 20. Yuan, X. and Li, P. (2022). 关于 FedProx 的收敛：局部不相似不变边界、非单调及超越。Advances in Neural Information Processing Systems 35, 10752–10765.
- 21. Gupta, P., Anand, A., Agarwal, P. and McArthur, G. (2024). 神经网络启发的云基础设施可扩展任务调度。Internet of Things and Cyber-Physical Systems 4, 268–279. 
- 22. Wang, H., et al. (2020). 匹配平均的联邦学习，arXiv preprint arXiv:2002.06440.
- 23. Mustapha, S. D. S. and Gupta, P. (2024). DBSCAN 启发的云基础设施任务调度。Internet of Things and Cyber-Physical Systems 4, 32–39.
- 24. Gupta, P., Rawat, P. S., Kumar Saini, D., Vijayarthi, A. and Alharbi, M. (2023). 神经网络启发的云基础设施差分进化任务调度。Alexandria Engineering Journal 37, 217–230.
- 25. Madhusdan, H. S., Gupta, P., Saini, D. K. and Tan, Z. (2023). 使用大象群优化方案的云计算中动态虚拟机分配。Journal of Circuits, Systems and Computers 32(11), 2350188.
- 26. Rawat, P. S., Gaur, S., Barthwal, V., Gupta, P., Ghosh, D., Gupta, D. and Rodrigues, J. C. (2023). 云计算中的虚拟机放置。Alexandria Engineering Journal 11, 145–152.
- 27. HS, M. Gupta, P. (2024). 基于 ANN 的联邦学习预测性维护。PLoS One 19(6), e030467.
- 28. S., et al. (2019). 边缘计算中的联邦学习场景与挑战。Future Internet 11(3).
- 29. Becker, S., Stoll, O., Kao, O. (2022). 神经网络启发的状态监控。IEEE BigData 4–8. 
- 30. Yegan, Y., et al. (2020). 物联网中的分布式联邦学习。Springer 2020.
- 31. Nguyen, J., et al. (2022). 联邦学习中的异步聚合。International Conference on Artificial Intelligence and Statistics. PMLR.

# 第 7 章：高级机器学习 预测性维护

## 针对中心化模型的机器学习聚合策略

预测性维护（PdM）是机器学习（ML）的一项关键应用，旨在减少停机时间并提高效率。然而，依赖于中心化数据的传统方法面临着许多挑战：

- **数据隐私担忧**：由于监管限制，行业无法共享数据。
- **高传输成本**：向中央服务器发送大量数据是不可持续的。
- **可扩展性限制**：随着连接设备数量增加，中心系统的负担随之增加。

为了解决这些问题，联邦学习（FL）成为了一种具前景的替代方案。它允许本地进行训练，仅向中央服务器共享更新，从而确保数据隐私。聚合策略的选择会影响模型的性能、鲁健性和适应性。本文探讨了 FL 中使用的各种聚合策略及其优势和适用性。

## 联邦预测性维护中的挑战

虽然 FL 提供了一种去中心化的方法，但其实现面临许多需要解决的挑战，例如数据安全和数据的变异性。

### 7.2 数据隐私与安全

在预测性维护中使用 FL 的动力之一是保护数据隐私和安全。工业环境产生大量的敏感数据，包括性能指标、错误日志和传感器读取。将这些数据共享给中央服务器会引发若干担忧：

- **合规性**：医疗、制造和能源行业受到严格数据保护法规（例如 GDPR 和 HIPAA）的限制。
- **机密性规则**：由于竞争考虑，公司往往不愿意共享机器数据，因为这些数据可能包含商业秘密或策略。
- **网络攻击风险**：中心化数据存储使系统容易受到网络威胁，包括未经授权的访问、数据泄露和工业间谍活动。

FL 通过允许本地训练缓解了这些风险，但还需要额外的安全措施（如安全聚合、加密和差分隐私）以防止对抗性攻击和模型反向破解。在工业设置中，传感器数据收集自各种机器，每种机器都有差异：

- **传感器类型和配置**：不同的设备制造商使用不同的传感器，导致格式、分辨率和测量单位的差异。
- **数据采样率**：某些机器以高频率生成数据，而另一些则不定期记录。
- **数据质量和噪声**：环境的变化、传感器老化和校准引入了数据质量的不一致。

这种异质性为训练泛泛化的联邦模型带来了挑战。如果局部数据分布差异巨大（非 IID 数据），全局模型可能无法收敛，或偏向某些机器类型。解决这一需要先进的聚合技术、自适应学习率和个性化联邦学习模型。

