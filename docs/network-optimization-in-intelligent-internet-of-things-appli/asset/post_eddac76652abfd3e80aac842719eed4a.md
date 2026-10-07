
## Lightweight Cryptography Algorithms in IoT

autonomous vehicles, security, and emergencies. These applications need a high-security framework. Some of these applications with security concerns are explained in this section:

### 11.3.3.1 Smart Cities

When it comes to enhancing people's lives with technology, automated cities play a major role. Smart cities can monitor and control major sectors such as climate change, scarcity of resources, and parking and transportation. Many of these services can be utilized through the smart card, which threatens citizens' privacy. These applications need to be designed with a high level of security concerning threats such as information leakage, traffic analysis, user impersonation, and smart theft. Blockchain technology enables communicating parties to exchange information securely while preserving privacy and threats. However, researchers need to pay much attention to threats to confidentiality, integrity, and authenticity.

### 11.3.3.2 Smart Health

Remote health monitoring systems monitor and analyze patients' health parameters remotely using sensor devices. However, ensuring the safety and privacy of applications is essential as it involves the life of patients. Such applications are vulnerable to threats such as:

- **Fingerprint and Timing-Based Snooping:** In this scenario, intruder tries to access information during data transit between sensors and the sensor to a private user location.

- **Router Attack:** As allowing data to be delivered remotely and encourages network versatility, e-healthcare systems require data to be delivered securely and protect user identity.

### 11.3.3.3 Smart Agriculture

With the use of modern technologies such as IoT, blockchain, cloud computing, and big data, agriculture information collected from various sensor nodes such as temperature, light, soil, and humidity can be analyzed with ease. The information collected from various sources is processed using various artificial intelligence (AI) programs and on the central server. Cyberattacks in agriculture are continuously increasing due to social networking, phishing, and other malware, such as banking fraud. The detect UAV-based communication is based on wireless communication. Therefore, the communication channels are highly vulnerable to snooping, dispatch systems, Wi-Fi, and data modification attacks. Some of the recent attacks on the agriculture sector are:

- **Data attacks** include false data injection, insider and cloud data leakage, and missing information attacks.

- **Networking and equipment attacks** contain side-channel, botnet, malware injection, DoS, and radio frequency jamming.

#### TABLE 11.2
Comparative Analysis of other Researchers' Work on IoT Security Issues

| Author & Ref. | Year | Vision | Security Concerns |
|---|---|---|---|
| Noor and Hassan [5] | 2018 | Analysis of IoT perception, network, and application layer. | RFID and WSN attacks such as jammers, injection, and side-channel attacks. |
| Rahimi et al. [11] | 2018 | Analysis of IoT security from 5G perspective. | Flooding on the cloud, RF jamming, sleep deprivation attacks. |
| Sfar et al. [12] | 2018 | IoT components and their interaction with each other and the environment. | Privacy, trust, integrity, and authentication. |
| Butt et al. [13] | 2019 | IoT applicability in the health sector and security issues. | Insider and external attack. |
| Shouran et al. [1] | 2019 | Smart home privacy issues | Eavesdropping, replay, user impersonation attack. |
| Song et al. [14] | 2020 | Security concerns in green IoT-based architecture are analyzed. | Man-in-middle attack, attack on cloud storage |
| Tsikanas et al. [15] | 2021 | Analysis of the industrial IoT sector. | Phishing attacks, supply chain attacks |

## 11.4 IOT SECURITY ISSUES, REQUIREMENTS, AND THREATS

Table 11.2 represents the major security concerns, requirements, and threats concerning the IoT communication framework. The in-detail descriptions are discussed in this section:

### 11.4.1 SECURITY ISSUES

To achieve a high-security IoT framework, the following issues need to be considered:

- **Maintaining Data Integrity:** The IoT data needs to maintain the integrity of the network. Integrity ensures reliable communication between users. The IoT architectures must be capable of providing integrity. Integrity confirms that the data is safeguarded from unauthorized users.

