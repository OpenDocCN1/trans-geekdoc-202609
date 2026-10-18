
## 12.6.1 Results

We explored in this approach different security aspects with respect to data regulation policies while at the same time enhancing the efficiency of AI models. Using federated learning, we are able to create a model for training while attending to privacy concerns for personal data, and with blockchain, we provided contributors with full anonymity, control, and access in providing the data that they want the model to assess, while having full transparency of the training process. Those features lead to the growth of the training data set by an average of 500 additional data points per day. Also, with the usage of the incentive mechanism, we are able to avoid malicious contribution since the data is verified by the contributors before the training phase. Since we are using a deposit/refund mechanism, each input requires monetary deposit. After a period of time, we saw that the account balance of malicious users went all the way to zero because all data was verified and deleted when it led to no refund to the contributor. Simultaneously the account balance of good contributors went up, since they were rewarded for their verification. This mechanism helps avoid the poisoning problem described previously. As for availability, the decentralized infrastructure of the blockchain helps in reaching countless users, who can provide their data in a secure and private environment.

Despite all those security features, the accuracy and the efficiency of the model increased by 5%. This is due to the fact that we don’t consider adding noise to the data to enhance privacy, such as we do in differential privacy. Thus the model is being trained with quality data received from contributors

## 12.7 CONCLUSION

In this chapter, we have shown that, despite new data regulation and policies, we are still able to provide quality and secure model training for the AI model, while complying with regulatory rules. And this is possible due to federated learning and blockchain technology. As we saw in our use case, where we merged federated learning and blockchain, multiple data security attributes were addressed while enhancing an AI model. This combination offers a specific approach to contribute to the CIA triad; i.e., by using federated learning, we manage to provide privacy and confidentiality to the data during training. At the same time, the blockchain offers traceability, integrity, and transparency. Those attributes also answer to the GDPR principles and CCPA regulations.

## REFERENCES

