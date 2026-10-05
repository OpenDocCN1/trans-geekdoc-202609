
# Cyber Security for Next-Generation Computing Technologies

NSL-KDD, and NOT-IoT can be used for SVM in detecting attacks like man-in-the-middle attacks, DoS, DDoS, tampering etc. etc. [72].

## 8.6 DEEP-LEARNING-BASED SIGNATURE-IDS SOLUTIONS FOR IOT

We apply deep learning (DL) techniques while dealing with larger datasets rather than machine-learning solutions. These methodologies are widely applied in IDSs. Deep learning is the domain of ML consisting of neural networks that help in identifying high-level features of data through layers of modification [73]. In an intrusion detection system, the hidden layers of the neural network help in identifying the best features for pattern selection. It contains an input, hidden layer(s) and an output layer. Specific weights are associated with every input of the network, which are adjusted to get the best output via the backpropagation method [74]. Deep learning techniques are classified into three main streams: supervised learning, unsupervised learning techniques, and hybrid methods [75].

Some of the famous techniques like deep neural networks (DNN), convolutional neural networks (CNN), etc. are included in supervised learning methods. These methods provide high accuracy. Deep neural networks (DNN) contain numerous hidden layers that aid in feature extraction. Tang et al. [76] designed a simple DNN that performed flow-based detection. Convolutional neural network (CNN) performs pooling, full connection with the dataset input. CNN involves less preprocessing. Kolosnici et al. [77] designed a model to detect malware by using CNN with recursive network layers. Recurrent neural network (RNN) is comprised of a memory function that stores previous data. It efficiently deals with time series information. Yin et al. [78] evaluated RNN with binary classification and multiclass classification.

Unsupervised learning techniques include generative adversarial networks (GANs), autoencoder (AE), deep belief networks (DBN), etc. These methods are low in performance as insufficient knowledge is available from labeled data. The best performance acquired on the KDCup dataset. The generative adversarial network (GAN) is a type of unsupervised learning that helps to process, scrutinize, and capture data. It consists of a generator and discriminator, which helps in identifying real features from fake ones. Erpek et al. [80] designed a jamming attacks detection model-based on a generative adversarial network consisting of transmitter, receiver, jammer. Autoencoder is a data compression algorithm used for reducing dimensions and detecting outliers. It uses feature space for compressing the input, Zhang et al. [81] proposed an IDS by using dilated convolutional AE (DCAEEs) to extract useful features from original data traffic of network.

Hybrid methods result in high performance and a smaller number of training samples, but computing time is high because of the complex structure. Li et al. [82] used a hybrid deep learning technique that implemented autoencoder and deep neural network for anomaly detection. AE was used to reduce the dimensions of data.

![](img/6cda7de083ea84ec227ad15ed4045807_165_0.png)

**Figure 8.5** Threat detection using signature-based IDS.

## 8.7 SIGNATURE-BASED INTRUSION DETECTION SYSTEM ARCHITECTURE

Researchers have used various kinds of IDS depending on the framework of the network as well per requirements. Sourour et al. [83] suggested a two-layered IDS to address the security concerns related to address translation (NAT). Layer 1 monitors the network entities, and layer 2 is deployed using three modules—alert consolidation, alert classification, and alert correlation—to lower the number of alerts and to pin down false alarms. Zhang et al. [84] introduced a dispersive kind of IDS for the smart grid using multilayered architecture using SVM for classification of attack and clonal selection (CSC) for attack detection. A deep learning (MDL) model was also suggested to deploy in IDS as it has a multi-architectural topology inspired by human brain, but this concept is still newborn [85]. The application layer is vulnerable to various kinds of attacks, so for cloud security, a signature-based IDS is an efficient approach, thus securing the application layer with rest of the layers [86, 87]. The common organization and threat detection phenomenon of signature-based IDS is shown in Figure 8.5.

## 8.8 LIMITATIONS IN SIGNATURE-BASED IDS

The signature-based technique for IDS is a widely used approach because it usually has low alarm rate and very efficient results. But this technique has limitations that need to be addressed with proper solutions. Signature-based IDS can only identify threats that are saved; thus it fails to detect anything absent from database [88, 90], and zero-day exploit remains unattended [89]. Each packet in signature-based approach needs to match, in the case that large-scale network traffic anomalies occur, the following scenario leads to packet drop, leaving the system open to chance of missing potential threats [92]. Thus these limitations are termed design or implementation flaws [93].

## 8.9 DISCUSSION AND FUTURE DIRECTIONS

