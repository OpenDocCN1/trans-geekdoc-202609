

# 参考文献

*   [19] Sai Praneeth Karimireddy, Lie He, Martin Jaggi, Byzantine-robust learning on heterogeneous datasets via bucketing, *International Conference on Learning Representations*. 2022.
*   [20] Li Tian, Shengyuan Hu, Ahmad Beirami, Virginia Smith, Ditto: fair and robust federated learning through personalization, *ICML*. 2021.
*   [21] Krishna Pillutla, Sham M. Kakade, Zaïd Harchaoui, Robust aggregation for federated learning, *IEEE Transactions on Signal Processing* 2022;70:1142–1154.
*   [22] Ximing Qiao, Yukun Yang, Hai Helen Li, Defending neural backdoors via generative distribution modeling, *NeurIPS*. 2019.
*   [23] Virat Shejwalkar, Amir Houmansadr, Manipulating the Byzantine: optimizing model poisoning attacks and defenses for federated learning, *NDSS*. 2021.
*   [24] Virat Shejwalkar, Amir Houmansadr, Peter Kairouz, Daniel Ramage, Back to the drawing board: a critical evaluation of poisoning attacks on production federated learning, *IEEE Symposium on Security and Privacy*. 2022.
*   [25] Ziteng Sun, Peter Kairouz, Ananda Theertha Suresh, H.B. McMahan, Can you really backdoor federated learning? [arXiv:1911.07963](http://www.arxiv.org/abs/1911.07963); 2019.
*   [26] Vale Tolpegin, Stacey Truex, Mehmet Emre Gursoy, Ling Liu, Data poisoning attacks against federated learning systems, *European Symposium on Research in Computer Security*. Springer; 2020:480–501.
*   [27] Hongyi Wang, Kartik Sreenivasan, Shashank Rajput, Harit Vishwakarma, Saurabh Agarwal, Jy-yong Sohn, Kangwook Lee, Dimitris Papailiopoulos, Attack of the tails: yes, you really can backdoor federated learning, *Advances in Neural Information Processing Systems* 2020;33:16070–16084.
*   [28] Yunjuan Wang, Poorya Mianjy, R. Arora, Robust learning for data poisoning attacks, *ICML*. 2021.
*   [29] E. Weiszfeld, Sur le point pour lequel la somme des distances de *n* points donnés est minimum, *Tohoku Mathematical Journal, First Series* 1937;43:355–386.
*   [30] Chulin Xie, Minghao Chen, Pin-Yu Chen, Bo Li, CRFL: certifiably robust federated learning against backdoor attacks, *International Conference on Machine Learning*. PMLR; 2021:11372–11382.
*   [31] Chulin Xie, Keli Huang, Pin-Yu Chen, Bo Li, DBA: distributed backdoor attacks against federated learning, *International Conference on Learning Representations*. 2019.
*   [32] Chulin Xie, Yunhui Long, Pin-Yu Chen, Krishnaram Kenthapadi, Bo Li, Certified robustness for free in differentially private federated learning, *NeurIPS 2021 New Frontiers in Federated Learning Workshop*. 2021.
*   [33] Cong Xie, *Toward communication-efficient and secure distributed machine learning*. [PhD thesis] University of Illinois at Urbana-Champaign; 2021.
*   [34] Cong Xie, Oluwasanmi Koyejo, Indranil Gupta, SLSGD: secure and efficient distributed on-device machine learning, *ECML/PKDD*. 2019.
*   [35] Cong Xie, Oluwasanmi Koyejo, Indranil Gupta, Zeno: distributed stochastic gradient descent with suspicion-based fault-tolerance, *ICML*. 2019.
*   [36] Dong Yin, Yudong Chen, Ramchandran Kannan, Peter Bartlett, Byzantine-robust distributed learning: towards optimal statistical rates, Jennifer Dy, Andreas Krause, eds. *Proceedings of the 35th International Conference on Machine Learning*. *Proceedings of Machine Learning Research*. PMLR; 2018.

# 第6章：评估梯度反演攻击与防御

Yangsibo Huang^[a]；Samyak Gupta^[b]；Zhao Song^[c]；Sanjeev Arora^[b]；Kai Li^[b]

^[a] 电子与计算机工程系，普林斯顿大学，新泽西州普林斯顿，美国
^[b] 普林斯顿大学，新泽西州普林斯顿，美国
^[c] Adobe Research，加利福尼亚州圣何塞，美国

## 摘要

梯度反演攻击（或从梯度中恢复输入）是联邦学习安全与隐私保护面临的一项新兴威胁，恶意窃听者或协议参与者可借此部分恢复客户端的私有数据。本章总结了联邦学习中现有的攻击手段，并探讨了其潜在局限性。随后，本章对多种针对梯度反演攻击的防御机制的优势进行了评估，以展示其在隐私泄露与数据效用之间的权衡。最后，本章提出了若干供进一步研究的开放问题。

### 关键词

联邦学习；隐私；重构攻击

## 6.1 简介

联邦学习[[27](#Chp006_105-122_B9780443190377000144.xhtml#br0135)，[34](#Chp006_105-122_B9780443190377000144.xhtml#br0170)]是一种框架，它允许分布式环境中的多个客户端协同训练中央服务器上的神经网络模型，同时将训练数据保留在各客户端的本地机器上。在每个训练步骤中，每个客户端使用全局模型的最新副本在其本地数据上计算模型更新（即梯度），然后将梯度发送至中央服务器。服务器聚合这些更新（通常通过平均）以构建全局模型，随后将新的模型参数发送给所有客户端。通过允许客户端在不直接共享数据的情况下参与训练，此类协议更好地符合了《健康保险流通与责任法案》（HIPAA）[[2](#Chp006_105-122_B9780443190377000144.xhtml#br0010)]、《通用数据保护条例》（GDPR）[[10](#Chp006_105-122_B9780443190377000144.xhtml#br0050)]和《加州消费者隐私法案》（CCPA）[[31](#Chp006_105-122_B9780443190377000144.xhtml#br0155)]等数据隐私法规。

虽然共享梯度最初被认为泄露的客户端私有数据信息很少，但近期的论文[[18](#Chp006_105-122_B9780443190377000144.xhtml#br0090)，[45](#Chp006_105-122_B9780443190377000144.xhtml#br0225)，[49](#Chp006_105-122_B9780443190377000144.xhtml#br0245)，[51](#Chp006_105-122_B9780443190377000144.xhtml#br0255)]开发出了一种“梯度反演攻击”，拥有传输梯度和模型参数访问权限的攻击者可借此重构客户端的私有训练数据。此场景下的攻击者可能是联邦学习方案中的恶意参与者——包括想要重构客户端私有数据的诚实但好奇的服务器，或想要重构其他客户端私有数据的诚实但好奇的客户端。该攻击的发现引发了对联邦学习所能确保的隐私水平的广泛关注。本章将概述评估和最小化梯度反演攻击风险的方法。

