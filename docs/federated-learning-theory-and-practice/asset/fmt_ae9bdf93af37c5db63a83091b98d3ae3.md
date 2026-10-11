
*   [\[69\]](#Chp014_257-279_B9780443190377000235.xhtml#cf1040) Sambhav Solanki, Samhita Kanaparthy, Sankarshan Damle, Sujit Gujar, Differentially private federated combinatorial bandits with constraints, [arXiv:2206.13192](http://www.arxiv.org/abs/2206.13192); 2022.
*   \[70\] Niranjan Srinivas, Andreas Krause, Sham M. Kakade, Matthias Seeger, Gaussian process optimization in the bandit setting: no regret and experimental design, *Proc. ICML*. 2010:1015–1022.
*   \[71\] Richard S. Sutton, Andrew G. Barto, *Reinforcement Learning: An Introduction*. MIT Press; 2018.
*   [\[72\]](#Chp014_257-279_B9780443190377000235.xhtml#cs0095_7) Arun Verma, Zhongxiang Dai, Bryan Kian Hsiang Low, Bayesian optimization under stochastic delayed feedback, *Proc. ICML*. PMLR; 2022:22145–22167.
*   \[73\] Yuanhao Wang, Jiachen Hu, Xiaoyu Chen, Liwei Wang, Distributed bandit learning: near-optimal regret with efficient communication, *Proc. ICLR*. 2020.
*   [\[74\]](#Chp014_257-279_B9780443190377000235.xhtml#cf0010) Ronald J. Williams, Simple statistical gradient-following algorithms for connectionist reinforcement learning, *Machine Learning* 1992;8(3–4):229–256.
*   [\[75\]](#Chp014_257-279_B9780443190377000235.xhtml#cs0055_4) Lin Xiao, Tong Zhang, A proximal stochastic gradient method with progressive variance reduction, *SIAM Journal on Optimization* 2014;24(4):2057–2075.
*   \[76\] Zhijie Xie, S.H. Song, FedKL: tackling data heterogeneity in federated reinforcement learning by penalizing KL divergence, [arXiv:2204.08125](http://www.arxiv.org/abs/2204.08125); 2022.
*   \[77\] Pan Xu, Felicia Gao, Quanquan Gu, An improved convergence analysis of stochastic variance-reduced policy gradient, *Uncertainty in Artificial Intelligence*. PMLR; 2020:541–551.
*   [\[78\]](#Chp014_257-279_B9780443190377000235.xhtml#cf0990) Zirui Yan, Quan Xiao, Tianyi Chen, Ali Tajer, Federated multi-armed bandit via uncoordinated exploration, *ICASSP 2022-2022 IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP)*. IEEE; 2022:5248–5252.
*   [\[79\]](#Chp014_257-279_B9780443190377000235.xhtml#cf0745) Qiang Yang, Yang Liu, Yong Cheng, Yan Kang, Tianjian Chen, Han Yu, Federated learning, *Synthesis Lectures on Artificial Intelligence and Machine Learning* 2019;13(3):1–207.
*   [\[80\]](#Chp014_257-279_B9780443190377000235.xhtml#cf0905) Yutong Ye, Wupan Zhao, Tongquan Wei, Shiyan Hu, Mingsong Chen, FedLight: federated reinforcement learning for autonomous multi-intersection traffic signal control, *2021 58th ACM/IEEE Design Automation Conference (DAC)*. IEEE; 2021:847–852.
*   [\[81\]](#Chp014_257-279_B9780443190377000235.xhtml#cf0290) Shipeng Yu, Faisal Farooq, Alexander Van Esbroeck, Glenn Fung, Vikram Anand, Balaji Krishnapuram, Predicting readmission risk with institution-specific prediction models, *Artificial Intelligence in Medicine* 2015;65(2):89–96.
*   [\[82\]](#Chp014_257-279_B9780443190377000235.xhtml#cf0910) Shuai Yu, Xu Chen, Zhi Zhou, Xiaowen Gong, Di Wu, When deep reinforcement learning meets federated learning: intelligent multi-timescale resource management for multi-access edge computing in 5G ultra dense network, *IEEE Internet of Things Journal* 2020.
*   [\[83\]](#Chp014_257-279_B9780443190377000235.xhtml#cs0100_3) Yehong Zhang, Zhongxiang Dai, Bryan Kian Hsiang Low, Bayesian optimization with binary auxiliary information, *Proc. UAI*. 2020:1222–1232.
*   [\[84\]](#Chp014_257-279_B9780443190377000235.xhtml#cs0100_4) Yehong Zhang, Trong Nghia Hoang, Bryan Kian Hsiang Low, Mohan Kankanhalli, Information-based multi-fidelity Bayesian optimization, *Proc. NeurIPS Workshop on Bayesian Optimization*. 2017.
*   [\[85\]](#Chp014_257-279_B9780443190377000235.xhtml#cf0980) Zhaowei Zhu, Jingxuan Zhu, Ji Liu, Yang Liu, Federated bandit: a gossiping approach, *Abstract Proceedings of the 2021 ACM SIGMETRICS/International Conference on Measurement and Modeling of Computer Systems*. 2021:3–4.
*   \[86\] Hankz Hankui Zhuo, Wenfeng Feng, Qian Xu, Qiang Yang, Yufeng Lin, Federated reinforcement learning, [arXiv:1901.08277](http://www.arxiv.org/abs/1901.08277); 2019.

---

# Chapter 15: Data valuation in federated learning

Zhaoxuan Wu^([a](#Chp015_281-296_B9780443190377000247.xhtml#aff0010)); Xinyi Xu^([a](#Chp015_281-296_B9780443190377000247.xhtml#aff0010)); Rachael Hwee Ling Sim^([a](#Chp015_281-296_B9780443190377000247.xhtml#aff0010)); Yao Shu^([a](#Chp015_281-296_B9780443190377000247.xhtml#aff0010)); Xiaoqiang Lin^([a](#Chp015_281-296_B9780443190377000247.xhtml#aff0010)); Lucas Agussurja^([a](#Chp015_281-296_B9780443190377000247.xhtml#aff0010)); Zhongxiang Dai^([a](#Chp015_281-296_B9780443190377000247.xhtml#aff0010)); See-Kiong Ng^([a](#Chp015_281-296_B9780443190377000247.xhtml#aff0010)); Chuan-Sheng Foo^([b](#Chp015_281-296_B9780443190377000247.xhtml#aff0015)); Patrick Jaillet^([c](#Chp015_281-296_B9780443190377000247.xhtml#aff0020)); Trong Nghia Hoang^([d](#Chp015_281-296_B9780443190377000247.xhtml#aff0025)); Bryan Kian Hsiang Low^([a](#Chp015_281-296_B9780443190377000247.xhtml#aff0010))

^a National University of Singapore, Singapore, Singapore

^b Agency for Science, Technology and Research, Singapore, Singapore

^c Massachusetts Institute of Technology, Cambridge, MA, United States

^d Washington State University, Pullman, WA, United States

## Abstract

Federated learning (FL) has become an increasingly popular solution paradigm for enabling collaborative machine learning (CML) in which multiple clients can collaboratively train a common model without sharing their private training data with others. However, broad adoption of FL in practice is still limited, as clients can often be reluctant to participate in such federated effort unless their contributions are accurately recognized and fairly compensated. Data valuation is thus extensively required to measure the relative contributions among clients. In this chapter, we review data valuation methods in the conventional supervised CML setting, followed by extensions to the FL paradigm. To better address the challenge that the private data from local clients cannot be made available to the server, we further discuss many specialized data valuation methods developed for both horizontal and vertical FL in detail. Overall, this chapter aims to provide a comprehensive suite of data valuation tools to empower FL practitioners in various practical scenarios.

### Keywords

Data valuation; Incentives; Fairness; Privacy; Contribution analysis; Feature attribution; Gradient attribution

## Acknowledgements

This research/project is supported by the National Research Foundation Singapore and DSO National Laboratories under the AI Singapore Programme (AISG Award No: AISG2-RP-2020-018).

## 15.1 Introduction

In recent years, there has been increasing interests in assessing the value of data in many real-world machine learning applications. Broadly speaking, in collaborative machine learning (CML), data valuation (DV) offers a trustworthy way of attributing rewards among participating clients and identifying potentially malicious ones in the learning effort. Federated learning (FL) is one of the most widely practiced CML frameworks, but its distinguishing data communication, fusion, and learning characteristics from the canonical machine learning framework necessitate tailored designs to effectively evaluate data contributed by various participating clients. For example, the server has no access to the raw data and the learning happens in an iterative round-wise manner. These characteristics pose challenges for developing effective and efficient methods.
