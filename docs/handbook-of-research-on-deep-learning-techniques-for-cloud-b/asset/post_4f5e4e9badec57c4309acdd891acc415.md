
## Table 1. Continued

| Author, Title, and Year of the Paper | Dataset Details | Machine Learning Model Used |
|---|---|---|
| Zeeshan M., et al., “Protocol-Based Deep Intrusion Detection for DoS and DDoS Attacks Using UNSW-NB15 and Bot-IoT Data-Sets”,2022 (Zeeshan et al., 2022) | The UNSW-NB15 and Bot-IoT dataset uses Protocol Based Deep Intrusion Detection (PB-DID) architecture to distinguish between anomalous and non-anomalous activity. | Deep Learning Techniques |
| Ullah, I., Mahmoud, Q., “Design and Development of a Deep Learning-Based Model for Anomaly Detection in IoT Networks”, 2021 (Ullah & Mahmoud, 2021) | The binary and multi-classification attacks are assessed using various performance indicators using the BoT-IoT, MQTT-IoT-IDS2020, and IoT-23 dataset. | Convolutional Neural Network. |
| Muhammad Shafiq et al., “CorrAUC: Malicious Bot-IoT Traffic Detection Method in IoT Network Using Machine-Learning Techniques”,2021 (Shafiq et al., 2021) | Based on feature selection, a novel framework model called CorrAUC on the Bot-IoT dataset is suggested to validate the identification of harmful traffic in the IoT network. | Decision Tree, Naive Bayes, Random Forest, Support Vector Machine. |
| Muhammad Shafiq, Zhihong Tian, et al., “IoT Malicious Traffic Identification Using Wrapper-Based Feature Selection Mechanisms”, 2020 (Shafiq et al., 2020) | For the BoT-IoT dataset one of the dimensional reduction method is created, by utilizing the wrapper technique to assess the performance metrics of harmful assaults. | Supervised Learning Methods. |

5. Reconnaissance: It is a technique for learning more about a network host. Another name for it is a probe. Attacks known as probing attacks include scanning distant nodes for details about the host.

These are the numerous cyber security assaults that may be examined using various machine learning techniques, which are essentially split into supervised and unsupervised techniques. We will discuss more machine learning methods and also a detailed description of the dataset used in our proposed work, in section III and followed by section IV, the feature extraction, data pre-processing, analysis of the test result, etc., of the proposed framework and finally in section V and VI will analyze and conclude the best-fit model for the data used.

## METHODS

### Dataset Description

The BoT-IoT dataset is used to create the NF-BoT-IoT, an IoT NetFlow-based dataset. The flows were tagged with the related cyber-attacks, and the features were taken from publicly accessible pcap files or CSV files (Sarhan et al., 2022). There are 600,100 data flows in total, of which 13,859 are benign and 586,241 represent samples of various cyberattacks. The collection contains information about four separate cyberattacks. Table 2 and Figure 1 represent the NF-BoT-IoT, cyber-attack details.

- 4. **Decision Tree (DT):** A collection of questions is addressed by the DT machine learning model, which arranges data into a tree-like structure. The DT model can automatically remove features that are redundant or unnecessary. The learning process includes feature selection, tree generation, and tree trimming (F., 2018). a) Each node addresses a test point at the feature level and alludes to a single variable or feature; b) Branches that deal with the test result are connected to lines that ultimately lead to c) Leaf Nodes, which address the class labels (Ge et al., 2019). The method selects the top characteristics one by one and creates child nodes from the root node while training a DT model (F., 2018). The DT is a fundamental classifier that supports both continuous and categorical input. With the DT approach, it is possible to quickly find all triggering rules (i.e., rules that match an input element) with a small number of comparisons in an intrusion detection process (Kumar et al., 2012; Journal & Science, 2021).

### Deep Learning Algorithms

