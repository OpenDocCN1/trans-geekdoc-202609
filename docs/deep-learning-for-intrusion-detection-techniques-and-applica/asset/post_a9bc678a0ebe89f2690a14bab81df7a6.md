
## 8.4 One-Class Classification Anomaly Detection

One-class classification (OCC) is an unsupervised learning algorithm that attempts to model normal examples in order to classify new examples as either normal or an outlier. OCC methods have gained prominence for their ability to learn from this imbalanced data by effectively modeling the normal class and identifying deviations as anomalies. The OCC method focuses exclusively on learning the characteristics of the available class [17], referred to as the normal class. The goal of OCC is to identify whether new, unseen instances belong to this learned class or deviate significantly from it, thus being considered anomalies or outliers.

OCC methods are designed to work with highly imbalanced datasets, making them essential for domains where the occurrence of anomalous events is rare but critical to identify. OCC techniques may be categorized into four main approaches as follows:

- Reconstruction-based methods—which identify anomalies through reconstruction errors.
- Variational autoencoders (VAEs)—model data distributions probabilistically
- Convolutional approaches—suitable for image and multimodal data
- Hybrid models—combine various techniques to enhance robustness and performance.

OCC methods are leveraged for AD in applications where obtaining labeled examples of abnormal behavior is difficult, costly, or even impossible. The applications of OCC for AD are listed below:

- Detection of rare diseases in healthcare
- Financial fraud prevention
- Industrial fault detection
- Cybersecurity/network security, and
- Medical diagnostics

Spiking one-class anomaly detection framework for AD in cybersecurity and industrial control systems uses evolving spiking neural networks to detect advanced persistent threats (APTs) by learning from normal operational data and identifying deviations. The same framework may also be used for health monitoring of machinery to prevent damage or downtime and detect faults [18].

In healthcare, OCC is used for patient monitoring and early detection of diseases. For example, AD can be applied to electrocardiogram (ECG) data to identify abnormal heartbeats that may indicate cardiac issues.

- If the reconstructed data significantly deviates from the input (high reconstruction error), it is considered an anomaly.
- They are well-suited for structured data like tabular datasets, time series, and simple image data where the normal patterns are well-represented and deviations are easy to capture.

## 8.5 Deep Reinforcement Learning Anomaly Detection

Deep reinforcement learning combines the decision-making ability of RL with DL. DRL techniques such as DQN, double DQL, deep autoencoder Q-learning, policy gradient, actor-critic models, deep deterministic policy gradient (DDPG), TD3 DPG (Twin delayed deep DPG), meta-policy active AD, RL with CNN, and RNN are leveraged for smart and reliable AD specifically for video surveillance AD, network ID, finance AD, medical AD, textual AD, fraud detection, industrial damage detection, and manufacturing AD systems. Literature review reveals that there are a very few applications that leveraged the DRL [19].

The deep Q-learning network method is suitable only for discrete action space and moreover, it overestimates action values in some circumstances. In order to address this overestimation issue of DQN, the double DQN method was developed [20]. Double deep Q-learning performs action assessment before the Q-value update phase. The actor-critic DRL techniques optimizes DNN integrators via concurrent gradient descent and the actor-learners stabilize learning.

The literature review illustrates seventeen distinct DRL models that are leveraged in thirteen different applications such as general AD, ID, network AD, NID, video AD, cloud ID, wireless network security, building AD, industrial network control, temporal AD, adversarial attack detection cyberattack AD, and the internet of things (IoT) AD [21]. The performance of the DRL models is analyzed with fifty different datasets applied in experiments on AD. In smart video surveillance, anomalous activity detection is a vital component as it recognizes abnormal activity when observing a continuously changing scene [22].

Recent research works investigated the application of RCNN with DRL for real-time smart video AD and classification. DRL is well suited for video surveillance AD as the high dimensional video dataset contains raw and unlabeled anomalies, which are hard to handle using conventional and classical ML AD models [23].

Generally AD can be implemented with deep reinforcement neural networks (DRNNs) with partially labeled anomalies and meta-policy active AD. Application of deep deterministic policy gradient DRL methods can be leveraged for building AD, cloud ID, and cyberattack detection. Cyberattack detection can be performed using DDPG, DQN. For NID, DQL network, DDQN, AE-DQN, DAEQ-N,

The goal of transfer learning is to recognize a point anomaly from the collective anomaly task. Related areas of inductive transfer learning are multitask learning and sequential learning, depending on whether tasks are learned simultaneously or sequentially.

## 8.8 Conclusion

Advanced AI-based AD methods have demonstrated a remarkable ability to model data instances from various application domains and effectively perform AD, making them indispensable in numerous applications such as health, finance, manufacturing, cyber security, network ID, industries, etc. This chapter provides brief information on advanced AI-based AD methods such as AEs, GANs, OCC, RNNs, and DRL. Applications, advantages, and implementation are also discussed. This chapter’s content will be a valuable resource for the research and student community to know the recent trends in AD using AI-based ML, DL, and DRL methods.

