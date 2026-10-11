
The data from IoT devices is stored in the cloud. As already mentioned, cloud information safety relies heavily on SaaS. Third companies typically backup data from IoT clouds. Backups pose a significant risk to data integrity ([B. Ondiege et al., 2017](#979-8-3693-9225-6.ch011.bits-pdf.xhtml#_idTextAnchor310)).

#### Table 4. Comparative analyses of IoT attacks based on recent research articles.

| Authors | IoT Attacks & Preventions | Method Used | Practical Implications | Limitations |
| --- | --- | --- | --- | --- |
| Abdul Hanan K. Mohammed et al., 2021 | Various IoT attacks include malware, DDoS, and man-in-middle attacks | Random Forest, Logistic Regression, SVM, KNN, MLP | • ML & DL approaches can be utilized to identify IoT Cyber-attacks.<br>• A comparative analysis of six detection techniques. | • Traditional strategy is inefficient at detecting cyber-attacks.<br>• Increasing security risks require increased innovation in defensive measures. |
| Nader Karmous et al., 2022 | • IoT attacks: DDoS, malware, ransomware, spoofing, eavesdropping, physical tampering<br>• Prevention methods: Network segmentation, encryption, strong authentication, regular software updates | Supervised machine learning Method and classification algorithms like RF, SVM, KNN | Employ supervised machine learning method for enhanced precision. | • The research lacks a full description of the interpretability of the machine learning models used, which is critical for understanding how the IDS makes choices and identifying potential biases or errors.<br>• The article does not thoroughly examine the scalability of the suggested framework, particularly in large-scale IoT setups with a significant volume of data and devices, which may impact real-world application. |
| Inayat U, Zia MF, 2022 | • Common IoT attacks include DoS, DDoS, probing, spoofing, and MITM.<br>• ML & DL are utilized to identify & prevent attacks. | Learning-based technologies (machine and deep learning) for detecting cyber-attacks in IoT networks | ML and DL approaches have been investigated with regard to the recognition of cyber assaults in IoT devices, offering a detailed review of their usefulness in defending IoT settings. | • IoT networks are vulnerable to cyber security assaults.<br>• Threats could cause physical and economic losses. |
| Anika Tasnim, Nigah Hossain, 2022 | • IoT threats include data breaches, network vulnerabilities, illegal access, and DDoS attacks.<br>• Implement strong encryption, perform frequent security updates, and segment your network. | • Various approaches, including DT, RF, AdaBoost, XGBoost, ANN, MLP<br>• Under-sampling, over-sampling, and SMOTE, were applied to the dataset. | • Using DT & RF, researchers improved the identification of IoT network attacks.<br>• Several ML & DL algorithms were investigated for improving IoT safety. | • Insufficient security features in IoT networks.<br>• The Adaboost technique and artificial neural networks perform badly in multiclass classification. |
| Celil Okur, Murat Dener, 2020 | • Botnet assaults against smart healthcare IoT devices.<br>• Machine learning algorithms are used to differentiate between regular and attack traffic as prevention proximity. | • Statistical measurements (Pearson coefficient, entropy)<br>• ML methods using data pre-processing techniques | • Enhanced security for IoT devices.<br>• Using machine learning algorithms to detect network attacks | • Time-consuming investigation using the tcpdump program.<br>• High processing throughput is required for high-speed networks. |
| Qifeng Chen, Haoming Chen, et al., 2018 | • DoS attacks simulated on IoT system using Kali Linux.<br>• A comparison of the efficiency of various DoS attack tactics is offered. | • Simulated IoT setup with Kali Linux attacker and Arduino victim.<br>• The research compares three main types of DoS attacks. | • IoT security problems, DoS attacks, and simulation-based efficiency comparisons. | • Security problems around IoT systems and attacks on IoT systems might cause significant damage. |

### 8 PREVENTIVE MEASURES USED FOR SAFE IOT

It is vital to deploy robust security measures to prevent unwanted access and data breaches. The following strategies provide comprehensive guidance on improving IoT safety and resilience against possible hazards.

#### 8.1 Strong Password

Using a common and basic password for IoT devices opens the door to potential hackers. The best defense against hackers is to use strong and secure passwords. Make sure you create a new password for each device ([Vutukuru & Lade, 2023](#979-8-3693-9225-6.ch011.bits-pdf.xhtml#_idTextAnchor319)). If a hacker guesses one of your passwords, it could harm all of your devices that utilize that password. Regularly upgrading these passwords reduces the possibility of illegal entry.

#### 8.2 Regular Improvement

If the version of a basic software tool is not modified for an extended period of time, it becomes an easy target. It just provides enough time for malicious people to examine the software for flaws (Kamel, Hegazi, 2018). So, it's a good idea to update on a regular basis and ensure that every connected device is up to date. It is preferable to automate the software update implementation across the infrastructure since it reduces the likelihood of a breach. Regularly updating the software on IoT devices helps to fix security vulnerabilities and enhance productivity.

#### 8.3 Encryption

Encryption is integral to improving cyber security for IoT (Internet of Things) devices. Encrypt all in-transit data, including sensor and device data, administration, provisioning, and deployments. Almost all modern IoT devices are capable of encrypting network traffic and protecting both information and control plane conversations. Some additional considerations are listed in the table below:

#### Table 5. Significance of encryption in cyber security

| Aspect | Significance |
| --- | --- |
| Data Confidentiality | Encryption ensures that data exchanged between IoT devices and servers is safe & can’t be understood by unauthorized parties (Lei Cui a b., Youyang Qu et al., 2020). Even if the data is intercepted, without the encryption key, it is nearly impossible to decipher. |
| Data Integrity | Encryption helps to protect data integrity by guaranteeing that it is not altered or messed over while being transmitted or stored. IoT devices can use cryptographic hash functions or digital signatures to ensure that the data they receive is genuine and unmodified (C. Ge, W. Susilo, 2022). |
| Authentication | Encryption makes it easier to authenticate IoT devices and users. Devices can use techniques like digital certificates and public-key cryptography to prove their identification to one another and the network, limiting illegal access (Pedro Ramos [Brandao, 2018](#979-8-3693-9225-6.ch011.bits-pdf.xhtml#_idTextAnchor300)). |
| Access Control | Encryption can be employed to limit access to sensitive information and resources in IoT devices. Encrypting data at rest or in transit allows organizations to give access to only authorized individuals, reducing the risk of data breaches. |
| Securing Firmware Updates | IoT devices frequently require software upgrades that fix flaws and enhance functionality. Encryption guarantees that these updates are securely communicated and implemented, preventing hackers from intercepting them and incorporating harmful code ([Kvarda, Hnyk, 2017](#979-8-3693-9225-6.ch011.bits-pdf.xhtml#_idTextAnchor306)). |

As a whole, encryption is a critical component of IoT cyber security, protecting against a variety of threats such as eavesdropping, tampering, illegal access, and data breaches.
