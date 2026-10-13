

# 实验与结果分析

随后，我们采用了随机森林分类算法，因为它在实验中取得了最佳结果。我们将随机森林应用于三个类别，以查看哪一类数据包层对检测攻击贡献最大、效果最好且准确率最高；同时也将其应用于各类别的选定特征，以检查准确率的变化。在保持高效率的前提下获得最少数量的特征将是最佳解决方案。

## 实验 1

首先，为利用最少特征检测 Mirai 攻击，我们分别采用了两种最常见的元启发式搜索算法——遗传算法和粒子群优化（PSO），以检验它们在众多解决方案中搜索最佳特征子集的效率。遗传算法从 116 个元素中选择了 18 个特征，粒子群优化选择了 12 个元素。

随后，我们应用了三种分类算法——朴素贝叶斯、J48 和随机森林——构建模型以检测网络流量中 Mirai 僵尸网络的恶意行为，并对比哪种算法效果最佳。我们使用 10 折交叉验证测试模型，并采用准确率、精确率、召回率和 F1 值等指标评估结果。表 3 展示了分别应用遗传算法和 PSO 后，这些分类算法在数据集上的性能表现。随机森林算法在两种特征选择算法中均取得最佳结果，遗传算法下准确率为 99.53%，PSO 下为 99.81%。该数据集上的先前工作已达到 100% 准确率（Meidan 等，2018）。因此，我们尝试一种能获得更高准确率的方法：先应用遗传算法再应用 PSO 的实验达到了预期效果，该方法仅选择了 8 个特征，却足以以 100% 的准确率检测 Mirai 僵尸网络的异常行为。表 4 展示了该实验结果，随机森林算法结合这种双重特征选择影响也获得了 100% 的最佳准确率。

### 表 3. 两个网络层子集在随机森林算法下的结果

| 数据子集 | 特征选择前准确率 | 特征选择后准确率 |
| :--- | :---: | :---: |
| 网络层 | 100% | 99.98% |
| 网络层和传输层 | 99.96% | 99.95% |
| 网络层和数据链路层 | 100% | 100% |

### 表 4. 遗传算法与 PSO 单独应用的结果

| 指标 | 遗传算法 | | | 粒子群优化 (PSO) | | |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| | 朴素贝叶斯 | J48 | 随机森林 | 朴素贝叶斯 | J48 | 随机森林 |
| 准确率 | 98.10% | 96.3% | **99.53%** | 98.00% | 95.73% | **99.81%** |
| 精确率 | 0.880 | 0.962 | **1.00** | 0.981 | 0.952 | **1.00** |
| 召回率 | 0.880 | 0.974 | **1.00** | 0.981 | 0.975 | **1.00** |
| F1 值 | 0.880 | 0.967 | **1.00** | 0.981 | 0.963 | **1.00** |

### 表 5. 多阶段特征选择（遗传算法后接 PSO）的结果

| 指标 | 遗传算法 + PSO | | |
| :--- | :---: | :---: | :---: |
| | 朴素贝叶斯 | J48 | 随机森林 |
| 准确率 | 99.99% | 98.99% | **100%** |
| 精确率 | 1.00 | 0.989 | **1.00** |
| 召回率 | 1.00 | 1.00 | **1.00** |
| F1 值 | 1.00 | 0.994 | **1.00** |

# 结论与未来工作

本文提出了一种结合遗传算法和粒子群优化的多阶段特征选择方法，配合随机森林集成机器学习算法，构建了一个用于检测基于网络的 Mirai 异常行为的分类模型，且仅使用最少数量的特征。在三种分类算法（朴素贝叶斯、J48 和随机森林）的对比中，随机森林表现最佳，成功以 100% 的准确率检测出所有异常行为。未来工作将重点关注传输层（TCP/UDP 套接字）的特性及其对检测异常流量行为的影响，以期获得更好的结果和准确率，并证明仅分析该层并实时计算其统计特征即足以检测 Mirai 的异常行为。

# 参考文献

