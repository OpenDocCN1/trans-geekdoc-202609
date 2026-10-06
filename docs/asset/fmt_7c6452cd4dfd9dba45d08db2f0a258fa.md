
| DDOS | DDOS | 1 | 0.006 | 0.952 | 0.997 |

| 机器人 (BOT) | BOT | | 0 | 1 | 1 | |

![](img/aeaf5e4a1e1020ca53a1da35e316de95_160_0.png)

图 6.29 测试用例 #10 的实际威胁与预测威胁。

# 有效入侵检测

![](img/aeaf5e4a1e1020ca53a1da35e316de95_161_0.png)

图 6.30 测试用例 #10 的预测边界。

| 攻击 | 被检测为 | a | b | c | d | e | f | g | h | i | j | k | l | m | n | o |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 正常 (BENIGN) | a | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 2 | 2 |
| SSM (PATATOR) | b | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| FTP (PATATOR) | c | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 心跳 (HEARTBEAT) | d | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| SLOWHTTPTEST (DOS) | e | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 7 | 0 | 0 | 0 | 0 | 0 |
| HULK (DOS) | f | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 5 | 2 | 0 | 0 | 0 | 0 | 0 |
| GOLDENEY (DOS) | g | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 3 | 1 | 0 | 0 | 0 | 0 | 0 |
| 渗透 (INFILTRATION) | h | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| BF (WEB ATTACK) | i | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 6 | 0 | 0 | 0 | 0 | 0 |
| XSS (WEB ATTACK) | j | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 4 | 0 | 0 | 0 | 0 |
| SQL IN (WEB ATTACK) | k | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 5 | 0 | 0 |
| 端口扫描 (PORTSCAN) | l | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| DDOS | m | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| BOT | n | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 |

图 6.31 检测器为测试用例 #10 生成的混淆矩阵。

### 表 6.12 测试用例性能

| 测试用集 | 实例数量 | 准确率 | 分类率 | 均方误差 | IPR | PPV | ROC |
|---|---|---|---|---|---|---|---|
| 测试用例 #01 | 359 | 97.493 | 2.507 | 0.043 | 0.056 | 0.975 | 0.993 |
| 测试用例 #02 | 359 | 96.939 | 3.064 | 0.0048 | 0.0582 | 0.969 | 0.995 |
| 测试用例 #03 | 359 | 97.215 | 2.785 | 0.0044 | 0.0567 | 0.972 | 0.994 |
| 测试用例 #04 | 359 | 97.493 | 2.507 | 0.0044 | 0.0551 | 0.975 | 0.995 |
| 测试用例 #05 | 359 | 98.602 | 1.3928 | 0.0028 | 0.0372 | 0.938 | 0.982 |
| 测试用例 #06 | 359 | 97.215 | 2.785 | 0.0049 | 0.0578 | 0.972 | 0.992 |
| 测试用例 #07 | 359 | 97.7654 | 2.236 | 0.0034 | 0.0532 | 0.978 | 0.995 |
| 测试用例 #08 | 359 | 95.2514 | 4.7486 | 0.0067 | 0.0711 | 0.953 | 0.999 |
| 测试用例 #09 | 359 | 96.9274 | 3.072 | 0.0063 | 0.0686 | 0.969 | 0.994 |
| 测试用例 #10 | 359 | 96.3687 | 3.6133 | 0.0058 | 0.0681 | 0.964 | 0.991 |
| 平均值 | 97.1271 | 2.8729 | 0.00471 | 0.05738 | 0.9713 | 0.0024 | 0.9737 | 0.992 |

# 用于增强网络防御的大数据与边缘智能

| 测试用例 #01 | 测试用例 #02 | 测试用例 #03 | 测试用例 #04 | 测试用例 #05 | 测试用例 #06 | 测试用例 #07 | 测试用例 #08 | 测试用例 #09 | 测试用例 #10 | 平均 |
|---|---|---|---|---|---|---|---|---|---|---|
| 2.507 | 3.041 | 2.785 | 2.507 | 1.398 | 2.785 | 2.234 | 1.486 | 3.027 | 3.631 | 2.829 |
| 97.493 | 96.959 | 97.215 | 97.493 | 98.602 | 97.215 | 97.7654 | 95.214 | 96.927 | 96.368 | 97.121 |

- 分类率

6.32 提议的引擎的准确率和分类率。

# 6.33 提议的引擎的真阳性率、精确率、假阳性率和均方误差。

提出了一种 IDS 引擎以应对高不平衡的分类问题。这里考虑的数据集是 CICIDS2017，这是一个最新的数据集，包含一个名为正常的实例和 14 类其他类的实例。挑战在于为这个包含超过 28 万个实例和 85 个特征且存在于高类别不平衡的数据集设计 IDS 框架。为了应对这个问题，首先通过一种名为无限潜在特征选择的概率潜图图排序方法对特征进行排序，然后选择所需的特征进行样本生成。采样通过蓄水采样技术进行，该技术将数据集视为数据流，确保每个实例被选中的概率相等。

## 有效入侵检测

样本的一部分。同样，Weka 模拟器中使用的另一种基于划分的采样机制 SRF 用于根据 10 个测试用例生成数据。测试用例的生成方式确保了在训练实例中不会发现任何测试用例实例，即测试采样机制。在检测阶段，部署了基于 C45 的分类机制 J48 Consolidated，并利用 CTC 算法赋能以应对涉及高度类别不平衡的分类问题。结果发现，我们的 IDS 检测威胁的准确率为 97.12%，误分类率极低，为 2.87%。我们的方法产生的误报率为 0.002%。

