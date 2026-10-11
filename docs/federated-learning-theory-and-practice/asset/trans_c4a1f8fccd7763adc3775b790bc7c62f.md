
然而，上述关于后门攻击不可避免性的理论发现，以及第 [4.4.1](#Chp004_75-90_B9780443190377000120.xhtml#s0080) 节中提到的检测后门的其他瓶颈的含义，仍需结合生产规模的联邦学习（FL）系统进行批判性分析。换句话说，所提攻击中假设的威胁模型需要针对真实部署进行验证，以得出准确的威胁评估。为了更直观地理解问题，以 Google Keyboard 为例，其拥有约 10 亿的安装用户基数，采用 FL 进行下一词预测。假设该场景下 10% 的客户端受到攻击，将意味着有 1000 万恶意客户端——这在受感染用户数量上可能是一个不切实际的假设。为此，一些初步结果表明，在现实威胁模型下（例如，恶意客户端比例从 0.1% 变化至最高 1%），现有的非目标投毒攻击（及其改进变体）应用于生产系统时，会导致全局模型在基准图像数据集上的准确率出现可忽略不计的下降（<1%）[[37]](#Chp004_75-90_B9780443190377000120.xhtml#br0185)。这些结果与在非生产系统上攻击时的一些观察结果相冲突[[38]](#Chp004_75-90_B9780443190377000120.xhtml#br0190)。但可以确定的是，仍存在开发更强攻击的空间，这些攻击将在部署系统的严格约束下运行。同样，更强的攻击应进一步推动对鲁棒聚合方案的研究，这些方案能在抵御攻击的同时保持模型准确性。

## 参考文献

*   [[1]](#Chp004_75-90_B9780443190377000120.xhtml#cs0055_1) D. Alistarh, Z. Allen-Zhu, J. Li, Byzantine stochastic gradient descent, *Advances in Neural Information Processing Systems* 2018;31.

*   [[2]](#Chp004_75-90_B9780443190377000120.xhtml#cs0055_2) E. Bagdasaryan, A. Veit, Y. Hua, D. Estrin, V. Shmatikov, How to backdoor federated learning, *International Conference on Artificial Intelligence and Statistics*. PMLR; 2020:2938–2948.

*   [[3]](#Chp004_75-90_B9780443190377000120.xhtml#cs0055_3) G. Baruch, M. Baruch, Y. Goldberg, A little is enough: circumventing defenses for distributed learning, *Advances in Neural Information Processing Systems* 2019;32.

*   [[4]](#Chp004_75-90_B9780443190377000120.xhtml#cs0055_4) A.N. Bhagoji, S. Chakraborty, P. Mittal, S. Calo, Analyzing federated learning through an adversarial lens, *International Conference on Machine Learning*. PMLR; 2019:634–643.

*   [[5]](#Chp004_75-90_B9780443190377000120.xhtml#cs0055_5) B. Biggio, B. Nelson, P. Laskov, Poisoning attacks against support vector machines, *Proceedings of the 29th International Conference on International Conference on Machine Learning, ICML'12*. 2012:1467–1474.

*   [[6]](#Chp004_75-90_B9780443190377000120.xhtml#cs0055_6) P. Blanchard, E.M. El Mhamdi, R. Guerraoui, J. Stainer, Machine learning with adversaries: Byzantine tolerant gradient descent, *Proceedings of the 31st International Conference on Neural Information Processing Systems*. 2017:118–128.

*   [[7]](#Chp004_75-90_B9780443190377000120.xhtml#cf0045) K. Bonawitz, V. Ivanov, B. Kreuter, A. Marcedone, H.B. McMahan, S. Patel, D. Ramage, A. Segal, K. Seth, Practical secure aggregation for privacy-preserving machine learning, *Proceedings of the 2017 ACM SIGSAC Conference on Computer and Communications Security*. 2017:1175–1191.

*   [[8]](#Chp004_75-90_B9780443190377000120.xhtml#cf0205) X. Cao, M. Fang, J. Liu, N.Z. Gong, FLTrust: Byzantine-robust federated learning via trust bootstrapping, [arXiv:2012.13995](http://www.arxiv.org/abs/2012.13995); 2020.

*   [[9]](#Chp004_75-90_B9780443190377000120.xhtml#cf0290) C. Chen, B. Kailkhura, R.A. Goldhahn, Y. Zhou, Certifiably-robust federated adversarial learning via randomized smoothing, [arXiv:2103.16031](http://www.arxiv.org/abs/2103.16031); 2021.

*   [[10]](#Chp004_75-90_B9780443190377000120.xhtml#cs0015_1) T. Chen, X. Jin, Y. Sun, W. Yin, VAFL: A method of vertical asynchronous federated learning, *FL-ICML*. 2020.

*   [[11]](#Chp004_75-90_B9780443190377000120.xhtml#cs0080_1) A.E. Cinà, K. Grosse, A. Demontis, B. Biggio, F. Roli, M. Pelillo, Machine learning security against data poisoning: are we there yet? [arXiv:2204.05986](http://www.arxiv.org/abs/2204.05986); 2022.

*   [[12]](#Chp004_75-90_B9780443190377000120.xhtml#cs0055_12) J. Cohen, E. Rosenfeld, Z. Kolter, Certified adversarial robustness via randomized smoothing, K. Chaudhuri, R. Salakhutdinov, eds. *Proceedings of the 36th International Conference on Machine Learning*. *Proceedings of Machine Learning Research*. 2019;vol. 97:1310–1320.

*   [[13]](#Chp004_75-90_B9780443190377000120.xhtml#cs0055_13) I. Diakonikolas, G. Kamath, D. Kane, J. Li, J. Steinhardt, A. Stewart Sever, A robust meta-algorithm for stochastic optimization, *International Conference on Machine Learning*. PMLR; 2019:1596–1606.

*   [[14]](#Chp004_75-90_B9780443190377000120.xhtml#cf0215) C. Dwork, F. McSherry, K. Nissim, A. Smith, Calibrating noise to sensitivity in private data analysis, *Theory of Cryptography Conference*. Springer; 2006:265–284.

*   [[15]](#Chp004_75-90_B9780443190377000120.xhtml#cs0055_15) M. Fang, X. Cao, J. Jia, N. Gong, Local model poisoning attacks to Byzantine-robust federated learning, *29th USENIX Security Symposium (USENIX Security 20)*. 2020:1605–1622.

*   [[16]](#Chp004_75-90_B9780443190377000120.xhtml#cs0075_1) Y. Gao, C. Xu, D. Wang, S. Chen, D.C. Ranasinghe, S. Nepal, STRIP: A defence against trojan attacks on deep neural networks, *Proceedings of the 35th Annual Computer Security Applications Conference*. 2019:113–125.

*   [[17]](#Chp004_75-90_B9780443190377000120.xhtml#cf0250) S. Goldwasser, M.P. Kim, V. Vaikuntanathan, O. Zamir, Planting undetectable backdoors in machine learning models, [arXiv:2204.06974](http://www.arxiv.org/abs/2204.06974); 2022.

*   [[18]](#Chp004_75-90_B9780443190377000120.xhtml#cs0050_1) I. Goodfellow, J. Shlens, C. Szegedy, Explaining and harnessing adversarial examples, *International Conference on Learning Representations*. 2015.

*   [[19]](#Chp004_75-90_B9780443190377000120.xhtml#cs0055_19) P. Kairouz, H.B. McMahan, B. Avent, A. Bellet, M. Bennis, A.N. Bhagoji, K. Bonawitz, Z. Charles, G. Cormode, R. Cummings, et al., Advances and open problems in federated learning, *Foundations and Trends in Machine Learning* 2021;14(1–2):1–210.

*   [[20]](#Chp004_75-90_B9780443190377000120.xhtml#cf0050) P.W. Koh, J. Steinhardt, P. Liang, Stronger data poisoning attacks break data sanitization defenses, *Machine Learning* 2022;111(1):1–47.

*   [[21]](#Chp004_75-90_B9780443190377000120.xhtml#cs0075_2) S. Kolouri, A. Saha, H. Pirsiavash, H. Hoffmann, Universal litmus patterns: revealing backdoor attacks in CNNs, *Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition*. 2020:301–310.

*   [[22]](#Chp004_75-90_B9780443190377000120.xhtml#cs0050_2) A. Kurakin, I. Goodfellow, S. Bengio, Adversarial examples in the physical world, in: ICLR Workshop, 2017.

*   [[23]](#Chp004_75-90_B9780443190377000120.xhtml#cs0040_2) B. Li, Y. Wang, A. Singh, Y. Vorobeychik, Data poisoning attacks on factorization-based collaborative filtering, *Proceedings of the 30th International Conference on Neural Information Processing Systems*. 2016:1893–1901.

*   [[24]](#Chp004_75-90_B9780443190377000120.xhtml#cs0015_2) Y. Liu, Y. Kang, X. Zhang, L. Li, Y. Cheng, T. Chen, M. Hong, Q. Yang, A communication efficient collaborative learning framework for distributed features, *FL-NeurIPS*. 2019.

*   [[25]](#Chp004_75-90_B9780443190377000120.xhtml#cs0075_3) Y. Liu, W.-C. Lee, G. Tao, S. Ma, Y. Aafer, X. Zhang, Abs: Scanning neural networks for back-doors by artificial brain stimulation, *Proceedings of the 2019 ACM SIGSAC Conference on Computer and Communications Security*. 2019:1265–1282.

*   [[26]](#Chp004_75-90_B9780443190377000120.xhtml#cs0055_26) Y. Liu, Z. Yi, T. Chen, Backdoor attacks and defenses in feature-partitioned collaborative learning, *FL-ICML*. 2020.
