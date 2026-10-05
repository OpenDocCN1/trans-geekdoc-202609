# Comparative Analysis of Machine and Deep Learning for Cyber Security

nodes—visible layer and hidden layer—and each layer has a set of neurons. RBM tries to learn the distribution of the input data by updating the weights linking the nodes of the visible and hidden layers. The weights are updated using a technique called contrastive divergence [65]. RBM is used for a wide range of applications, such as image recognition, speech recognition, and collaborative filtering.

# 3.5.14 AUTOENCODER

Autoencoder is an unsupervised neural network used to reduce noise. Autoencoder consists of four parts: encoder, bottleneck, decoder, and reconstruction loss. The encoder learns how to compress the data. [66].

# 3.6 COMMONLY USED CYBER SECURITY DATASETS

ML techniques are quite helpful in detecting cyber threats. However, simulating a novel dataset is considered a tough job. A benchmark dataset can be used by many researchers, providing convenience and reliability. Using already available network security datasets can save a lot of time and increase the research efficiency by providing quick access to the required data for research.

# 3.6.1 DARPA IDS DATASET

The DARPA Intrusion Detection Data Sets, under the direction of DARPA and AFRL/SNIS, are collected and published by The Cyber Systems and Technology Group of MIT Lincoln Laboratory for evaluating computer network IDS [67]. This standard dataset provides a large amount of background traffic and attack data, with three primary subsets: (1) the 1998 DARPA Intrusion Detection Assessment Dataset, which includes seven weeks of training data and two weeks of test data; (2) the 1999 DARPA Intrusion Detection Assessment Dataset, which includes three weeks of training data and two weeks of test data; (3) the 2000 DARPA Intrusion Detection Scenario-Dataset, which includes LDDOS 1.0 Attack Scenario Data, LDDOS 2.0.2 Attack Scenario Data, and Windows NT Attack Data [68].

# 3.6.2 KDD CUP 99 DATASET

The KDD Cup 99 dataset is a widely used dataset for IDS, based on the DARPA 1998 dataset. It contains 4.9 million records containing total of 22 types of attack [69]. KDD Cup 99 is used to provide a full set of training and testing data. The so-called 10% subset was created to address the huge amount of connection records present in the full set, with some Dos attacks having millions of records [70]. Training and testing datasets have different probability distributions, and the 10% subset was intended for training while the corrected subset can be used for performance testing with over 300,000 records containing 37 different types. Moreover, the testing set has specific attack types that do not appear in the training set, making it a more realistic basis for IDS [71, 72].