- **Maintaining Data Confidentiality:** It ensures the user's confidential information cannot be leaked to any unauthorized user. The major concern of IoT smart objects is maintaining the confidentiality of data among communicating entities. In addition to that, important communication protocols such as constrained application protocol (CoAP), IEEE 802.15.4 standard, and the IPv6 over low-power wireless personal area networks (6LoWPAN) are used to achieve data confidentiality.

- **C. Maintaining Privacy of Communication:** The privacy of communication, data, and images are the main priority and security concerns. Such issues arise due to multiple resource-constrained device connectivity. User credentials such as passwords, IDs, images, and other sensitive information such as location need to be maintained.

- **D. Ensuring Mutual authentication:** Authentication is required at different levels in the IoT framework as it involves sensors, Gateway Node (GWN), and user devices. The user’s authenticity should be verified before communication takes place [16].

### 11.4.2 Key Requirements for IoT Security

Therefore, an hour is required to use IoT communication so that the majority of people can effectively use it. Confidentiality, authentication, and integrity are important requirements of IoT communication. The IoT devices are resource-constrained. Therefore, there must be a strong authentication method to identify.

### 11.4.3 IoT Threats

All IoT devices are receiving data over the internet, which is susceptible to many attacks. Considering the above-mentioned cases, IoT systems are categorized as:

- **Denial of service (DoS):** Either by jamming or flooding the network.

- **Impersonation attack:** An attacker by masquerading like a legitimate user.

- **Reply attack:** A malicious node sends the same message to the receiver.

- **Mutual authentication:** In an IoT scenario, between sensor nodes and base station.

- **Man-in-middle attack:** Where the intruder may attempt to control the communication channel.

## 11.5 RECENT LIGHTWEIGHT CRYPTOGRAPHY FOR IOT

### 11.5.1 ASYMMETRIC ENCRYPTION

Public key (asymmetric) encryption is used to secure IoT communication by sharing secret keys with the legitimate user. The encryption is based on the mathematical framework, where public and private keys are generated randomly. Anyone with access to public keys can encrypt data. Recently, [19] analyzed that to the complexity of integer factorization, the popularity of public key encryption is increasing. The researchers [20] also focus on elliptic curve cryptography (ECC) due to its advantages in lightweight cryptography. In IoT, alternative approaches such as hyper-elliptic cryptography [21], NTRU [22], and Blue Ray [23] were proposed, which are based on the shorter key size.

### 11.5.2 SYMMETRIC CRYOGRAPHY

The single key is used at both ends to send and receive messages. The major challenge is to share secret keys with legitimate users. It is difficult for eavesdroppers in the communication channel; therefore, ensuring that keys are shared with only legitimate users is a difficult task. The symmetric key cryptography algorithm, such as advanced encryption standard (AES), is popular for encrypting data [3].

### 11.5.3 HASHING

Hash-based authentication is widely used for ensuring integrity, verification, and secure digital signature and hash-based biometric authentication. The efficiently implemented hashes are believed to be resistant to quantum adversaries. Hafizul and Prosanta [24] security issues in IoT communication have been prevalent for many years as IoT devices with the heterogeneous type of data sharing and generation. Therefore, the authors [25] work on securing multimedia communication. Their protocol use authentication to secure user credentials based on the two-step process. Therefore, it allows only authenticated users to access the communication channel.

## 11.6 LIGHTWEIGHT SCHEMES FOR IOT

IoT devices have limited batteries and computational capabilities. Therefore, it is expedient to develop lighter yet stronger cryptographic solutions. Based on AES primitive, the author [26] proposed a lightweight security enhancement scheme. Their work is based on a dynamic-key generation process based on time to provide authentication. Symmetric algorithms such as Height, Tiny Encryption Algorithm (TEA), and RC5 provide solutions for possible attacks such as saturation-related and differential attacks [5]. A secured IoT communication framework is
