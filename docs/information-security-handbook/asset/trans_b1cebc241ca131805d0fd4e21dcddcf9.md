

[Figure 9.9](#ch09.xhtml#fig9_9) shows in which phase dynamic and static tools will work in malware detection \[[14](#ch09.xhtml#ref9_14)\]. This paper suggests the different ransomware detection approach that analyzes the attack on the current running state of a computer by using the proposed model called finite state machine, which is used to synthesize the knowledge of the attack in the victim's system. Also, the author monitors the current system in terms of utilization, persistence through which the source of the attack can be discovered.

![Figure 9.9 Training phase in malware detection.](Images/fig9_9.jpg)

[Figure 9.9 Training phase in malware detection.](#ch09.xhtml#Ffig9_9)

## [9.3 Materials & Methods](#ch09.xhtml#c_sec9_3)

In this section, we see the various algorithms that are used for the prevention and detection of malware, as well as ransomware attack. Machine learning is the technique that is now trending in the detection of attacks, as we see in the previous section. In the testing phase, all the machine-learning algorithms are used in \[5\] SVM classifiers. Machine learning is not the only technique; there is deep learning \[[15](#ch09.xhtml#ref9_15)\], which is used for feature exploration in the Android system. The author proposes the TC-droid feature; it is a framework that depends on the text-classification method. TC-Droid implements the convolution neural network (CNN) to inspect the important information or knowledge. This extraction process has four types of features: permission, service, intent, and receiver. Once the feature extraction process is complete, the author trains the TextCNN for text classification. This is done in two categories, malicious and benign. We understand different attacks that happened and different techniques used for preventing attacks through [Table 9.2](#ch09.xhtml#table9_2).

[Table 9.2 Different Attacks Uses Different Techniques](#ch09.xhtml#Ttable9_2)

| Paper name || Types of Attack || Technique || Limitation/Future |

| --- | --- | --- | --- |

| Davies et al. \[[16](#ch09.xhtml#ref9_16)\] || 

1.  NotPetya

2.  Bad rabbit

3.  Phobos hybrid ransomware

 || 

1.  Recovery by using the AES Key from volatile type of memory helps in finding out the encrypted keys.

 || 

1.  This technique is not implemented in all the ransomware families, like WannaCry.

 |

| --- | --- | --- | --- |

| Hwang et al. \[[17](#ch09.xhtml#ref9_17)\] || 

1.  Ransomware attack

 || 

1.  Markov model

2.  Random forest model is a two-staged ransomware detection technique.

 || 

1.  When ransomware detection has a higher false-negative rate, it is disastrous for the system.

2.  More ransomware is required to generate like normalWare.

 |

| Vinayakumar et al. \[[18](#ch09.xhtml#ref9_18)\] || 

1.  Ransomware attack

 || 

1.  Two configurations of SVM: one is the linear kernel, and the second one is the radial basis function.

 || 

1.  This technique uses complex architecture. An enhanced MLP network can be made in the future.

 |

| Arabo et al. \[[19](#ch09.xhtml#ref9_19)\] || 

1.  Ransomware attack

2.  Benign attack

3.  Malware samples

 || 

1.  Uses the interrelation between process behavior, as well as its nature, to determine the ransomware. This can be done by using machine-learning techniques with a low false-positive and false-negative to distinguish the benign and other ransomware.

 || 

1.  In the future, the author will try to develop an early warning system that tells the victim in the first five seconds that a malicious attack has happened.

 |

| Mercaldo et al. \[[20](#ch09.xhtml#ref9_20)\] || 

1.  Mobile Malware attack through image

 || 

1.  By using the deep neural network architecture and to convert a binary to an image it can be done to encode a binary file into a PNG

 || 

1.  In the future author tries to use the formal verification method for an image that creates better performance.

 |

| Lei et al. \[[21](#ch09.xhtml#ref9_21)\] || 

1.  Ransomware attack

 || 

1.  A self-recovery service is proposed by the author to ease the damage done by the ransomware attack to the edge servers. Evaluation is done based on 

    1.  CPU usage

    2.  Disk Access Time

    3.  Disk Read/write speed

    4.  Disk Average transfer rate.

 || 

1.  SRS is the solution for IoT systems and in the future more of this type of solution may be suggested.

 |

| Zimba et al. \[[22](#ch09.xhtml#ref9_22)\] || 

1.  Wannacry Ransomware attack

 || 

1.  A cascaded network segmentation approach to uncover the artifacts which set the security in the network.

2.  Through static malware, the analysis author finds out the different techniques to propagate the ransomware and attack the CI components over the various network partitions.

 || 

1.  This technique can be implemented in intrusion detection systems in each segment in the future.

 |

In the above discussion, we saw the deep-learning and machine-learning techniques \[2\], but IoT is also one of the areas where we need to discuss ransomware because the internet of things is a network of the network where physical devices are connected. In IoT \[[23](#ch09.xhtml#ref9_23)\], physical devices can handle and organize the device; that's why they are called smart devices. This paper presents the crypto-wall attack works on detection model based on the communication, as well as the behavioral study of cryptowall for IoT. The suggested model works on the network traffic, especially TCP/IP traffic \[[24](#ch09.xhtml#ref9_24)\] over a server that extracts TCP/IP header and uses the C&C server for blacklisting to find out the ransomware attacks.

### [9.3.1 Algorithms Used for Ransomware/Malware Detection](#ch09.xhtml#c_sec9_003_001)

The author proposed \[[25](#ch09.xhtml#ref9_25)\] a new technique that uses the machine-learning technique to detect and classify the spreading phase of a ransomware attack affecting the integrated clinical environment here. OC-SVM and Naïve Bayes detecting strategy work very well in detecting some of the dangerous malware like Wannacry, Petya, BadRabbit, and PowerGhost. The author also finds the worst case and best case of detecting the ransomware attack. Besides this, author uses the anomaly-detection method, and probabilistic classification technique of ML technique selection has taken place. Evaluation is done by using different measures like precision, recall, and accuracy, as well as F1-score through which the author analyzes the previous and proposed method improvement. Further, we understand the algorithmic point of view through the given in [Table 9.3](#ch09.xhtml#table9_3) below.

[Table 9.3 Algorithm Used for Different Attacks](#ch09.xhtml#Ttable9_3)

| Paper Name || Attack and Techniques || Algorithm Used/Work done |

| --- | --- | --- |

| Liu et al. \[[26](#ch09.xhtml#ref9_26)\] || 

1.  Ransomware attacks and tracks the online behavior and understands each source, as well as destination entity.

 || 

1.  LooCipher is used to detect the ransomware, which works on the approach called Identify-Collect-Examine-Analyze-Present.

 |

| --- | --- | --- |

| Mitchell et al. \[[27](#ch09.xhtml#ref9_27)\] || 

1.  North Korean Ransomware

2.  Russian Ransomware

3.  Chinese Ransomware

 || 

1.  Various algorithms like AES for encryption techniques.

 |

| Zavarsky et al. \[[28](#ch09.xhtml#ref9_28)\] || 

1.  Ransomware attack, and detection is done for the Windows operating system.

 || 

1.  Uses the Message digest-5 for each sample for checksum values that are analyzed

2.  PEiD tool is used to reveal packers, cryptors, and compilers

 |

| Alsoghyer et al. \[[29](#ch09.xhtml#ref9_29)\] || 

1.  Android Ransomware attack and machine learning is used for detection and for doing permission analysis

 || 

1.  The sequential minimal optimization algorithm

2.  Naïve Bayes algorithm for cross-validation testing.

3.  Random forest and Decision trees show the best result.

 |

