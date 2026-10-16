# 11.5.3.3 Real-World Implementations

+   - GNN-based IDS achieved 96% accuracy in detecting blackhole attacks and Sybil attacks in MANETs [31].
+   - LSTM models successfully identified malicious route alterations in dynamic vehicular ad hoc networks (VANETs) [32].
+   - RL-driven IDS are adapted to change MANET topologies, improving threat detection over time.

Adaptive, real-time IDS solutions in resource-constrained and decentralized MANET environments are provided by DL. These solutions secure communication in military networks, IoT networks, and vehicular networks. Modern wireless networks have been revolutionized by DL-based IDSs, which counteract security threats in the IoT, 5G, and MANET environments—scenes rife with not just traditional but also entirely novel forms of cyberattack. Using CNNs, RNNs, LSTMs, GANs, transformers, and RL, anomaly detection in IDS models can recognize routing attacks, DDoS threats, and network slice vulnerabilities with high precision [33].

# 11.6 Challenges and Future Research Directions

DL-based IDSs have substantially improved network security in recent times. They fall under the category of artificial intelligence (AI), along with other sophisticated machine learning methods. DL relies on artificial neural networks for its framework and is not directly interpretable. Because proximal features handily separate benign and malicious traffic, the realization has occurred that, with a few exceptions, well-designed IDSs are not necessary to achieve a high level of security. We explore these key challenges with AI-based intrusion detection and outline potential future solutions.

# 11.6.1 Adversarial Attacks Against Deep Learning IDS

DL models are vulnerable to adversarial attacks, where attackers manipulate input data to mislead IDS models into misclassifying malicious traffic as benign. These attacks exploit weaknesses in DL-based IDSs, reducing their reliability in real-world scenarios [34].

# 11.6.1.1 Techniques Used by Attackers to Evade IDSs

Attackers can bypass DL-based IDSs using adversarial techniques as detailed below:

+   - Evasion Attacks: Attackers introduce minor perturbations in network traffic data to fool IDS models while maintaining functionality.