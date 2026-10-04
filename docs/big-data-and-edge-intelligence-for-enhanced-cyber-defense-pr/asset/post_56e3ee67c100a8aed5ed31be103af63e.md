
# Enhancing Intrusion Detection in IoT-Based Vulnerable Environments

## 5.5.2 DATA PREPROCESSING AND FEATURE ENGINEERING

The preprocessing steps applied to the collected IoT data to ensure its quality and suitability for intrusion detection. We discuss data cleaning techniques, outlier detection, and data normalization to remove noise and inconsistencies. Feature engineering methodologies are also elaborated, where we transform raw data into informative features that can enhance the performance of the intrusion detection model. Moreover, we explore techniques to reduce data dimensionality and address the heterogeneity of data from different IoT devices. This includes feature selection methods and data transformation approaches tailored to the federated learning setup.

## 5.5.3 DATA PARTITIONING FOR FEDERATED LEARNING

In this section, we describe how the processed IoT data is partitioned into subsets for the federated learning process. We consider the privacy implications and communication constraints of IoT devices when partitioning data. The data partitioning approach ensures that sensitive data remains local to each device during the model training.

We discuss strategies for ensuring a balanced and representative distribution of data among the IoT devices while maintaining diversity and covering intrusion scenarios. Furthermore, we address how data partitioning affects the model's generalization and its implications on the overall intrusion detection performance.

## 5.5.4 DATASET: EDGE-IIOTSET

The “Edge-IIoT” dataset serves as a crucial element in the research, offering a realistic and comprehensive representation of network traffic in IoT-based vulnerable environments. This dataset is tailored to capture the intricacies of Industrial IoT (IIoT) systems and their vulnerabilities, enabling effective evaluation of intrusion detection techniques.

### Key Characteristics of Edge-IIoTset

- Realistic Scenarios: The dataset comprises network traffic collected from diverse IoT devices within industrial environments, closely resembling real-world setups.
- Diverse Behaviors: It encompasses a wide range of behaviors, including both normal and malicious activities. This diversity enables the exploration of various attack vectors and vulnerabilities.
- Labeled Instances: Each instance in the dataset is meticulously labeled to indicate the nature of behavior, whether it’s a normal operation, a specific attack type, or a vulnerability.
- Raw and Processed Data: The dataset includes both raw packet-level data and pre-processed features, facilitating flexibility in experimentation and analysis.

# 110 Big Data and Edge Intelligence for Enhanced Cyber Defense

# Data Pre-Processing

### 1. Data Collection and Raw Dataset:
Raw data is collected by monitoring network traffic within an industrial IoT environment. This involves capturing network packets, which contain information about source and destination IP addresses, port numbers, protocols, and payload data.

### 2. Data Cleaning and Formatting:
- Raw data contains noise, missing values, and redundant information.
- Removing duplicate packets and records to ensure data integrity.
- Handling missing values through methods like imputation or removing instances with incomplete information.
- Standardizing data formats to eliminate inconsistencies.

### 3. Feature Extraction:
Feature extraction transforms raw packet data into a format suitable for machine learning algorithms. It involves the following:
- Calculating statistical features such as mean, median, standard deviation of packet sizes, and inter-arrival times.
- Extracting timing-based features, including timestamps and session durations.
- Generating frequency-based features like packet counts, protocol distribution, and port utilization.

### 4. Data Labeling:
Each instance is labeled to identify its category, such as normal behavior, specific attack type (e.g., Distributed Denial of Service, Man in the Middle [MITM]), or vulnerability (e.g., weak password). Proper labeling is essential for supervised learning.

# Feature Selection

### 1. Dimensionality Reduction:
High-dimensional feature spaces can lead to computational inefficiencies and overfitting. Techniques like principal component analysis (PCA) or t-distributed stochastic neighbor embedding (t-SNE) are applied to reduce dimensionality while preserving meaningful information.

### 2. Feature Importance:
Random forest (RF), gradient boosting, or similar models are used to assess feature importance. This helps identify which features contribute the most to the model's predictive power.

### 3. Correlation Analysis:
Features with high correlation might introduce redundancy. Correlation analysis identifies and eliminates redundant features, enhancing model efficiency.

