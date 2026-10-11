
# Chapter 5: Adversarial robustness in federated learning

Chulin Xie; Xiaoyang Wang  
University of Illinois at Urbana-Champaign, Urbana, IL, United States

## Abstract

While federated learning (FL) enables training a shared machine learning model over scattered and private data from diverse clients, its distributed nature increases the vulnerability as the clients may not be trustworthy. This chapter summarizes and provides a taxonomy of common attacks and defenses in federated learning. The attack section includes methods for corrupting the local models with data poisoning and model poisoning. The defenses are summarized accordingly, including robust statistic-based methods and smoothing-based methods, and we discuss their effectiveness against multiple attacks. In addition, we highlight how data heterogeneity and privacy concerns impose new challenges on securing FL systems.

### Keywords

Federated learning; Robustness; Attack; Defense

## 5.1 Introduction

Adversarial attacks that target the increasingly deployed machine learning models have raised many concerns. For example, in a broad class of anomaly detection tasks such as fraud detection, an adversarial may want to decrease the accuracy of the machine learning model or mislead the predictions on a given set of data samples. A federated learning system, where the server has no visibility of the client-side training procedure, is more vulnerable to adversarial attacks and imposes challenges in defending against such attacks.

## References

*   [[27]](#Chp004_75-90_B9780443190377000120.xhtml#cf0220) Y. Ma, X. Zhu, J. Hsu, Data poisoning against differentially-private learners: attacks and defenses, *Proceedings of the 28th International Joint Conference on Artificial Intelligence*. 2019:4732–4738.

*   [28] A. Madry, A. Makelov, L. Schmidt, D. Tsipras, A. Vladu, Towards deep learning models resistant to adversarial attacks, *6th International Conference on Learning Representations, ICLR*. 2018.

*   [[29]](#Chp004_75-90_B9780443190377000120.xhtml#cf0035) B. McMahan, E. Moore, D. Ramage, S. Hampson, B. Aguera y Arcas, Communication-efficient learning of deep networks from decentralized data, *Proceedings of the 20th AISTATS, PMLR*. 2017;vol. 54:1273–1282.

*   [30] E.M.E. Mhamdi, R. Guerraoui, S. Rouault, et al., The hidden vulnerability of distributed learning in Byzantium, *International Conference on Machine Learning*. PMLR; 2018:3521–3530.

*   [[31]](#Chp004_75-90_B9780443190377000120.xhtml#cs0020_2) L. Muñoz-González, B. Biggio, A. Demontis, A. Paudice, V. Wongrassamee, E.C. Lupu, F. Roli, Towards poisoning of deep learning algorithms with back-gradient optimization, *Proceedings of the 10th ACM Workshop on Artificial Intelligence and Security*. 2017:27–38.

*   [[32]](#Chp004_75-90_B9780443190377000120.xhtml#cf0240) M.S. Ozdayi, M. Kantarcioglu, Y.R. Gel, Defending against backdoors in federated learning with robust learning rate, *Proceedings of the AAAI Conference on Artificial Intelligence* 2021;35:9268–9276.

*   [[33]](#Chp004_75-90_B9780443190377000120.xhtml#cf0245) A. Panda, S. Mahloujifar, A.N. Bhagoji, S. Chakraborty, P. Mittal Sparsefed, Mitigating model poisoning attacks in federated learning with sparsification, *International Conference on Artificial Intelligence and Statistics*. PMLR; 2022:7587–7624.

*   [34] A. Raghunathan, J. Steinhardt, P. Liang, Certified defenses against adversarial examples, *6th International Conference on Learning Representations, ICLR*. 2018.

*   [[35]](#Chp004_75-90_B9780443190377000120.xhtml#cs0080_2) A. Schwarzschild, M. Goldblum, A. Gupta, J.P. Dickerson, T. Goldstein, Just how toxic is data poisoning? A unified benchmark for backdoor and data poisoning attacks, *International Conference on Machine Learning*. PMLR; 2021:9389–9398.

*   [[36]](#Chp004_75-90_B9780443190377000120.xhtml#cf0275) D. Shah, P. Dube, S. Chakraborty, A. Verma, Adversarial training in communication constrained federated learning, [arXiv:2103.01319](http://www.arxiv.org/abs/2103.01319); 2021.

*   [[37]](#Chp004_75-90_B9780443190377000120.xhtml#cf0310) V. Shejwalkar, A. Houmansadr, P. Kairouz, D. Ramage, Back to the drawing board: a critical evaluation of poisoning attacks on production federated learning, *2022 IEEE Symposium on Security and Privacy (SP)*. 2022:1354–1371.

*   [38] Z. Sun, P. Kairouz, A.T. Suresh, H.B. McMahan, Can you really backdoor federated learning? [arXiv:1911.07963](http://www.arxiv.org/abs/1911.07963); 2019.

*   [[39]](#Chp004_75-90_B9780443190377000120.xhtml#cs0050_3) C. Szegedy, W. Zaremba, I. Sutskever, J. Bruna, D. Erhan, I. Goodfellow, R. Fergus, Intriguing properties of neural networks, *International Conference on Learning Representations*. 2014.

*   [[40]](#Chp004_75-90_B9780443190377000120.xhtml#cs0075_4) B. Wang, Y. Yao, S. Shan, H. Li, B. Viswanath, H. Zheng, B.Y. Zhao, Neural cleanse: identifying and mitigating backdoor attacks in neural networks, *2019 IEEE Symposium on Security and Privacy (SP)*. IEEE; 2019:707–723.

*   [41] H. Wang, K. Sreenivasan, S. Rajput, H. Vishwakarma, S. Agarwal, J.-y. Sohn, K. Lee, D. Papailiopoulos, Attack of the tails: yes, you really can backdoor federated learning, H. Larochelle, M. Ranzato, R. Hadsell, M. Balcan, H. Lin, eds. *Advances in Neural Information Processing Systems*. Curran Associates, Inc.; 2020;vol. 33:16070–16084.

*   [42] C. Xie, K. Huang, P.-Y. Chen, B. Li, DBA: Distributed backdoor attacks against federated learning, *International Conference on Learning Representations*. 2020.

*   [[43]](#Chp004_75-90_B9780443190377000120.xhtml#cs0040_3) C. Xie, O. Koyejo, I. Gupta, Fall of empires: Breaking Byzantine-tolerant SGD by inner product manipulation, *Uncertainty in Artificial Intelligence*. PMLR; 2020:261–270.

*   [44] C. Xie, M. Chen, P.-Y. Chen, B. Li, CRFL: Certifiably robust federated learning against backdoor attacks, *International Conference on Machine Learning*. PMLR; 2021:11372–11382.

*   [[45]](#Chp004_75-90_B9780443190377000120.xhtml#cs0075_5) X. Xu, Q. Wang, H. Li, N. Borisov, C.A. Gunter, B. Li, Detecting AI trojans using meta neural analysis, *2021 IEEE Symposium on Security and Privacy (SP)*. IEEE; 2021:103–120.

*   [[46]](#Chp004_75-90_B9780443190377000120.xhtml#cs0010_2) Q. Yang, Y. Liu, T. Chen, Y. Tong, Federated machine learning: concept and applications, *ACM Transactions on Intelligent Systems and Technology (TIST)* 2019;10(2):1–19.

*   [47] D. Yin, Y. Chen, R. Kannan, P. Bartlett, Byzantine-robust distributed learning: towards optimal statistical rates, *International Conference on Machine Learning*. PMLR; 2018:5650–5659.

*   [[48]](#Chp004_75-90_B9780443190377000120.xhtml#cf0055) Z. Zhang, A. Panda, L. Song, Y. Yang, M. Mahoney, P. Mittal, R. Kannan, J. Gonzalez, Neurotoxin: Durable backdoors in federated learning, *International Conference on Machine Learning*. PMLR; 2022:26429–26446.

*   [49] G. Zizzo, A. Rawat, M. Sinn, B. Buesser, FAT: Federated adversarial training, [arXiv:2012.01791](http://www.arxiv.org/abs/2012.01791); 2020.
