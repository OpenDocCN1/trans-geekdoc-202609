
# Cyber Security for Next-Generation Computing Technologies

Finally, the KDD data is old and no longer accurately represents the current network environment [73, 74].

### 3.6.3 NSL-KDD DATASET

This dataset is considered the new version of the previous one. This dataset contains 22 different attack types, which are categorized into four major groups. It is comprised of the KDDTrain+ as the training set and the KDDTest+ and KDDTest-21 datasets as the testing set [75]. The latter is more challenging to classify due to its unbalanced representation of normal and attack records. However, the NSL-KDD still lacks up-to-date data, particularly for minority class samples. Despite this limitation, the dataset represents a significant improvement over its predecessor and serves as valuable resource for network intrusion detection research.

### 3.6.4 ADFA DATASET

The ADFA dataset specifically consists of datasets for host-level intrusion detection systems and is commonly utilized in cyber science [76]. Kernel is considered the main facility to interact between the user space and kernel space. ADFA-LD is presented in figure. Further, data can be found on two platforms, which include Linux and Windows.

### 3.6.5 UNSW-NB15 DATASET

The UNSW-NB15 dataset was formulated by the University of South Wales. The field of IDS on a variety of datasets, including UNSW-NB15, CAIDA, ADFA-LD, and UNM [77, 78]. As a new and representative IDS dataset, the UNSW-NB15 has been utilized and currently has less influence than the KDD99 [79].

## 3.7 SURVEY OF ML-AIDED TECHNIQUES IN CYBER SECURITY

This section presents different machine-learning-aided techniques proposed for cyber attack detection, which have been evaluated on datasets with performance metrics. The proposed methods include both supervised and unsupervised techniques and various ML-aided techniques proposed for cyber attack detection, evaluated on various datasets with performance metrics.

In the supervised techniques, five methods have been proposed for detecting different types of attacks. In [80], a naive Bayes classifier to accurately classify the labeled data into the attack and normal classes. The results show improved accuracy, precision, and recall. In [81], clustering is used to extract cluster centers and identify the nearest node. The K-NN and K-means algorithms are used for this method, and the results show improved recall and accuracy.

In [82], the proposed method uses a one-class SVM to evaluate the practical feasibility of incorporating contextual and quantitative information of net records using a specific kernel function. The results show high accuracy. In [83], three experiments were conducted to evaluate RT-IDS for different machine-learning classification approaches. The results show that the DT algorithm achieves the accuracy, while the NB has the lowest. In [84], the proposed IDS is implemented with a neuro tree for improved detection accuracy. The results show improved accuracy for both the RF and the C4.5 algorithms.

In the unsupervised techniques, two different methods have been proposed. In [85], a new method proposed that combines different techniques. The results show improved precision and recall. In [86], a new dataset is created by combining the voted outputs of built models on the GA suggested features of the NSL KDD dataset based on five different labels, by executing kernel extreme learning machine (KELM) with optimized parameters using GA. The results show high accuracy, recall, and precision for SVM, MLP, DT, and K-NN algorithms (Table 3.3).

### 3.8 SURVEY OF DI-ALED TECHNIQUES IN CYBER SECURITY

In [87], a supervised approach is described that uses the RNN technique for cyber threats. Other research [88] uses another unsupervised approach that uses long term memory (LSTM) to secure channels. In [89], a supervised approach is simulated to identify categories of images in emails, achieving an accuracy of 75.10%. Another unsupervised approach [90] compares two deep neural network architectures, deep belief networks (DBNs), and cortical attention (CA) DNNs, for spam classification on the Spam dataset. The CA DNN architecture achieved higher accuracy than DBN with a six-layer architecture and decreasing hidden neurons, achieving an accuracy of 96.40%.

Researchers [91] have also described an unsupervised approach that uses deep learning-based anomaly detection methods, including denoising autoencoder (DAE), stacked autoencoder (SAE), generative adversarial network (GAN). Another unsupervised approach [92] describes an unsupervised approach focusing on the KDD99 dataset. [93] provides information on smart grid detection.

## 3.9 COMPARATIVE ANALYSIS OF ML/DL IN CYBER SECURITY

In this section, the comparative analysis of ML and DL in cyber security suggests that DL have the potential to outperform traditional techniques. However, the reliability and interpretability of DL remain a challenge.

### TABLE 3.3 SURVEY OF ML-AIDED TECHNIQUES

| Ref | Attack Type | Proposed Solution | ML-Aided Technique | Dataset | Performance | Result |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Supervised | [80] DoS, normal | A naive Bayes classifier to accurately classify the labeled data into the attack and normal classes. The results show improved accuracy, precision, and recall. | classify the labeled data into the attack and normal classes. The results show improved accuracy, precision, and recall. | NB, K-means | ISCX | Precision: 85.02% | Recall: 87% Accuracy: 97.42% |
| Supervised | [81] DoS, R2L, Probe | Clustering is used to extract cluster centers and identify the nearest node. The K-NN and K-means algorithms are used for this method, and the results show improved recall and accuracy. | K-NN, K-means | KDD-99 | Precision: 90.10% | Recall: 91.40% Accuracy: 96.81% |
| Supervised | [82] DDoS, TCP | The proposed method uses a one-class SVM to evaluate the practical feasibility of incorporating contextual and quantitative information of net records using a specific kernel function. The results show high accuracy. | One class SVM | MATPOWER | Precision: 82.42% | Recall: 82.40% Accuracy: 95.80% |
| Supervised | [83] DoS, normal | Three experiments were conducted to evaluate RT-IDS for different machine-learning classification approaches. The results show that the DT algorithm achieves the accuracy, while the NB has the lowest. | NB, DT, NN | KDD-99 | Precision: 90.10% | Recall: 87.21% Accuracy: 91.50% |
| Supervised | [84] DoS, R2L, U2R | The proposed IDS is implemented with a neuro tree for improved detection accuracy. The results show improved accuracy for both the RF and the C4.5 algorithms. | RF, C4.5 | KDD-99 | Precision: 89.21% | Recall: 92.10% Accuracy: 88.28% |
| Unsupervised | [85] DoS, R2L, U2R | A new method proposed that combines different techniques. The results show improved precision and recall. | SVM, MLP, PCA | ISC 2012, NSL-KDD, Kyoto 2006 | Precision: 85.02% | Recall: 87% Accuracy: 97.42% |
| Unsupervised | [86] DoS, R2L, U2R | A new dataset is created by combining the voted outputs of built models on the GA suggested features of the NSL KDD dataset based on five different labels, by executing kernel extreme-learning machine (ELM) with optimized parameters using GA. | SVM, MLP, DT, K-NN | NSL-NED | Precision: 94.29% | Recall: 82.42% Accuracy: 96.51% |
