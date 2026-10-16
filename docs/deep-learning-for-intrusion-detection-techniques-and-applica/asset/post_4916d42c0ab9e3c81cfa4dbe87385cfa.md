
Common DL architectures for IDS include as follows:

- **CNNs:** These are helpful at recognizing spatial patterns in network traffic, for example, characteristics within packet sequences that may point to an attack.
- **RNNs and Long Short-Term Memory (LSTM) Networks:** These models are great for estimating sequential data, making them suitable for detecting time-dependent attacks in IoT traffic.
- **Autoencoders:** These unsupervised learning models detect anomalies by learning to reconstruct normal system behavior, flagging deviations as potential intrusions.

## 12.3.1 Implementation Examples

a) **Detection of Anomalous Activities in Medical Devices:** DL-based IDS can monitor clinical devices in healthcare IoT, like insulin pumps or pacemakers, for uncommon behavior that could indicate malicious activity. For example, DL models have been used to recognize the normal working behavior of medical devices and can pick out deviations due to attacks [27].

b) **Mitigating Threats in Agricultural IoT:** IoT systems are utilized in intelligent farming to reveal crop fitness, control equipment, and control irrigation [28]. Unexpected increases in data traffic, such as unusual communication between devices, can also imply intrusions that can be tracked on DL-based IDS. For example, an anomaly system can help shield against cyberattacks targeting smart agriculture [29].

## 12.4 Ensuring Data Safety and Privacy in Deep Learning-Based Intrusion Detection Systems (IDSs)

In secure IoT contexts, the privacy and security of data are critical with respect to DL-based IDS solutions. As IoT devices generate large amounts of sensitive data, it is essential to provide strong security mechanism techniques to ensure the privacy of the data.

### 12.4.1 Data Security Measures

### 12.4.1.1 Encryption Techniques for IoT Data

a) **End-to-End Encryption (E2EE):** The information received from IoT devices contains sensitive facts. The network traffic records from IoT gadgets are analyzed using a DL-based IDS system. The E2EE approach is required to prevent unwanted access to crucial detection device data received from IoT devices [30]. A lightweight encryption technique referred to as elliptic curve cryptography (ECC) is often employed in IoT environments to shield data from manipulation [31].

b) **Homomorphic Encryption:** Sensitive scientific data in cloud-based structures must be protected, and homomorphic encryption makes it possible to process data while maintaining confidentiality. The ability of homomorphic encryption to process encrypted data without the need for decryption is crucial for protecting patient privacy during medical evaluation and diagnostic procedures like coronary heart attack risk prediction and ECG monitoring, showcasing the effectiveness of this cryptographic method in real-world scientific applications [32].

### 12.4.1.2 Role of Secure Communication Protocols

a) **TLS/SSL with DL Models:** Using a DL-based intrusion detection system, network traffic information is exchanged between edge devices and centralized structures for training or evaluation. Datagram Transport Layer Security (DTLS) or Transport Layer Security (TLS) are secure communication protocols that defend the data from unwanted access [33]. By preventing man-in-the-middle attacks, these protocols guarantee the integrity of the data collected for anomaly detection.

b) **MQTT with Encryption:** Many IoT networks use lightweight protocols, such as Message Queuing Telemetry Transport (MQTT), to ensure secure communication. The protection of data shifting across the network and information interchange between IoT devices and IDSs is ensured by the addition of encryption layers such as TLS or Secure Socket Layer (SSL) [34].

### 12.4.2 Privacy Protection

### 12.4.2.1 Differential Privacy Techniques in Data Sharing

a) **Differential Privacy (DP) in Training Data:** Large volumes of network traffic data, which may contain sensitive information, are needed for training DL models for intrusion detection. DP approaches guarantee that user or device data is protected during the model training process. By adding statistical noise to the data, DP protects the privacy of individuals while allowing the model to learn effectively from aggregated information [35].

