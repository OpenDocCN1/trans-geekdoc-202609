
communications, it is timely to study the security and privacy concerns of machine learning systems in the area of RFML.

## 2.1.1 Scope and Background

Machine learning has found diverse and far-reaching applications ranging from computer vision and NLP to cyber security and autonomous navigation. Over time, machine learning capabilities have evolved from engineering intelligent machines and programs, to learning without being explicitly programmed, and now to learning using deep neural networks, as illustrated in [Figure 2.1](#). Recently, machine learning has also been applied to the wireless domain. This emerging research area is colloquially referred to as RFML. As wireless technologies evolve over time (as depicted in [Figure 2.2](#)) to meet the ever growing demand of supporting high rates, high reliability, and low latency with smart edge devices in heterogeneous networks, machine learning has provided an automated means to learn from and adapt to spectrum data and solve complex tasks in the wireless domain. Empowered by the ever increasing hardware accelerators for computing, machine learning systems based on advanced deep learning architectures have been considered for various wireless applications in the emerging landscape of next-generation communications systems (see [Figure 2.3](#)). These applications include but are not limited to spectrum sensing applications (such as signal detection, estimation, classification, and identification), waveform design (such as beam optimization, power control, and channel access), channel estimation, emitter identification, cognitive jamming, and anti-jamming. These research thrusts are expected to play an increasingly prevalent role in the development of next-generation machine-learning-empowered wireless communications [3].

Engineering of making intelligent machines and programs

Ability to learn without being explicitly programmed

Learning using deep neural networks

![](img/efffc69cb8cda75bcf341884e3396898_67_0.png)

FIGURE 2.1 Evolution of machine learning over time.

![](img/efffc69cb8cda75bcf341884e3396898_67_1.png)

FIGURE 2.2 Wireless technologies evolving over time.

![](img/efffc69cb8cda75bcf341884e3396898_68_0.png)

**FIGURE 2.3** Wireless applications and objectives that will benefit from machine learning.

Recent research in the more established machine learning domains has indicated that machine learning is vulnerable to adversarial manipulations, forming the basis for the emerging field of adversarial machine learning that studies learning in the presence of adversaries [4–7]. However, the impact of machine learning security on RFML technologies has not been fully understood yet [8–10]. Therefore, it is timely to study wireless security in the context of adversarial machine learning and understand its implications for 5G and later communications systems. While adversarial machine learning can take a variety of shapes and forms, our focus is on adversarial techniques in the context of deep neural networks since they currently represent the majority of commonly used RFML architectures.

Research efforts that are needed to address machine learning for wireless security are diverse, including but not limited to the following directions:

- *Security attacks built upon adversarial machine learning*: evasion attacks (adversarial examples), poisoning (causative) attacks, Trojan (backdoor or trapdoor) attacks, and generative adversarial learning for signal spoofing
- *Privacy threats for machine learning solutions*: membership inference attacks, model inversion, and physical layer privacy
- *Machine learning hardening techniques*: privacy-preserving learning, secure learning, hardware and software implementations, edge computing, testbeds, experiments, and datasets
- *Expansion of machine learning applications for wireless security*: device identification, spectrum monitoring, RF fingerprinting, smart jamming, smart eavesdropping, localization, covert communications, authentication, anonymity, intrusion detection, and IoT security

The remainder is organized as follows. Section 2.2 presents different types of adversarial machine learning attacks and describes the vulnerabilities of machine learning systems used in the wireless domain. Section 3.3 discusses challenges and gaps for machine learning applications in wireless communications and security. Section 2.4 makes concluding remarks with recommendations for future research directions.

## 2.2 ADVERSARIAL MACHINE LEARNING

Different types of attacks built upon adversarial machine learning are illustrated in [Figure 2.4](#). Adversarial machine learning studies the attacks launched on the training and/or testing of machine learning models. Recently, these attacks have been extended to wireless applications and have been shown to be stealthier and more energy efficient compared to conventional attacks such as brute-force jamming of data transmissions [11,12] in the presence of different levels of wireless network uncertainty.

Exploratory attacks have been studied in [18, 19] to learn the transmitting behavior of a dynamic spectrum access (DSA) system and to develop jamming strategies accordingly. The exploratory attack can be considered the initial step for various follow-up black-box attacks without requiring any knowledge about the machine learning algorithm (such as its type, its hyperparameters, and the underlying training dataset). In this context, active learning [20] can be applied to reduce the number of data samples needed by the exploratory attack [21].

- *Evasion (adversarial) attack*: The goal of the evasion attack is to tamper with the input data in test time and fool a machine learning algorithm into making errors in their decisions. Figure 2.5 shows two examples of the evasion attack, one from computer vision and another from wireless signal classification. Note that the evasion attacks in the wireless domain require the over-the-air manipulation of input data and need to account for channel effects (for both the victim system and the adversary). Most of the studies on evasion attacks in the wireless domain have considered the modulation classifier as the victim system [22–32]. Additional constraints on communication performance at one receiver have been imposed in [33–35], along with the evasion attack launched on another receiver. This setting also extends to adversarial machine-learning-driven covert communications, where the objective is to hide communications from eavesdroppers equipped with machine learning algorithms for spectrum sensing [36]. Various defense mechanisms have been proposed against evasion attacks [27, 37–40], such as statistical outlier detection and certified defense. Evasion attacks have been also considered for other machine learning applications including spectrum sensing [41–43], end-to-end communications with an autoencoder (that consists of an encoder at the transmitter and a decoder at the receiver [44, 45], multiuser power control [46, 47], initial access for directional transmissions [48], and DSA systems [49].

![](img/efffc69cb8cda75bcf341884e3396898_72_0.png)

![](img/efffc69cb8cda75bcf341884e3396898_72_1.png)

FIGURE 2.5 Examples of evasion (adversarial) attack from (a) computer vision [4], (b) wireless signal classification.

- **Poisoning (causative) attack:** The goal of the poisoning attack is to tamper with the (re)training process of a machine learning algorithm such that the machine learning algorithm makes errors in test time [50]. The poisoning attacks have been considered for spectrum sensing [42, 43] and cooperative spectrum sensing [51–53] as the machine learning extension of spectrum sensing data falsification attacks [54, 55]. As spectrum environments change over time, it is useful to update the machine learning models. To that end, causative attacks can be launched when the wireless system retrains the machine learning models over time.
- **Trojan (backdoor) attack:** The goal of the Trojan attack is to insert Trojans (i.e., backdoors or triggers) into some training data samples in training time and then activate them in test time such that the machine learning makes errors in test time only for selected input samples. For example, [56] investigated input samples with Trojans while the machine learning model keeps high accuracy for the input samples that are not poisoned with Trojans. The Trojan attack was considered in [57] against a wireless signal classifier. For that purpose, the adversary