Alauthaman, M., Aslam, N., Zhang, L., Alasem, R., & Hossain, M. A. (2018). A P2P Botnet detection scheme based on decision tree and adaptive multilayer neural networks. *Neural Computing & Applications*, 29(11), 991–1004. doi:10.1007/s00521-016-2564-5

Alauthman, M., Almomani, A., Alweshah, M., Omoushd, W., & Alieyane, K. (2019). Machine Learning for phishing Detection and Mitigation. *Machine Learning for Computer and Cyber Security: Principle, Algorithms, and Practices*, 26.

Alauthman, M., Aslam, N., Al-kasassbeh, M., Khan, S., Al-Qerem, A., & Raymond Choo, K.-K. (2020). An efficient reinforcement learning-based Botnet detection approach. *Journal of Network and Computer Applications*, 150, 102479. doi:10.1016/j.jnca.2019.102479

Alieyan, K., Almomani, A., Anbar, M., Alauthman, M., Abdullah, R., & Gupta, B. B. (2019). DNS rule-based schema to botnet detection. *Enterprise Information Systems*, 1–20. doi:10.1080/17517575.2019.1644673

Atzori, L., Iera, A., & Morabito, G. (2010). The internet of things: A survey. *Computer Networks*, 54(15), 2787–2805. doi:10.1016/j.comnet.2010.05.010

Bertino, E., & Islam, N. (2017). Botnets and internet of things security. *Computer*, 50(2), 76–79. doi:10.1109/MC.2017.62

Bostani, H., & Sheikhan, M. (2017). Hybrid of anomaly-based and specification-based IDS for Internet of Things using unsupervised OPF based on MapReduce approach. *Computer Communications*, 98, 52–71. doi:10.1016/j.comcom.2016.12.001

Breiman, L. (2001). Random forests. *Machine Learning*, 45(1), 5–32. doi:10.1023/A:1010933404324

Butun, I., Kantarci, B., & Erol-Kantarci, M. (2015). Anomaly detection and privacy preservation in cloud-centric Internet of Things. *Proceedings 2015 IEEE International Conference on Communication Workshop (ICCW)*. doi:10.1109/ICCW.2015.7247572

Gonzalez, G. R., Organero, M. M., & Kloos, C. D. (2008). Early infrastructure of an internet of things in spaces for learning. *Proceedings 2008 Eighth IEEE International Conference on Advanced Learning Technologies*. doi:10.1109/ICALT.2008.210

Guyon, I., & Elisseeff, A. (2003). An introduction to variable and feature selection. *Journal of Machine Learning Research*, 3(Mar), 1157–1182.

Hall, M. A. (1999). Correlation-based feature selection for machine learning.

Kamal, A., Ammar, A., Rosni, A., Badr, A., & Mohammad, A. (2020). Botnet and Internet of Things (IoTs): A Definition, Taxonomy, Challenges, and Future Directions. In *Security, Privacy, and Forensics Issues in Big Data* (pp. 304–316). Hershey, PA: IGI Global.

Kolias, C., Kambourakis, G., Stavrou, A., & Voas, J. (2017). DDoS in the IoT: Mirai and other botnets. *Computer*, 50(7), 80–84. doi:10.1109/MC.2017.201

Leardi, R. (1996). Genetic algorithms in feature selection. In *Genetic algorithms in molecular modeling* (pp. 67–86). Elsevier. doi:10.1016/B978-012213810-2/50004-9

Lee, J.-H., & Kim, H. (2017). Security and privacy challenges in the internet of things [security and privacy matters]. *IEEE Consumer Electronics Magazine*, 6(3), 134–136. doi:10.1109/MCE.2017.2685019

Meidan, Y., Bohadana, M., Mathov, Y., Mirsky, Y., Shabtai, A., Breitenbacher, D., & Elovici, Y. (2018). N-BaIoT—Network-based detection of IoT botnet attacks using deep autoencoders. *IEEE Pervasive Computing*, 17(3), 12–22. doi:10.1109/MPRV.2018.03367731

