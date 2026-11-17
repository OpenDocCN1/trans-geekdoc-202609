
## CHAPTER 8

## The Fusion of Human-Computer Interaction and Artificial Intelligence Leads to the Emergence of Brain Computer Interaction

M. Kiruthiga Devi*

Department of Computer Science and Engineering, Sri Sai Ram Engineering College, Chennai, India

Abstract: A personal computer may be used, with input devices such as a keyboard, mouse, and joystick serving as an interface between the computers and the human. The euphemistic, physically challenged are unable to use these computer systems, therefore, BCI technology has advanced external applications to be managed without physical movements in order to assist these physically disabled people and address the limitations of HCI. The technological advancement in the field of cognitive neuroscience and brain imaging has enabled it to communicate directly with the human brain instead of using an interface. Rather than generating signals from muscle movements, these systems use brain activity to monitor computers or communication devices. Researchers in the field of Human-Computer Interaction (HCI) look at ways for machines to utilize as many sensory sources as possible. Further, researchers have begun to consider implicit types of data, input that is not specifically performed to instruct a machine to perform a task. Systems can evolve dynamically based on this data in order to assist the user with the task at hand. Here we discussed components of Brain-Computer Interface, its characteristics and challenges. The researchers are attempting to replace conventional classifiers with Convolutional neural networks (CNNs) that would provide a promising advantage in classification. The EEG signals from the brain can be linked seamlessly to mechanical systems via BCI applications, making it a rapidly growing technology that has applications in fields such as Artificial Intelligence and Computational Intelligence.

Keywords: Actions, Atmosphere, Artificial intelligence, Brain computer interface, Convolutional neural networks, Classifiers, Communication, Computational, Deep Learning, Electroencephalographic, EEG, Human-computer interaction, Input devices, Movements, Machines, Machine learning, Mechanical system, Neuroscience, Physiology, Signals, Sensory, Support vector.

* Corresponding author M. Kiruthiga Devi: Department of Computer Science and Engineering, Sri Sai Ram Engineering College, Chennai, India; E-mail: kiruthigaprofessor89@gmail.com

## INTRODUCTION

Sensors are used to track some of the physical processes in the brain associated with specific types of thought [1]. As a result of these developments, brain-computer interfaces (BCIs) have been developed, allowing communication among systems that do not depend on the brain's usual peripheral nerve and muscle systems. Many factors have aided this advancement, including improved understanding of neurobiological processes, machine learning algorithms, and deep learning. A personal computer may be used as an interface between computers and humans with input devices such as a keyboard, mouse, etc. [2]. The disabled persons are unable to use these systems, but in order to assist these euphemistic physically challenged people and address the limitations of HCI, BCI technology has advanced, allowing external applications to be managed without the use of physical muscle movements. BCI calibration is difficult with two stages: the low signal-to-noise ratio (SNR) and high subject-to-subject variability. The amount of time needed for calibration varies depending on the type of paradigm used. It can still be reduced by half. If brain signals have a low Signal-to-Noise Ratio (SNR), BCI is most challenging when it comes to accurately determine human intentions [3]. The reality is that BCI's real-world implementation is limited by poor generalization potential and low classification accuracy.

Deep learning approaches have been used to work with brain knowledge in recent years to address the aforementioned challenges. While normally machine learning algorithms need to select features manually, deep learning can learn complex high-level features directly from brain signals, and its accuracy scales well with the size of the training data set [4]. It is possible to monitor the activity of the brain using different techniques, which can be categorized into two types: invasive and non-invasive. The non-invasive BCI system majorly uses Electroencephalogram (EEG) signals to capture brain signals from electrodes mounted on the scalp. EEG data is extremely noisy, therefore, it can be difficult to extract a coherent signal when your brains communicate through your scalp into the EEG sensor. As a result, it's critical to extract useful information from distorted brain signals and to develop a strong BCI system. When data from electroencephalographic (EEG) sensors is processed through brain-computer interfaces (BCIs), the number of channels, the amount of training data, and the signal-to-noise ratio affect the accuracy of classification [5]. In real-world applications, the SNR is the most difficult to modify of all these variables. The development of several preprocessing and feature engineering methods for reducing noise has been time-consuming and may result in information loss in the extracted features. Feature engineering is heavily reliant on human domain knowledge. Human experience can aid in capturing characteristics of some specific aspects, but it is inadequate in more general situations. An algorithm automatically extracts representative features as the result. Because most machine learning research focuses on static data, it is unable to reliably classify constantly evolving brain signals [6, 7]. BCI systems need to use novel learning methods to deal with dynamic data streams [8]. The benefit of deep learning is backpropagating. By back-propagating, it learns distinguishable information by utilizing the raw brain signals without the need to pre-process and engineer features. Furthermore, deep neural networks may use deep structures to capture latent dependencies and representative high-level features [9].

## COMPONENTS OF BRAIN COMPUTER INTERFACE

The primary objective of a Brain-Computer Interface is to detect and analyze the signals in the user's brain that indicate user intention and then transmit these signals to an external computer that executes the user instruction. A BCI-based system has four components that work together to achieve this objective as shown in Fig. (1).

![](img/0616422b380b1bd62613a261ed51be87_150_0.png)

Fig. (1). Components of BCI.

### Signal Acquisition

It is the first component that detects and analyses brain signals. The purpose of this component is to receive and register signals produced by neuronal action. It also transfers the resulting signals to the next part of the BCI component for signal enhancement and to reduce the noise [10].

### Feature Extraction

It is the first step in the signal processing of the Brain Computer Interface. Digital signals (such as signals corresponding to user intentions) are processed by analyzing different characteristics of the signals and translating them into acceptable commands for user output.

### Translation

In this stage of signal processing, the extracted features of the signal are passed to a translation algorithm. It converts the features into valid instructions that are sent to an external system in order to fulfil the purpose (e.g. the user’s intention is converted into complete instructions).

### Application/Device Output

A translation algorithm provides instructions for driving and controlling an output device. It helps users achieve their objectives such as selecting alphabets, controlling a mouse, moving a robotic arm, using a wheelchair, moving a paralyzed limb, etc. [11].

![](img/0616422b380b1bd62613a261ed51be87_151_0.png)

Fig. (2). Number of BCI related paper publication over the year.

## BCI CHARACTERISTICS

### BCI Systems are Classified according to how they use the Brain: Active BCI

This mechanism derives its effects from the brain’s voluntary programmed movements which are independent of external stimuli. In order to manage an application such as BCI, it is activated by a person’s deliberate motor imagery [12].
