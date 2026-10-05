

## URL检测中大数据分析的深度学习架构 331

## 14.7 基于机器学习的网络安全提议架构

在计算机安全领域，计算机技术的使用日益增长，这使得它在我们社会中变得至关重要。根据2008年的国家统计数据，英国65%的家庭已连接到互联网，大约相当于1600万户（国家统计数据 2008）。此外，近年来，计算机恶意软件的数量在快速增加。计算机用户始终面临着风险，即使系统没有连接到互联网也是如此。此外，无人看守的系统容易受到未经授权的访问和系统滥用。如果计算机连接到网络，攻击的风险将进一步增加。在这种情况下，世界各地的任何用户都可以远程访问任何计算机，并尝试访问个人和机密信息。这些攻击通常通过侵入、钓鱼类URL实施。为了应对侵入和钓鱼类URL的增加，我们为机构提出了一个网络威胁态势感知平台。所提系统的高层架构如图14.9所示。

- 原型模型使用了深度学习和机器学习算法。
- 由于监督学习技术获取标注数据存在困难，原型模型还引入了无监督学习技术。

![](img/6d0ce7dba01af52e1c2fae47d5b04a05_347_0.png)

图 14.9 基于机器学习的网络安全提议架构

## 14.8 结论与未来工作

这项工作分析了监督和无监督学习技术在侵入和钓鱼URL中的有效性。经典机器学习分类器对KDD-Cup-99侵入数据的检测率与其他方法密切相当。实验通过完整数据集和最少特征进行了评估，以理解每个特征的重要性。基于DNN的分类优于所有经典的机器学习技术。这可以通过促进训练、在现有架构中堆叠更多层数，或向现有数据中添加新特征来改进。在大多数情况下，低频攻击类别产生单条连接记录；然而，当隐藏在其他连接记录中时，DNN在检测率上的性能优于KDD-Cup-99挑战赛获奖作品和其他发表的结果。由于深度学习架构计算开销高，我们未能采用其他架构。未来的工作可以包含使用CNN、LSTM、GRU、IRNN等其他深度学习架构的分类，以及如CNN-LSTM等混合网络。当模型被构建为无监督学习问题时，检测率很高。M-ZOOM框架展示了无监督学习的潜力。在钓鱼URL检测方面，CNN-LSTM表现最佳。在这项工作中，我们从机构角度出发，提出了一种基于AI的态势感知平台，用于检测侵入和钓鱼URL。所提架构中的投票方案是未来工作的方向。

## 致谢

本研究得到了Paramount Computer Systems和Lakhshya Cybersecurity Labs的支持。我们感谢NVIDIA India为研究资助提供的GPU硬件支持。我们感谢计算工程与网络（CEN）部门对研究的鼓励。

## 参考文献