b) **Federated Learning for Intrusion Detection:** In federated learning, the model used for DL is trained directly on IoT devices using their information, while the central server only receives the updated model parameters, not the actual data. This ensures that sensitive data remains on the device, reducing the risk of exposure during the training phase of the IDS model [36].

### 12.4.2.2 Edge Computing to Reduce Exposure of Sensitive Data

a) **On-Device Detection and Analysis:** DL-based IDS may immediately evaluate and identify anomalies on IoT devices or adjacent edge nodes by utilizing edge computing. This lowers the danger of data breaches during transmission by sending less sensitive data to the cloud for centralized processing [37]. To protect privacy, an IoT surveillance system might, for instance, locally process video data for intrusion detection rather than uploading raw footage to the cloud.

b) **Privacy-Preserving Machine Learning (PPML):** Secure multiparty computation (SMPC) and homomorphic encryption are two PPML techniques that allow DL models to learn from and be assessed on encrypted data without compromising privacy [38]. Within the context of the IoT, this means that the sensitivity of individual data is covered even when it is aggregated for intrusion detection from multiple sources.

### 12.4.3 Case Studies

a) **Healthcare Example: Protecting Patient Health Data in Wearable Devices:** Wearable technology within healthcare IoT, such as insulin pumps and heart rate monitors, produces personal fitness records that need to be protected. By analyzing data from numerous gadgets, a DL-based IDS can identify anomalous patterns that point to security risks (such as intentional manipulation or illegal access). For example, the machine uses encrypted information and differential privacy to locate intrusions throughout the analysis phase even while maintaining the privacy of vital patient records. On-device threat detection can also be made viable via federated learning, which eliminates the need to share health statistics with outside servers [39].

b) **Agriculture Example: Preventing Data Tampering in Smart Farming Systems:** IoT sensors in smart agriculture keep a watch on vital environmental parameters together with crop health, temperature, and soil moisture. A DL-based IDS is used to discover harmful records tampering or network intrusions. Sensor statistics handled at the edge layer are safeguarded against manipulation or eavesdropping through the use of secure conversation protocols like DTLS and lightweight encryption [40]. In addition to enhancing privacy, localized statistics processing reduces the amount of personal agricultural records made available to the cloud [41].

## 12.5 IoT Operations with Security Optimization

To enhance the efficiency and reliability of the device, the integration of IDS in IoT environments performs a crucial role. The IDS device can quickly discover, analyze, and respond to potential threats, ensuring privacy and preventing negatively affected operations. The environments that require continuous, real-time monitoring, like healthcare and agriculture, are crucial and thus need maintained system security to ensure that the devices remain operational and the data remains reliable and accurate. [42].

Considering the healthcare scenario, various medical devices, like wearable health monitors and implants, are nowadays being used for continuous patient health monitoring without any interruption. If these devices are compromised, it could result in false data, which in turn could lead to incorrect treatment affecting the patient's health. Thus, by securing these devices with IDSs, the healthcare devices can ensure that abnormal activities, such as data breaches or unauthorized access that compromise patient data, can be secured and will avoid delaying treatment for the patient. [43].

The various IoT devices used in agriculture, like crop health monitoring systems and smart irrigation systems, are integral for optimizing resources and ensuring the processes used for farming practices are efficient. [44]. A malfunction in these devices could lead to crop damage or resource wastage. The IDS in agricultural IoT environments produces an additional layer of security that ensures that it cannot be manipulated by any of the threats, thereby maintaining operational efficiency and optimizing agricultural productivity.

To secure data in an IoT network, the primary challenge is to provide a bridge between security and performance, which are directly proportional to one another. The IoT devices are constrained in terms of power, storage, computing, and energy consumption, thus making it crucial to apply lightweight security measures. Traditional security systems, such as signature-based intrusion detection of IoT environments because of their high resource consumption, fail to meet the balance between the security and performance requirements of IoT environments.

To understand and tackle this challenge, lightweight DL models are more in demand, as they are specially designed to work within the resource-constrained devices of IoT. The DL models are advanced enough to perform intrusion detection