- 1. [Filip e Betzel](#), Karen Khatamifard, Harini Suresh, David J. Lilja, John Sartori, and Ulya Karpuzcu. Approximate Communication: Techniques for Reducing Communication Bottlenecks in Large-Scale Parallel Systems. *ACM Computing Surveys*, 51(1):1–32, April 2018.
- 2. [Minghong Fang](#), Xiaoyu Cao, Jinyuan Jia, and Neil Zhenqiang Gong. Local Model Poisoning Attacks to Byzantine-Robust Federated Learning. page 19.
- 3. [Michelle Goddard](#). The EU General Data Protection Regulation (GDPR): European Regulation that has a Global Impact. *International Journal of Market Research*, 59(6):703–705, November 2017.
- 4. [Lydia de la Torre](#). A Guide to the California Consumer Privacy Act of 2018. *SSRN Electronic Journal*, 2018.
- 5. [Dorothy Elizabeth Robling Denning](#). *Cryptography and Data Security*. Addison-Wesley, Reading, Mass, 1982.
- 6. [Oliver Radley-Gardner](#), Hugh Beale, and Reinhard Zimmermann, editors. *Fundamental Texts On European Private Law*. Hart Publishing, 2016.
- 7. [Xin Yao](#), Tianchi Huang, Chenglei Wu, Ruixiao Zhang, and Lifeng Sun. Towards Faster and Better Federated Learning: A Feature Fusion Approach. In *2019 IEEE International Conference on Image Processing (ICIP)*, pages 175–179, Taipei, Taiwan, September 2019. IEEE.
- 8. [Qiang Yang](#), Yang Liu, Tianjian Chen, and Yongxin Tong. Federated Machine Learning: Concept and Applications. *arXiv:1902.04885 [cs]*, February 2019. arXiv: 1902.04885.
- 9. [Kelvin](#). Introduction to Federated Learning and Challenges, November 2020.
- 10. Huawei Huang and Yang Yang. WorkerFirst: Worker-Centric Model Selection for Federated Learning in Mobile Edge Computing. In 2020 IEEE/CIC International Conference on Communications in China (ICCC), pages 1039–1044, August 2020. ISSN: 2377–8644.
- 11. Jiankai Sun, Xin Yang, Yuanshun Yao, Aonan Zhang, Weihao Gao, Junyuan Xie, and Chong Wang. Vertical Federated Learning without Revealing Intersection Membership. arXiv:2106.05508 [cs], June 2021. arXiv: 2106.05508.
- 12. Peter Kairouz, H. Brendan McMahan, Brendan Avent, Aurélien Bellet, Mehdi Bennis, Arjun Nitin Bhagoji, Kallista Bonawitz, Zachary Charles, Graham Cormode, Rachel Cummings, Rafael G. L. D’Oliveira, Hubert Eichner, Salim El Rouayheb, David Evans, Josh Gardner, Zachary Garrett, Adrià Gascón, Badih Ghazi, Phillip B. Gibbons, Marco Gruteser, Zaid Harchaoui, Chaoyang He, Lie He, Zhouyuan Huo, Ben Hutchinson, Justin Hsu, Martin Jaggi, Tara Javidi, Gauri Joshi, Mikhail Khodak, Jakub Konečný, Aleksandra Korolova, Farinaz Koushanfar, Sanmi Koyejo, Tancrède Lepoint, Yang Liu, Prateek Mittal, Mehryar Mohri, Richard Nock, Ayfer Özgür, Rasmus Pagh, Mariana Raykova, Hang Qi, Daniel Ramage, Ramesh Raskar, Dawn Song, Weikang Song, Sebastian U. Stich, Ziteng Sun, Ananda Theertha Suresh, Florian Tramèr, Praneeth Vepakomma, Jianyu Wang, Li Xiong, Zheng Xu, Qiang Yang, Felix X. Yu, Han Yu, and Sen Zhao. Advances and Open Problems in Federated Learning. arXiv:1912.04977 [cs, stat], March 2021. arXiv: 1912.04977.
- 13. Lifei Wei, Haojin Zhu, Zhenfu Cao, Xiaolei Dong, Weiwei Jia, Yunlu Chen, and Athanasios V. Vasilakos. Security and Privacy for Storage and Computation in Cloud Computing. Information Sciences, 258:371–386, February 2014.
- 14. Cynthia Dwork. Differential Privacy: A Survey of Results. In Manindra Agrawal, Dingzhu Du, Zhenhua Duan, and Angsheng Li, editors, Theory and Applications of Models of Computation, pages 1–19, Berlin, Heidelberg, 2008. Springer Berlin Heidelberg.
- 15. Hyesung Kim, Jihong Park, Mehdi Bennis, and Seong-Lyun Kim. Blockchained On-Device Federated Learning. IEEE Communications Letters, 24(6):1279–1283, June 2020.
- 16. [Quoc Khanh Nguyen](#) and Quang Vang Dang. Blockchain Technology for the Advancement of the Future. In *2018 4th International Conference on Green Technology and Sustainable Development (GTSD)*, pages 483–486, Ho Chi Minh City, November 2018. IEEE.
- 17. [Konstantinos Christidis](#) and Michael Devetsikiotis. Blockchains and Smart Contracts for the Internet of Things. *Ieee Access*, 4:2292–2303, 2016.
- 18. [Bin Hu](#). A Comprehensive Survey on Smart Contract Construction and Execution: Paradigms, Tools, and Systems. *OPEN ACCESS*, page 51.

## Part III

## Using AI/ML Algorithms for Cyber Security

## Using Machine Learning for Cyber Security:
Overview

D. Roshni Thanka, G. Jaspher W. Kathrine, and E. Bijolin Edwin
*Karunya Institute of Technology and Sciences, Coimbatore, Tamil Nadu, India*

DOI: 10.1201/9781003187158-16

## Contents

- §3.1 Introduction
- §3.2 Is Artificial Intelligence Enough to Stop Cyber Crime?
- §3.3 Corporations’ Use of Machine Learning to Strengthen Their Cyber Security Systems
- §3.4 Cyber Attack/Cyber Security Threats and Attacks
  - 3.4.1 Malware
  - 3.4.2 Data Breach
  - 3.4.3 Structured Query Language Injection (SQL-i)
  - 3.4.4 Cross-site Scripting (XSS)
  - 3.4.5 Denial-of-service (DOS) Attack
  - 3.4.6 Insider Threats
  - 3.4.7 Birthday Attack
  - 3.4.8 Network Intrusions
  - 3.4.9 Impersonation Attacks
  - 3.4.10 DDoS Attacks Detection on Online Systems
- §3.5 Different Machine Learning Techniques in Cyber Security
  - 3.5.1 Support Vector Machine (SVM)
  - 3.5.2 K-nearest Neighbor (KNN)
  - 3.5.3 Naïve Bayes
  - 3.5.4 Decision Tree

the real world, where an attack is pertinent at each corner of the network, is the main focal point. Cyber security has a significant role in this context of maintaining security. Brute-force attack, credential stuffing, phishing, malware attacks, botnets denial-of-service, instant messaging abuse, worms, Trojans, intellectual property theft, rootkit, password sniffing, etc. are just some of the attacks commonly faced by any organization or by users of the internet. To detect and prevent these kinds of attacks, to assist analysts in dealing with them, and to prevent the abuse of data in the modern era, artificial intelligence categories like machine learning and deep learning play a vital role. With the use of machine learning techniques, patterns are developed and applied to algorithms to preemptively prevent various unforeseen attacks and bolster the security system. To generate these patterns, relevant, potentially rich-quality data is essential. Models developed using machine learning techniques automate computers and assist analysts in preserving valuable data without the explicit presence of the analysts. In any kind of attack, the very first thing is to know about the goal of the attack [2], which may be under any of the categories shown in Figure 13.1. A second important dimension is to deflate an adversary’s ability to execute malicious activities.
