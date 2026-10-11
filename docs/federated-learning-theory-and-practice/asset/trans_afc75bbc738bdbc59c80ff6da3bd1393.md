
该框架在作者运行其设置的受控环境中，很好地减少了上述资源。他们还通过不需要客户端进行超参数探索、不需要额外的超参数调优阶段，很好地解决了可扩展性挑战，从而显著降低了资源成本。然而，他们做出了一些在实际场景中不成立的假设。例如，他们要求资源同质性以获得可预测的结果，这对现实世界的用例是一个强限制。他们完全忽略了超时和参与率，并假设在训练阶段中途不会有客户端退出。他们还假设数据分布在整个训练过程中保持不变，并且所有客户端始终可用。这项工作证明了为跨设备联邦学习创建资源感知的超参数调优是可能的，是朝这个方向迈出的很好的第一步。然而，他们要求的标准在现实场景中很难满足，因此在能够适用于约束较少的框架方面仍有探索空间。

### **FedEx** [\[15\]](#Chp012_219-235_B9780443190377000211.xhtml#br0075)

该论文是联邦学习中解决超参数调优挑战的首批工作之一。其重点是通过并行化搜索阶段，减少探索客户端超参数所花费的时间。他们从一组想要探索的超参数集开始，将不同的集合发送给选定进行一轮训练的不同客户端。客户端按常规进行本地训练，并将其权重和损失返回给服务器。在服务器端，利用本地模型权重与基线模型之间的差异计算梯度，并结合服务器端学习率使用这些梯度来更新全局模型权重。通过这种方式，可以在训练过程中尝试多个超参数。目的不是寻找好的超参数，而是在不同客户端上使用多个超参数进行良好训练。

虽然该论文并未直接执行超参数调优，且未考虑资源使用，但它与我们的情况仍然相关，因为它展示了为每个客户端使用不同超参数也能取得良好结果。它还在训练期间对超参数搜索空间进行优化，无需额外资源。然而，这一过程是资源无感知的。例如，将高批量大小值和本地步数分配给较慢的客户端可能会造成负担，且未考虑对整体资源消耗影响极大的服务器端超参数。此外，在训练期间执行优化是否会增加收敛所需的总轮数尚不清楚。

### **其他工作。**

虽然这些工作是跨设备联邦学习环境下超参数调优领域最新且最相关的，但也存在其他相关工作，我们简要回顾一下。其中一项工作是论文“*On Large-Cohort Training for Federated Learning*” [\[6\]](#Chp012_219-235_B9780443190377000211.xhtml#br0030)，作者探讨了每轮采样的客户端数量如何影响联邦学习训练，但完全略过了资源效率部分。论文“*Federated Learning with Hyperparameter-based Clustering for Electrical Load Forecasting*” [\[11\]](#Chp012_219-235_B9780443190377000211.xhtml#br0055) 尝试预测电力负载，但未讨论资源异质性的挑战。论文“*Robust Federated Learning through Representation Matching and Adaptive Hyperparameters*” [\[27\]](#Chp012_219-235_B9780443190377000211.xhtml#br0135) 使用 `REINFORCE` 算法 [\[34\]](#Chp012_219-235_B9780443190377000211.xhtml#br0170) 进行在线超参数调优，其探索/利用阶段代价高昂；而论文“*Federated Bayesian Optimization via Thompson Sampling*” [\[8\]](#Chp012_219-235_B9780443190377000211.xhtml#br0040) 在设备上使用贝叶斯优化，代价也很高。总之，虽然联邦学习中的超参数优化已有一些工作，但鲜有作者深入探讨资源成本对联邦学习的影响。

## 12.6 结论

在本章中，我们从系统角度讨论了跨设备联邦学习中超参数优化的问题。我们首先列出并解释了需考虑的相关可量化资源。随后枚举了客户端和服务器端的超参数，并解释了它们对训练和资源消耗的影响。我们讨论了联邦学习中的挑战及其在资源成本方面的影响，并指出了当前相关文献中最相关的工作。对这些工作的讨论表明，在为跨设备联邦学习设计资源高效的超参数优化技术方面，仍有大量工作有待完成。

## 参考文献

*   [\[1\]](#Chp012_219-235_B9780443190377000211.xhtml#cs0050_1) Takuya Akiba, Shotaro Sano, Toshihiko Yanase, Takeru Ohta, Masanori Koyama, Optuna: a next-generation hyperparameter optimization framework, *Proceedings of the 25th ACM SIGKDD International Conference on Knowledge Discovery & Data Mining*. 2019:2623–2631.

*   \[2\] Keith Bonawitz, Hubert Eichner, Wolfgang Grieskamp, Dzmitry Huba, Alex Ingerman, Vladimir Ivanov, Chloe Kiddon, Jakub Konečnỳ, Stefano Mazzocchi, Brendan McMahan, et al., Towards federated learning at scale: system design, *Proceedings of Machine Learning and Systems*. 2019;vol. 1:374–388.

*   

*   [\[3\]](#Chp012_219-235_B9780443190377000211.xhtml#cs0060_2) Zheng Chai, Ahsan Ali, Syed Zawad, Stacey Truex, Ali Anwar, Nathalie Baracaldo, Yi Zhou, Heiko Ludwig, Feng Yan, Yue Cheng, TiFL: a tier-based federated learning system, *Proceedings of the 29th International Symposium on High-Performance Parallel and Distributed Computing*. 2020:125–136.

*   [\[4\]](#Chp012_219-235_B9780443190377000211.xhtml#cs0065_1) Zheng Chai, Yujing Chen, Ali Anwar, Liang Zhao, Yue Cheng, Huzefa Rangwala, FedAT: a high-performance and communication-efficient federated learning system with asynchronous tiers, *Proceedings of the International Conference for High Performance Computing, Networking, Storage and Analysis*. 2021:1–16.

*   [\[5\]](#Chp012_219-235_B9780443190377000211.xhtml#cs0060_3) Zheng Chai, Hannan Fayyaz, Zeshan Fayyaz, Ali Anwar, Yi Zhou, Nathalie Baracaldo, Heiko Ludwig, Yue Cheng, Towards taming the resource and data heterogeneity in federated learning, *2019 USENIX Conference on Operational Machine Learning (OpML 19)*. 2019:19–21.

*   [\[6\]](#Chp012_219-235_B9780443190377000211.xhtml#cf0130) Zachary Charles, Zachary Garrett, Zhouyuan Huo, Sergei Shmulyian, Virginia Smith, On large-cohort training for federated learning, *Advances in Neural Information Processing Systems* 2021;34:20461–20475.

*   \[7\] Yujing Chen, Yue Ning, Martin Slawski, Huzefa Rangwala, Asynchronous online federated learning for edge devices with non-iid data, *2020 IEEE International Conference on Big Data (Big Data)*. IEEE; 2020:15–24.

*   [\[8\]](#Chp012_219-235_B9780443190377000211.xhtml#cf0150) Zhongxiang Dai, Bryan Kian Hsiang Low, Patrick Jaillet, Federated Bayesian optimization via Thompson sampling, *Advances in Neural Information Processing Systems* 2020;33.

*   [\[9\]](#Chp012_219-235_B9780443190377000211.xhtml#cf0100) Thomas Elsken, Jan Hendrik Metzen, Frank Hutter, Neural architecture search: a survey, *Journal of Machine Learning Research* 2019;20(1):1997–2017.

*   \[10\] Alireza Fallah, Aryan Mokhtari, Asuman Ozdaglar, Personalized federated learning: a meta-learning approach, [arXiv:2002.07948](http://www.arxiv.org/abs/2002.07948); 2020.