### 4. Domain Expertise Integration:
Domain experts review the selected features to ensure they align with the characteristics of IoT-based vulnerable environments. This step ensures that the chosen features make sense from a practical perspective.

# Enhancing Intrusion Detection in IoT-Based Vulnerable Environments

By leveraging the “Edge-IIoTset” dataset, performing comprehensive pre-processing, and employing effective feature selection strategies, the research aims to enhance intrusion detection capabilities using federated learning in IoT-based vulnerable environments. The dataset’s richness, combined with meticulous pre-processing and feature selection, contributes to the accuracy and robustness of the intrusion detection framework.

## 5.6 EVALUATION METRICS AND METHODOLOGY

### 5.6.1 PERFORMANCE METRICS FOR INTRUSION DETECTION

In this subsection, we introduce the performance metrics used to evaluate the effectiveness of our intrusion detection model. These metrics include true positive rate (TPR), FPR, accuracy, precision, recall, F1-score, and area under the receiver operating characteristic curve (AUC-ROC). We explain the significance of each metric in assessing the model’s ability to detect intrusions accurately and efficiently.

## 5.6.2 DESCRIPTION OF THE EVALUATION METHODOLOGY

Here, we provide an overview of the evaluation methodology to assess the performance of our FL-ID system. We explain the setup of experiments, including the number of participating IoT devices, the duration of the federated learning process, and the communication frequency between devices and the central server.

We discuss the metrics collected during each federated learning round and the stopping criteria to determine convergence. We also address any potential biases or limitations in the evaluation process and propose strategies to mitigate them.

## 5.6.3 BASELINE MODELS FOR COMPARISON

In this subsection, we introduce the baseline models used for performance comparison with our FL-ID system. The baseline models may include traditional machine learning algorithms like support vector machines (SVMs), decision trees (DTs), or ensemble methods like RF.

We explain the rationale behind choosing these baseline models and how they represent the performance benchmark for our federated learning model. The evaluation results of these baseline models will help us understand the effectiveness and advantages of our proposed approach.

By outlining the dataset collection, preprocessing steps, and partitioning strategies, along with the evaluation metrics, methodology, and baseline models, we ensure a rigorous evaluation of our intrusion detection system and provide insights into the model’s performance and capabilities in the IoT-based vulnerable environment.

# 112 Big Data and Edge Intelligence for Enhanced Cyber Defense

## 5.7 EXPERIMENTAL RESULTS

### 5.7.1 PRESENTATION OF EXPERIMENTAL SETUP AND HARDWARE CONFIGURATION

In this section, we provide a detailed presentation of the experimental setup used to evaluate the performance of our intrusion detection system based on federated learning. We describe the hardware configuration of the central server and the participating IoT devices, including their processing capabilities, memory, and communication interfaces. Additionally, we outline the software environment, including the operating systems, libraries, and frameworks, used to implement the federated learning model and the baseline detection models for comparison. The communication protocols and data exchange mechanisms between the central server and IoT devices are also discussed.

Furthermore, we present the data collection process, specifying the duration and frequency of data updates from the IoT devices to the central server during the federated learning rounds. We ensure transparency in the experimental setup to facilitate reproducibility and to enable other researchers to validate our findings.

### 5.7.2 PERFORMANCE COMPARISON OF FEDERATED LEARNING WITH TRADITIONAL APPROACHES

For a comprehensive performance comparison, let's compare the FL-ID system with five traditional approaches commonly used in centralized intrusion detection systems:

- SVMs
- DTs
- RF
- Naive Bayes (NB)
- k-nearest neighbors (k-NN)

# Results

Experiments conducted on a dataset from an industrial IoT environment. The dataset contains sensor readings from different machines and devices within the industrial setup. The labeled dataset contains instances of normal operation and instances where anomalies or intrusions occurred.

We divide the dataset into a training set and a test set. Then, we train each model using the training set and evaluate their performance on the test set using various metrics.

# Performance Metrics

We evaluate the models using the following performance metrics, and comparison results are shown in Table 5.1.

Accuracy: The percentage of correctly classified instances out of all instances in the test set.
