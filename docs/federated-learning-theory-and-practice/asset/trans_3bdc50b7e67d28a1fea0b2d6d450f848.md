

## 联邦学习测试床评估

我们现在在一个FL测试床中对直方图提升树模型进行实验，利用IBM FL库 [\[24\]](#Chp013_237-255_B9780443190377000223.xhtml#br0120), [\[29\]](#Chp013_237-255_B9780443190377000223.xhtml#br0145)。更具体地说，我们保留了40%的油溢出和电力数据集以及20%的EEG眼状态数据集作为全局保留集，仅用于评估最终FL模型的性能。每个客户端从原始数据集的其余部分随机采样以获得其各自的训练数据集。我们报告在单次训练/测试划分上任意HP（基线或FLoRA推荐）的平衡准确率。给定平衡准确率作为评估指标，我们在[算法 1](#Chp013_237-255_B9780443190377000223.xhtml#f0010)中使用`(1 – 平衡准确率)`作为损失 `ℒ[t]^(m)`。每个客户端将运行HPO以生成 `T = 500` 个（HP, 损失）对，并根据第 [13.3.2](#Chp013_237-255_B9780443190377000223.xhtml#s0050) 节所述的不同聚合过程，协作或自行利用这些对来生成损失曲面。一旦生成损失曲面，聚合器使用Hyperopt [\[3\]](#Chp013_237-255_B9780443190377000223.xhtml#br0015) 选择最佳HP候选，并通过IBM FL库使用选定的HPs训练联邦XGBoost模型。[表 13.3](#Chp013_237-255_B9780443190377000223.xhtml#t0020) 总结了3个数据集的实验结果，表明FLoRA在IBM FL测试床中相较于基线有显著提升。

### 表 13.3

FLoRA结合IBM-FL系统在保留测试集上的*平衡准确率*性能（越高越好）。基线仍为scikit-learn中`HistGradientBoostingClassifier`的默认HP配置。

| 数据 | *n* | \|*D*[*m*]\| ∀ *m* ∈ [*n*] | 基线 | SGM | SGM+U | MPLM | APLM |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| 油溢出 | 3 | 200 | 0.59 | **0.74** | 0.59 | 0.71 | 0.73 |
| EEG眼状态 | 3 | 3,000 | 0.89 | 0.92 | 0.92 | **0.93** | 0.92 |
| 电力 | 6 | 4,000 | 0.85 | 0.86 | **0.86** | 0.86 | 0.86 |

## 13.5 结论

如何在FL设置中有效选择超参数是一个极具挑战性的问题。在本章中，我们给出了FL-HPO问题的一般定义，并讨论了这一新领域中的几种FL-HPO方法。此外，我们提出了FLoRA，一种单次FL-HPO算法，可应用于多种ML模型，并提供了理论分析，其中包括FLoRA超参数选择所导致的最优性差距界。初步实验评估表明，FLoRA能够有效产生仅需单次运行即可超越基线的超参数配置。

本章讨论的FL-HPO解决方案各有其局限性。其中一些仅限于基于SGD的FL算法（如FedAvg），一些只能调整神经网络架构。FLoRA的一个局限性是它无法处理在任何局部HPO期间均不活跃的HPs。这些包括聚合器特定和某些FL训练特定的HPs。在没有任何额外信息或结构的情况下，单次FL-HPO不太可能处理此类HPs。因此，FL-HPO当前的挑战之一是探索如何将单次方法扩展为“少样本”FL-HPO以处理此类HPs，并结合某种形式的多保真度HP评估。

除了FL-HPO之外，还需要有效解决FL联合算法选择与超参数优化（CASH）问题，即联合优化训练算法及其HPs。由于搜索空间维度的增加以及每个训练算法拥有不同的HP集合，FL-CASH给FL-HPO带来了额外挑战。我们最近在[\[1\]](#Chp013_237-255_B9780443190377000223.xhtml#br0005)中为解决FL-CASH问题迈出了初步步伐。

## 参考文献

*   [\[1\]](#Chp013_237-255_B9780443190377000223.xhtml#cf0390) Md Alam, Koushik Kar, Theodoros Salonidis, Horst Samulowitz, DASH: decentralized CASH for federated learning, *International Workshop on Federated Learning: Recent Advances and New Challenges (FL-NeurIPS'22) in Conjunction with NeurIPS*. 2022.
*   [\[2\]](#Chp013_237-255_B9780443190377000223.xhtml#br0010) James Bergstra, Yoshua Bengio, Random search for hyper-parameter optimization, *Journal of Machine Learning Research* Feb 2012;13:281–305.
*   [\[3\]](#Chp013_237-255_B9780443190377000223.xhtml#br0015) James S. Bergstra, Rémi Bardenet, Yoshua Bengio, Balázs Kégl, Algorithms for hyper-parameter optimization, *Advances in Neural Information Processing Systems*. 2011:2546–2554.
*   [\[4\]](#Chp013_237-255_B9780443190377000223.xhtml#cf0235) Leo Breiman, Random forests, *Machine Learning* 2001;45(1):5–32.
*   [\[5\]](#Chp013_237-255_B9780443190377000223.xhtml#br0025) Tianqi Chen, Carlos Guestrin, XGBoost: A scalable tree boosting system, *Proceedings of the 22nd ACM SIGKDD International Conference on Knowledge Discovery and Data Mining, KDD'16*. New York, NY, USA: ACM; 2016:785–794.
*   [\[6\]](#Chp013_237-255_B9780443190377000223.xhtml#cs0035_1) Z. Dai, B.K.H. Low, P. Jaillet, Federated Bayesian optimization via Thompson sampling, *Advances in Neural Information Processing Systems* 2020;33.
*   [\[7\]](#Chp013_237-255_B9780443190377000223.xhtml#cs0035_2) Z. Dai, B.K.H. Low, P. Jaillet, Differentially private federated Bayesian optimization with distributed exploration, *Advances in Neural Information Processing Systems* 2021;34.
*   [\[8\]](#Chp013_237-255_B9780443190377000223.xhtml#cs0015_1) Alireza Fallah, Aryan Mokhtari, Asuman Ozdaglar, Personalized federated learning with theoretical guarantees: a model-agnostic meta-learning approach, *Advances in Neural Information Processing Systems* 2020;33:3557–3568.
*   [\[9\]](#Chp013_237-255_B9780443190377000223.xhtml#cs0070_1) Matthias Feurer, Katharina Eggensperger, Stefan Falkner, Marius Lindauer, Frank Hutter, Auto-sklearn 2.0: the next generation, [arXiv:2007.04074 \[cs.LG\]](http://www.arxiv.org/abs/2007.04074); 2020.
*   [\[10\]](#Chp013_237-255_B9780443190377000223.xhtml#cs0070_2) Matthias Feurer, Aaron Klein, Katharina Eggensperger, Jost Springenberg, Manuel Blum, Frank Hutter, Efficient and robust automated machine learning, *Advances in Neural Information Processing Systems*. 2015:2962–2970.
*   [\[11\]](#Chp013_237-255_B9780443190377000223.xhtml#br0045) Jerome H. Friedman, Greedy function approximation: a gradient boosting machine, *The Annals of Statistics* 2001:1189–1232.
*   [\[12\]](#Chp013_237-255_B9780443190377000223.xhtml#cs0040_1) Anubhav Garg, Amit Kumar Saha, Debo Dutta, Direct federated neural architecture search, [arXiv:2010.06223](http://www.arxiv.org/abs/2010.06223); 2020.
*   [\[13\]](#Chp013_237-255_B9780443190377000223.xhtml#cf0170) Gary Gensler, Lily Bailey, Deep learning and financial stability, 2020, Available at SSRN 3723132.
*   [\[14\]](#Chp013_237-255_B9780443190377000223.xhtml#cf0165) Bryce Goodman, Seth Flaxman, European Union regulations on algorithmic decision-making and a “right to explanation”, *AI Magazine* 2017;38(3):50–57.
*   [\[15\]](#Chp013_237-255_B9780443190377000223.xhtml#cs0040_2) Chaoyang He, Murali Annavaram, Salman Avestimehr, Towards non-i.i.d. and invisible data with FedNAS: federated deep learning via neural architecture search, [arXiv:2004.08546](http://www.arxiv.org/abs/2004.08546); 2020.
*   [\[16\]](#Chp013_237-255_B9780443190377000223.xhtml#cf0200) Frank Hutter, Holger H. Hoos, Kevin Leyton-Brown, Sequential model-based optimization for general algorithm configuration, *International Conference on Learning and Intelligent Optimization*. Springer; 2011:507–523.