## 参考文献

- 1. Scife, P. Traynor, and K. Butler, “Making sense of the ransomware measure (and enabling a sensible forward),” IEEE Potentials, vol. 36, no. 6, pp. 28–31, Nov. 2017. doi: 10.1109/MPOT.2017.2737201
- 2. Q. Chen and R. A. Briggs, “Automated behavioral analysis of malware: A case study of Wannacry ransomware,” in 2017 IEEE International Conference on Machine Learning and Applications (ICMLA), Dec. 2017, pp. 454–460. doi: 10.1109/ICMLA.2017.0-119
- 3. M. Uyas and S. A. Alharbi, “Machine learning approaches to network intrusion detection for contemporary internet traffic,” vol. 104, no. 5, pp. 1061–1076, May 2022. doi: 10.1017/s00607-021-01050-5
- 4. R. Panigahi, S. Shorbari, A. Boko, and P. Mallick, “Intrusion detection systems (IDS)–overview with a generalized framework,” Cognitive Informatics and Soft Computing, pp. 107–117, 2020.
- 5. A. Ahmed et al., “Multi-attribute decision-making for intrusion detection: A systematic review,” International Journal of Information Technology & Decision Making, vol. 22, no. 01, pp. 589–636, Jun. 2013. doi: 10.1142/S01962220022300044
- 6. M. Poongdi, V. Vijayakumar, F. Al-Tijuran, M. Handi, and M. Ma, “Intrusion detection system for DDoS attack on VAN with RECAPTCHA using information methods,” IEEE ACCESS, vol. 7, pp. 15841–15891, 2019. doi: 10.1109/ACCESS.2019.2945682
- 7. N. A. Aziz, T. M. Bana, S. Misra, A. Adewumi, C. Van der Viber, and R. Ahuja, “Intrusion Detection and Prevention Systems: An Updated Review,” 2020, pp. 685–696. doi: 10.1007/978-981-32-9949-8
- 8. R. Panigahi and S. Ghosh, “A statistical analysis of lazy classifiers using Canadian institute of cybersecurity,” in Data Science and Management, Springer, 2020, pp. 215–222.
- 9. H.-J. Liao, C.-H. Richard, Y.-C. Lin, and K.-Y. Tung, “Intrusion detection system: a comprehensive review,” Journal of Network and Computer Applications, vol. 36, no. 1, pp. 16–24, Jan. 2003. doi: 10.1016/jjnca.2002.094
- 10. C. A. Catania, and C. G. Garino, “Automated network intrusion detection: techniques and open issues,” Computers & Electrical Engineering, vol. 38, no. 5, pp. 1062–1083, Sep. 2012. doi: 10.1109/j..2012.013
- 11. I. Ibaruren, J. Muguera, I. Guruttaza, and A. Orbelait, “Coverage-based resampling: Building robust classification trees,” Knowledge-Based Systems, vol. 79, pp. 51–67, May 2015. doi: 10.1016/j.knosys.2014.123
- 12. J. M. Pérez, J. Muguera, A. Orbelait, and J. Martin, “Combining multiple class distribution subsamples in a single tree,” Pattern Recognition Letters, vol. 28, no. 4, pp. 414–442, Mar. 2007. doi: 10.1016/j.patrec.2006.013

## 大数据与边缘智能增强防御

- 13. C. D. Kim, J. Jeong, and G. Kim, "Imbalanced Continuous Learning with Partitioning Sampling,” 2020, pp. 411–428. doi: 10.1007/978-3-030-58601-25
- 14. R. Vijayan, D. Devaraj, and B. Kannapa, "Intusion detection system for wireless network using multiple support vector classifier with algorithm-based selection," Computers & Security, 77, pp. 304–314, 2019. doi: 10.1016/j.cose.2018.0410
- 15. E. Kabir, J. Hu, and G. Guan, "A novel statistical technique for intrusion detection," Future Generation, 79, pp. 303–318, Feb.2018. doi: 10.1016/j.future.2017.0129
- 16. S. M. Hosseini, "An effective intrusion detection framework based on PLCM/SVM optimized by time-varying chaos optimization," Neurocomputing, 199, pp. 90–102, June 2016. doi: 10.1016/j.necom.2016.0331
- 17. D. S. Kim and J. Park, "Network-based intrusion detection with support vector machines," 2003, pp. 747–756. doi: 10.1007/978-3-540-4235-7
- 18. S. M. Hosseini, H. Wang, and Y. Shi, "Ramp Loss-support vector regression: a robust and sparse multi-class approach to the intrusion detection," Knowledge-Based Systems, 126, pp. 113–126, Jun 2017. doi: 10.1016/j.ksbas.2017.0312
- 19. S. Mukammala, G. Janoski, and A. Sung, "Intrusion detection using neural networks and support machines," in Proceedings of the 2002 International Conference on Neural Networks, IJCNN (No. 02370), pp. 1702–1707. doi: 10.1109/IJCNN.2002.10074
- 20. T. Ambwani, "Multi support vector machine implementation for intrusion detection," in Proceedings of the International Conference on Neural Networks, vol. 2003, pp. 2300–2305. doi: 10.1109/IJCNN.2003.12377
- 21. A. Mewada, P. Gedam, S. Khan, and U. M. Reddy, "Network intrusion detection using multiclass support vector machine," International Journal of Computer and Communication Technology, pp. 262–265, 2010. doi: 10.47893/IJCT.2010.1054