- [1] Lee W, Fan W, Miller M, et al. Toward cost-sensitive modeling for intrusion detection and response. Journal of Computer Security. 2002;10(1–2):5–22.
- [2] LeCun Y, Bengio Y, Hinton G. Deep learning. Nature. 2015;521(7553):436–444.
- [3] Staudeyer RC. Applying long short-term recurrent neural networks for intrusion detection. South African Computer Journal. 2015;56(1):136–154.
- [4] Vinayakumar R, Soman K, Poornachandar P. Applying convolutional neural network for network intrusion detection. In: Advances in Computing, Communications and Informatics (ICACCI), 2017 International Conference. IEEE; 2017, p. 1222–1228.
- [5] Vinayakumar R, Soman K, Poornachandran P. Evaluating effectiveness of shallow and deep networks to intrusion detection. In: Advances in Computing, Communications and Informatics (ICACCI), 2017 International Conference. IEEE; 2017. p. 1282–1289.
- [6] Vinayakumar R, Soman K, Poornachandran P. Evaluation of recurrent neural network and its variants for intrusion detection (IDS). International Journal of System Modeling and Design (IJISMD). 2017;8(3);43–63.
- [7] Vinayakumar R, Soman K, Poornachandran P. Long short-term memory based anomaly detection. In: Advances in Computing, Communications and Informatics (ICACCI), 2017 International Conference. IEEE; 2017. p. 236–242.
- [8] Wang Z. The applications of deep learning on traffic. BlackHat, USA; 2015.
- [9] Vinayakumar R, Soman K, Poornachandran P. Applying deep learning for prediction. In: Advances in Computing, Communications and Informatics (ICACCI), 2017 International Conference. IEEE; 2017. p. 2353–2358.
- [10] Vinayakumar R, Soman K. Secure (SSH) traffic analysis with flow features using shallow and deep networks. In: Advances in Computing, Communications and Informatics (ICACCI), 2017 International Conference. IEEE; 2017. p. 2026–2032.
- [11] Vinayakumar R, Soman K. Evaluating shallow and deep networks for secure (SSH) traffic analysis. In: Advances in Computing, Communications and Informatics (ICACCI), 2017 International Conference. IEEE; 2017. p. 266–274.
- [12] ECN Shor, Dong S, Moazze R. Recognizing features with neural networks. In: USENIX Security Symposium;2015. p. 611–626.
- [13] Vinayakumar R, Soman K, Poornachandran P. Detecting malicious names using deep learning approaches at scale. Journal of Intelligent & Fuzzy Systems. 2018;34(3):1355–1367.
- [14] Vinayakumar R, Soman K, Poornachandran P, et al. Evaluating deep learning approaches to characterize and classify the DGAs at scale. Journal of Intelligent & Fuzzy Systems. 2018;34(3):1265–1276.
- [15] Vinayakumar R, Poornachandran P, Soman K. Scalable framework for cyber threat situational awareness on domain name systems. In: Big Data in Engineering Applications. Springer; 2018. p. 113–142.
- [16] Mohan VS, Vinayakumar R, Soman K, et al. Spoof: Syntactic patterns for identification of online factors. In: 2018 Security and Privacy Workshops (SPW). IEEE; 2018. p. 258–263.
- [17] Vinayakumar R, Soman K P. Evaluating deep learning approaches to characterize and classify malicious URLs. Journal of Intelligent & Fuzzy Systems. 2018;34(3):1333–1343.
- [18] Pascanu R, Stokes JW, Sanossian H, et al. Malware classification with recurrent networks. In: Acoustics, Speech and Signal Processing (ICASSP), 2015. p. 1916–1920.
- [19] Vinayakumar, Soman K, Poornachandran P, et al. Detecting Android malware using long-term memory (LSTM). Journal of Intelligent & Fuzzy Systems. 2018;34(3):1277–1288.
- [20] Vinayakumar, Soman K, Poornachandran P. Deep Android malware detection and classification. In: Advances in Computing, Communications and Informatics (ICACCI), 2017 International Conference. IEEE; 2017. p. 1677–1688.
- [21] Vinayakumar R, Soman, KS, et al. Evaluating shallow and deep networks for intrusion detection and classification. In: Advances in Computing, Communications and Informatics (ICACCI), 2017 International Conference. IEEE; 2017, p. 259–265.
- [22] Hodo E, Bellekens K, Hamilton A, et al. Shallow and deep intrusion detection: A taxonomy and survey. arXiv preprint arXiv:1701.02145. 2017.
- [23] Shin K, Hooi B, Faloutsos C.M: Fast dense-block detection in tensors with quality guarantees. In: Joint European Conference on Machine Learning and Knowledge Databases. Cham: Springer; 2016; p. 264–280.
- [24] Sabhni M, Serpent G. Application of machine learning algorithms to KDD intrusion detection within misuse context. In: MLMTA; 2003; p. 209–215.
- [25] Sinclair C, Pierce L, Matner S. Application of machine learning to work intrusion detection. In: 1999.(ACS99) 15th Annual Conference. IEEE; 1999, p. 371–377.
- [26] Denning DE. An intrusion-detection model. IEEE Transactions on Software Engineering. 1987;(22):222–232.
- [27] Andersen R, Chung F, Lang K. Local graph partitioning using PageRank vectors. In: Foundations of Computer Science, 2006. FOCS’06 47th Annual IEEE Symposium on. IEEE; 2006; p. 475–486.
- [28] Leskovec J, McAlee J. Learning to discover social circles in networks. In: Advances in Neural Information Systems; 2012; p. 539–547.
- [29] Cortes C, Pegibon D, Volinsky C. Communities of interest. In: International Symposium on Intelligent Data Analytics. Springer; 2001; p. 105–114.
- [30] Akoglu L, McGoghlan M, Faloutsos C. Spotting anomalies in weighted graphs. In: Pacific-Asia Conference on Discovery and Data Mining. Springer; 2010. p. 410–421.
- [31] Beutel A, Hu W, Gurwami V, et al. CopyCatch: stopping group attacks by stopping behavior in social networks. In: Proceedings of the 22nd International Conference on World Wide Web. ACM; 2013, p. 119–130.
- [32] Papalakis EE, Beutel A, Steenkiste P. Network anomaly detection using co-clustering. In: Encyclopedia of Social Network Analysis and Mining. Springer; 2014. p. 1054–1068.

