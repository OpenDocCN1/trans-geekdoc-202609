

# 评估指标

[Figure 4](#979-8-3693-1642-9.ch005.xhtml#f04) 图示了测量体系与 TP、FP、FN 和 TN 标记之间的关系。最直观的分类指标是准确率，它衡量网络中正确预测的攻击占攻击总数的比例。

**Accuracy** = ![Mathtype979-8-3693-1642-9.ch005.m06](i/ch005.m06.png) (6)

当数据集不平衡时，精确率和召回率比准确率能更好地衡量性能。精确率衡量真阳性在所有正向预测中的准确度。

**Precision** = ![Mathtype979-8-3693-1642-9.ch005.m07](i/ch005.m07.png) (7)

模型识别真阳性占实际正样本总数比例的能力。

**Recall** = ![Mathtype979-8-3693-1642-9.ch005.m08](i/ch005.m08.png) (8)

F1-score 是精确率和召回率的调和平均数。因此，从公式 (6)、(7) 和 (8) 可得：

**F1-score** = 2 × ![Mathtype979-8-3693-1642-9.ch005.m09](i/ch005.m09.png) (9)

所提模型实现了 90.96% 的高准确率，92.87% 的高精确率，表明该模型能正确预测正类别。该模型的召回率为 95.11%，表明模型成功识别了大部分正实例。F1-score 为 93.98%，在 FP 和 FN 之间取得了平衡。

# 6. 结论

尽管 `XGBoost` 分类在 ML 算法中广泛使用，但需要调整训练器参数以提高性能，而获得最优参数是一项具有挑战性的任务 (Cheng and Shi, 2021)。为克服这些问题，我们采用 `LightGBM` 方法而非 `XGBoost` 进行入侵检测。我们基于特征分数的重要性应用 `LightGBM` 模型进行特征选择 (Nadiya et al., 2020)。设定一个阈值以判断数据是正常还是受攻击。实验结果表明，与基准模型 `XGBoost` 相比，分类准确率达到 91%。因此，所提模型 `WOA` 结合 `LightGBM` 能产生更高的准确率和更快的入侵检测模型。

## 6.1 未来展望

网络安全处理高维数据，因为攻击数据集太大难以处理。因此，先进的学习技术应运而生以处理高维数据。深度学习方法和最新的人工智能技术等先进学习技术，通过高效覆盖分类和特征选择问题，能为网络攻击检测问题提供更好的解决方案。

# 缩略语

*   **ML**: Machine learning
*   **CS**: Cryptosystems
*   **SVM**: Support Vector Machine
*   **WOA**: Whale Optimization Algorithm
*   **LightGBM**: Light Gradient Boosting Machine
*   **IoT**: Internet of Things
*   **MSE**: Mean Square Error

# 参考文献

Ahmad, S., & Mirvaziri, H. (2019). Performance improvement of intrusion detection system using neural networks and particle swarm optimization algorithms. *International Journal of Information Technology : an Official Journal of Bharati Vidyapeeth's Institute of Computer Applications and Management*, 12, 849–860.

Chaofei, T. (2020). An Efficient Intrusion Detection Method Based on LightGBM and Autoencoder. *Semantic Scholar, Symmetry*, 12(1458), 1-16.

Chen, J. H., Ma, S. F., & Wu, Y. (2021). International carbon financial market prediction using particle swarm optimization and support vector machine. *Journal of Ambient Intelligence and Humanized Computing*, 2021, 1–15.

Chen, R. Y., Pan, B., & Lin, X. D. (2016). Chinese stock index futures price fluctuation analysis and prediction based on complementary ensemble empirical mode decomposition. *Mathematical Problems in Engineering*, 2016, 1–13. doi:[10.1155/2016/3791504](https://doi.org/10.1155/2016/3791504)

Chung-Jui, T., Chuang, L.-Y., Jun-Yang, C., & Yang, C.-H. (2007). Feature selection using PSO-SVM. *IAENG International Journal of Computer Science*, 33.

Cong, Y.-Q., Guan, T., Cui, J., & Cheng, X. (2022). LGBM: An Intrusion Detection Scheme for Resource-Constrained End Devices in Internet of Things. *Security and Communication Networks*, 2022, 1–12. doi:[10.1155/2022/1761655](https://doi.org/10.1155/2022/1761655)

Devan, P., & Khare, N. (2020). An efficient XGBoost-DNN-based classification model for network intrusion detection system. *Neural Computing & Applications*, 32(16), 16. doi:[10.1007/s00521-020-04708-x](https://doi.org/10.1007/s00521-020-04708-x)

Esmaeili, M., Goki, S. H., Masjidi, B. H. K., Sameh, M., Gharagozlou, H., & Mohammed, A. S. (2022). ML-DDoSnet: IoT Intrusion Detection Based on Denial-of-Service Attacks Using Machine Learning Methods and NSL-KDD. *Wireless Communications and Mobile Computing*, 2022, 1–16. doi:[10.1155/2022/8481452](https://doi.org/10.1155/2022/8481452)

Gautam, S., Henry, A., Zuhair, M., Rashid, M., Javed, A. R., & Maddikunta, P. K. R. (2022). A Composite Approach of Intrusion Detection Systems: Hybrid RNN and Correlation-Based Feature Optimization. *Electronics (Basel)*, 11(21), 3529. doi:[10.3390/electronics11213529](https://doi.org/10.3390/electronics11213529)

Hanieh, A., Richard, M. K., Wanchat, T., & Kenneth, A. L. (2019). A swarm intelligence-based approach to anomaly detection of dynamic systems. *Swarm and Evolutionary Computation*, 44, 806–827. doi:[10.1016/j.swevo.2018.09.003](https://doi.org/10.1016/j.swevo.2018.09.003)

Li, P., Qiang, W. & Christopher, J. B. (2007). McRank: Learning to rank using multiple classification and gradient boosting. *Advances in Neural Information Processing Systems*, 20.

Liang, Y., Wu, J., & Wang, W. (2019). ACM Product Marketing Prediction Based on XGboost and LightGBM Algorithm. *Association for Computing Machinery*.

Ma, L., Cheng, S., & Shi, Y. (2021). Enhancing learning efficiency of brain storm optimization via orthogonal learning design. *IEEE Transactions on Systems, Man, and Cybernetics. Systems*, 51(11), 6723–6742. doi:[10.1109/TSMC.2020.2963943](https://doi.org/10.1109/TSMC.2020.2963943)

Ma, L., Huang, M., Yang, S., Wang, R., & Wang, X. (2021). An adaptive localized decision variable analysis approach to large-scale multi-objective and many-objective optimization. *IEEE Transactions on Cybernetics*, 52(7), 6684–6696. doi:[10.1109/TCYB.2020.3041212](https://doi.org/10.1109/TCYB.2020.3041212)

Machado, F. P. (2003). Communication and memory efficient parallel decision tree construction. *Academic Press*.

Mohamed, S. A., Alsaif, O. I., & Saleh, I. A. (2022). Intrusion Detection Network Attacks Based on Whale Optimization Algorithm. *Ingénierie Des Systèmes D Information*, 27(3), 441–446. doi:[10.18280/isi.270310](https://doi.org/10.18280/isi.270310)

Mourad, A., Tout, H., Wahab, O. A., Otrok, H., & Dbouk, T. (2020). Ad-hoc Vehicular Fog Enabling Cooperative Low-Latency Intrusion Detection. *IEEE Internet of Things Journal*, 1–1. doi:[10.1109/JIOT.2020.3008488](https://doi.org/10.1109/JIOT.2020.3008488)

Muhammed, S., Gianni, A. D. C., & Muddassar, F. (2011). Swarm intelligence based routing protocol for wireless sensor networks: Survey and future directions'. *Information Sciences*, 181(20), 4597–4624. doi:[10.1016/j.ins.2010.07.005](https://doi.org/10.1016/j.ins.2010.07.005)

Nadiya El, K., Mohamed, E., Youssef, L., & Raja, T. (2020). A Smart Agent Design for Cyber Security Based on Honeypot and Machine Learning. *Security and Communication Networks*, 2020, 1–9.

Rahman, S. A., Tout, H., Talhi, C., & Mourad, A. (2020). Internet of Things intrusion Detection: Centralized, On-Device, or Federated Learning? *IEEE Network*, 34(6), 310–317. doi:[10.1109/MNET.011.2000286](https://doi.org/10.1109/MNET.011.2000286)

Rongfeng, Z., Jiayong, L., Weina, N., Liang, L., Kai, L., & Shan, L. (2020). Preprocessing Method for Encrypted Traffic Based on Semisupervised Clustering. *Security and Communication Networks*, 2020, 1–13.