## References

- 1. Goswami, M.J. (2024). AI-based anomaly detection for real-time cybersecurity. International Journal of Research and Review Techniques 3 (1): 45–53.
- 2. Rousopoulou, V., Vafeiadis, T., Nizamis, A. et al. (2022). Cognitive analytics platform with AI solutions for anomaly detection. Computers in Industry 134: 103555.
- 3. Wang, X., Wang, H., Bhandari, B., and Cheng, L. (2024). AI-empowered methods for smart energy consumption: a review of load forecasting, anomaly detection and demand response. International Journal of Precision Engineering and Manufacturing-Green Technology 11 (3): 963–993.
- 4. Masoodi, F.S., Quasim, M., Bukhari, S. et al. (ed.) (2023). Applications of Machine Learning and Deep Learning on Biological Data. CRC Press.
- 5. Sipple, J. and Youssef, A. (2022). A general-purpose method for applying explainable AI for anomaly detection. In International Symposium on Methodologies for Intelligent System, October 3–5, 2022, Cosenza, Italy, pp. 162–174. Cham: Springer International Publishing.
- 6. Abrar, I., Ayub, Z., Masoodi, F.S., and Bamhdi, A.M. (2020). A machine learning approach for intrusion detection system on NSL-KDD dataset. 2020 International Conference on Smart Electronics and Communication (ICOSEC), September 10-12, 2020, IEEE.
- 7. Santry, D.J. (2024). Demystifying Deep Learning: An Introduction to the Mathematics of Neural Networks. Hoboken, NJ: Wiley.
- 8. Ahanger, A.S., Khan, S.M., Masoodi, F. et al. (2025). Advanced intrusion detection in internet of things using graph attention networks. *Scientific Reports* 15: 983.
- 9. Wang, R., Nie, K., Wang, T. et al. (2020). Deep learning for anomaly detection. In *Proceedings of the 13th International Conference on Web Search and Data Mining*, February 3-7, 2020, Houston, TX USA, pp. 894–896.
- 10. Vinayakumar, R., Alazab, M., (Senior Member, IEEE) et al. Deep learning approach for intelligent intrusion detection system. *IEEE Access* 7: https://doi.org/10.1109/ACCESS.2019.2895334.
- 11. Liao, H.J., Lin, C.-H.R., and Ying-Chih, T.K.-Y. (2013). Intrusion detection system: a comprehensive review. *Journal of Network and Computer Applications* 36: 16–24. https://doi.org/10.1016/j.jnca.2012.09.004.
- 12. Khraisat, A., Gondal, I., Vamplew, P., and Kamruzzaman, J. (2019). Survey of intrusion detection systems: techniques, datasets and challenges. *Cybersecurity* 2: 20. https://doi.org/10.1186/s42400-019-0038-7.
- 13. Masoodi, F.S., Abrar, I., and Bamhdi, A.M. (2022). An effective intrusion detection system using homogeneous ensemble techniques. *International Journal of Information Security and Privacy (IJISP)* 16 (1): 18.
- 14. Ahanger, A.S., Khan, S.M., and Masoodi, F.S. (2021). An effective intrusion detection system using supervised machine learning techniques. *2021 5th International Conference on Computing Methodologies and Communication (ICCMC)*, April 8-10, 2021, Erode, India, IEEE.
- 15. El-Maged, L.M.A., Darwish, A., and Hassanien, A.E. (2020). Artificial intelligence-based plant’s diseases classification. In: *Proceedings of the International Conference on Artificial Intelligence and Computer Vision (AICV2020)* (ed. A.-E. Hassanien, A.T. Azar, T. Gaber, and D.O.F.M. Tolba), 3–15. Switzerland AG: Springer Nature.
- 16. Jan, S., Masoodi, F. S., and Bamhdi, A. (2022). Effective intrusion detection in IoT environment: deep learning approach. *SCRS Conference Proceedings on Intelligent Systems, April 26, 2022, India.*
- 17. Arshad, S., Ashraf, W., Ashraf, S. et al. (2023). Comparative study of machine learning techniques for intrusion detection on CICIDS-2017 dataset. *2023 10th International Conference on Computing for Sustainable Global Development (INDIACom)*, March 15-17, 2023, New Delhi, India. IEEE.
- 18. Salloum, S.A., Alshurideh, M., Elnagar, A., and Shaalan, K. (2020). Machine learning and deep learning techniques for cybersecurity: a review. In: *Proceedings of the International Conference on Artificial Intelligence and Computer Vision (AICV2020)*. (ed. A.-E. Hassanien, A.T. Azar, T. Gaber, and D.O.F.M. Tolba), 50–57. Switzerland AG: Springer Nature.
- 19. Bamhdi, A.M., Abrar, I., and Masoodi, F. (2021). An ensemble based approach for effective intrusion detection using majority voting. *Telkomnika (Telecommunication Computing Electronics and Control)* 19 (2): 664–671.