It is a computing system that draws inspiration from the information processing and distributed communication nodes in the human brain. It is a technology that enables the computer to classify additional examples of data after learning from a small number of data instances (Idrissi et al., 2022b). Through a series of nonlinear transformations, deep learning is well known for finding outstanding variables in raw data, with each change achieving an increased degree of depth and complexity (Dina et al., 2023). Keras Model, CNN, RNN, LSTM, and GRU, among others, are deep learning models (Idrissi et al., 2022a).

- 1. **Auto-Encoder (AE):** It is the sort of unsupervised learning algorithm made to take an input and change it into another representation. To reduce dimensionality, it only requires reduced version of the data and reconstructs the original message from that. It is used to solve a variety of issues, such as facial recognition, feature detection, anomaly detection, etc. (Boumerdassi et al., 2022).

- 2. **Artificial Neural Networks (ANN):** It is a kind of nonlinear statistical model that shows an intricate connection between inputs and outputs to identify novel patterns. ANNs learn from sample datasets and are used to enhance current data analysis techniques because of their strong predictive skills. It is a very efficient data-driven modeling tool for identification and dynamic modeling since it offers flexible structure and universal approximation capabilities.

- 3. **Convolutional Neural Networks (CNN):** A type of deep neural network that can be used for a variety of applications. Convolution and pooling layers, rather than fully connected hidden layers, are used in this sort of neural network. In contrast to other machine learning algorithms, CNN can classify the traffic on its own and learn better attributes (Idrissi et al., 2021, 2022a).

Because CNN uses the same convolution matrix (mask), a sizable reduction in the number of parameters and training computation summation is feasible while still learning more features with more traffic data (Sarhan et al., 2022).

- 4. **Long Short-Term Memory (LSTM):** It is the sequential data that comprehend both the network’s present and past activity (Ge et al., 2019). Due to the fact that the attackers carry out the attack as a series of continuing actions, it is essential to examine both the most recent and earlier traffic. Including the input, output, and forget gates within the RNN model, (Farhan & Jasim, 2022) aids in resolving the issue of long-term dependency and is therefore regarded as an RNN development (Ullah & Mahmoud, 2021).

## PROPOSED FRAMEWORK

Our proposed method has undergone five essential steps, such as Feature extraction, data pre-processing, feature selection, splitting into training and testing data, and implementation of machine learning methods (refer to Figure 2).

- 1. **Feature Extraction:** The dataset is collected from the website https://staff.itee.uq.edu.au/marius/NIDS_datasets/. It consists of NIDS datasets in CSV file format (Leevy et al., 2022). This data is used to identify the normal and the malicious attack and also the category of the attacks. The collected data size is 600,100*14(rows*columns) which includes dependent features and the target variables Label and Attack. With the extraction of fresh dataset characteristics, this technique was primarily intended to enhance model performance (Leevy et al., 2022) (Refer to Table 3).

- 2. **Data Pre-Processing:** Pre-processing data transformation techniques are used to change the dataset’s structure into one that is appropriate for machine learning. Also, the dataset must be cleaned to make it more effective by removing any irrelevant or damaged data that can impair the dataset’s accuracy.

Categorical categories in the dataset are given usual and nominal values, and numerical data are given discrete and continuous values. The data must then be categorized into vectors, which can be done in many different methods. One hot encoding and label encoding (Agarap, 2018) are two often employed methods. In this work, the data is converted into a feature vector using label encoding techniques. The majority of the attributes in the dataset have both several unique values and nominal category values. In the dataset, the label encoding method is employed to convert values into a vector.

- 3. **Feature Selection:** Feature selection increases data clarity while reducing computational effort (i.e., training time) (i.e., facilitates visual detection of patterns). In certain situations, feature selection can improve classification performance and lessen the effects of class imbalance (Liu & Lang, 2019).

Reducing the quantity of features and using only those needed to create and test the algorithms is crucial if we are to find a straightforward security solution for the data (Agarwal et al., 2021).

- 4. **Splitting Into Training and Testing Data:** In addition to the data needed for machine learning, it has to be trained and tested, for the Model’s performance and efficiency of it. The training data comprised 80% of the NF-BoT-IoT dataset, whereas the testing data included 20%.