Advances in technology and the Internet of Things have caused great vulnerability to security of data [94, 95]. Signature-based IDSs are among the widely installed IDSs in the commercial sector due to their pattern-based detection capability. These systems are improving every day to meet the complexity of new variant. A detailed survey of signature-based IDS, along with various implementation techniques, was discussed in this chapter. Future work can be performed by implementing-IDS with specific techniques that make threat prone. Software as SNORT, WINPCAP, etc. can be focused on real-time detection and efficiency [96]. Markov DL also helps in packet filtering in IDS as there is huge scope for this, and enormous work can be done in this field.

## 8.10 CONCLUSION

Security has no longer a choice in IT infrastructure; it is an utter commotion. The mushroom growth of IoT devices has posed the challenge of security in the IoT environment. Signature-based IDS is an excellent approach to counter security threats. Many solutions using signature-based detection techniques have been suggested by different researchers using different methodologies. The pattern matching approach has the identification of this type of detection, but it has some limitations leading to false negative conditions and potential danger. The machine learning and deep learning algorithm counters the limitation of signature-based detection by means of training over various datasets, decreasing the false detection rate and improving accuracy. This work offers a detailed survey of a variety of signature-based IDSs and the techniques deployed with them.

## REFERENCES

- [1] Algahtani B, Alnajrani B (2020) A study of Internet Protocols and communication. In: Proceedings of the 2nd International Conference on Computer and Information Sciences (ICCIS), pp. 1–6, doi:10.1109/ICCIS49240.2020.927652.
- [2] Soumayatha R, Hegde SG (2016) Study of IoT: Understanding IoT architecture, applications, and challenges. In: 1st International Conference on Innovations in Computing & Network (ICCKIN), CSE, International Journal of Networking & Applications, vol. 478.
- [3] Abdawal N, Sajun A, Kaddoura Y, Zulkerman IA, Aloul F (2022) Generative deep learning to detect cyberattacks for the IoT dataset. IEEE Access 10: 6430–6441, doi:10.1109/ACCESS.2023.3140015.
- [4] Mann P, Tyagi N, Gautam S, Rana A (2020) Classification of various types of attacks in IoT environment. In: 2020 12th International Conference on Computational Intelligence and Communication Networks (CICN), IEEE, Bhimtal, India.
- [5] Cisco Annual Internet Report–Cisco Annual Internet Report (2018–2023). White Paper. Accessed: May 31, 2021 [Online]. Available: https://www.cisco.com/en/us/solutions/executive-perspectives/annual-internet-report-white-paper-c1-71490.html.
- [6] Ashraf J, Bakshi AD, Moustafa N, Khurshid H, Javed A, Beheshti A (2021) Novel deep learning-enabled LSTM autoencoder for discovering anomalous events from intelligent transportation systems. IEEE Transactions on Intelligent Transportation, 22(7): 4507.
- [7] Archana MB, Harshitha BN, Prakaj M (2017) A technique to safeguard cluster-based wireless sensor networks against Sybil attack. International Journal of Recent Trends in Engineering and Research, 3(4):370–373, doi:10.23883/ijiter.2017.js.
- [8] Wang W, He S, Sun L, Zhang Q (2019) Cross technology for heterogeneous IoT devices through shifters. IEEE Transactions on Wireless Communications, 18(2): 796–806, doi:10.1109/twc.2018.288344.
- [9] Kumar V (2012) Signature based intrusion detection system using SNORT. International Journal of Computer Applications & Information Technology, I(7).
- [10] Bhuyan MH, Bhattacharjya DK, Kalita JK (2014) Network anomaly detection: Methods, systems and tools. IEEE Surveys & Tutorials, 16(1): 303–336.
- [11] Tang Y, Chen J (2007) An automated signature-based approach across polymorphic intent worms. IEEE Transactions on Parallel and Distributed Systems, 18(7): 879–892, doi:10.1109/TPDS.2007.1050.
- [12] Snehi J, Bhandari A, Gautam V, Beni M (2020) Diverse methods for signature-based intrusion detection schemes adopted. International Journal of Recent Technology and Engineering, 9(2): 44–49.
- [13] Hidoussi F, Toral-Cruz H, Boubiche E, Lakhtaria K, Mihova A, Voznak M (2015) Centralized IDS based on misuse detection for cluster-based wireless sensor networks. Wireless Personal Communication, 85(1): 207–224.
- [14] Patel SK, Sonker A (2016) Rule-based network intrusion detection system for port scanning with efficient port detection using snort. International Journal of Future Generation Communication and Networking, 9(6): 339–350.
- [15] Mehare TM, Bhosale S (2017) Design and development of intrusion detection system for internet of things. The International Journal of Innovative Research in Communication and Engineering, 5(7): 13469–13475.
