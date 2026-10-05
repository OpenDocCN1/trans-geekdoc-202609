# Cyber Security for Next-Generation Computing Technologies

In summary, supervised learning is a powerful approach to intrusion detection that can be used to classify network traffic as normal or malicious based on labeled examples. Decision trees, SVMs, and ANNs are popular algorithms used in supervised learning for IDS. However, the availability and quality of labeled data and the risk of overfitting are important considerations when using this approach.

# 7.6 LITERATURE REVIEW

Intrusion detection systems (IDSs) have become an essential component of network security. IDS are designed to detect and respond to malicious activities in computer systems and networks. There are two types of IDS: signature-based and anomaly-based. signature-based IDS detect known attacks by comparing network traffic against a database of attack signatures, while anomaly-based IDS detect unknown attacks by detecting deviations from normal network behavior [77].

In recent years, research has focused on enhancing the accuracy and efficiency of IDS through the use of machine learning (ML) techniques. ML-IDS are capable of learning and adapting to new threats without the need for manual signature updates. Researchers have employed a wide range of ML algorithms, including decision trees, neural networks, support vector machines, and ensemble methods, to improve the accuracy and efficiency of IDS.

Several studies have evaluated the effectiveness of ML-IDS using the UNSW-NB15 dataset. Liu et al. (2020) proposed a deep network-based IDS that achieved an accuracy of 99.7% and an F-score of 0.997. The study by Laczano et al. (2018) used a hybrid IDS based on a random forest algorithm and achieved an accuracy of 99.1% and an F-score of 0.988.

In addition to ML techniques, researchers have also explored the use of other methods to improve IDS performance. For instance, several studies have used feature selection techniques to reduce the dimensionality of data and improve the accuracy of IDS. Liu et al. (2019) used a feature selection method based on the Relief algorithm and achieved an accuracy of 99.4% and an F-score of 0.994 [78].

Furthermore, the use of deep learning techniques, such as convolutional neural networks (CNNs) and recurrent neural networks (RNNs), has also gained popularity in IDS research. These techniques have been shown to effectively capture temporal and spatial features in network traffic data. For instance, Haddouti et al. (2020) proposed a CNN-based IDS that achieved an accuracy of 99.1% and an F-score of 0.99, while Huang et al. (2021) proposed an RNN-based IDS that achieved an accuracy of 98.9% and an F-score of 0.986.

Another area of IDS research is the use of ensemble methods, which combine multiple IDS to improve the accuracy and robustness of the system. For instance, Liu et al. (2018) proposed an ensemble IDS that combined a decision-tree-based IDS and a random-forest-based IDS, achieving an accuracy of 99.5% and an F-score of 0.995.

Despite the progress in IDS research, challenges still need to be addressed. For instance, the lack of labeled data is a major challenge in IDS research. Collecting and labeling large amounts of data is time-consuming and costly, making it difficult to develop and evaluate IDS. Moreover, IDS are prone to false positives and false negatives, which can affect the performance of the system.