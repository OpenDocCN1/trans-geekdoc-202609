
- **Complexity in Interpretation:** It can be challenging to interpret why a model flagged a particular activity as anomalous, making it harder for security analysts to understand and respond effectively.
- **Computational Resources:** Some unsupervised algorithms, particularly clustering and neural network-based methods, can be computationally intensive, especially when analyzing large volumes of network data in real time.

## 2.6.1 Techniques and Algorithms

The following are the different Unsupervised Learning Algorithms, summary of all these algorithms are given in Table 2.4.

**Clustering Algorithms:**

- **K-means Clustering:** A popular algorithm for partitioning data into K distinct clusters based on feature similarity. In IDS, K-means can group network traffic into typical patterns, with points that don’t fit well into any cluster potentially indicating anomalies.
- **DBSCAN (Density-Based Spatial Clustering of Applications with Noise):** Useful for finding clusters of arbitrary shape, DBSCAN labels points in high-density regions as clusters, and points in low-density regions as noise, which can indicate anomalies.
- **Hierarchical Clustering:** Builds a hierarchy of clusters, which can help in detecting different levels of granularity in patterns, identifying not only isolated outliers but also anomalous subclusters within normal traffic patterns.

**Anomaly Detection Algorithms:**

- **Isolation Forests:** This algorithm isolates anomalies by building a series of random binary trees. Data points that require fewer splits to isolate are flagged as potential anomalies. Isolation Forests are efficient and effective for large datasets, making them well-suited for real-time IDS applications.

Table 2.4 Summary of unsupervised learning algorithms.

| Aspect | Clustering algorithms | Anomaly detection | Density-based anomaly detection |
|---|---|---|---|
| Objective | Group similar data points | Identify outliers | Detect outliers based on density |
| Primary output | Clusters | Anomaly labels | Anomaly labels based on density |
| Key metric | Similarity/ Dissimilarity | Deviation from norm | Local density |
| Dependency | Entire dataset's structure | Normal vs abnormal labels | Local neighborhood density |
| Algorithm examples | K-Means, DBSCAN | Isolation Forest, PCA | LOF, DBSCAN |

- **Principal Component Analysis (PCA)**: PCA reduces data dimensionality by identifying principal components, or directions of maximum variance. In IDS, PCA can reveal patterns in high-dimensional data and detect anomalies by identifying data points that fall outside the typical variance.
- **Autoencoders**: A type of neural network used for anomaly detection. Autoencoders are trained to compress and then reconstruct input data. Data that cannot be reconstructed well is considered anomalous. In IDS, autoencoders are effective for recognizing complex, high-dimensional anomalies, such as unusual packet headers or payload structures.

### Density-Based Anomaly Detection:

- **Local Outlier Factor (LOF)**: Measures the local density of a data point relative to its neighbors. Points with substantially lower density than surrounding points are considered anomalies, ideal for detecting unusual network traffic patterns that might indicate an intrusion.

## 2.6.2 Example Use Case: Anomaly-Based Network Intrusion Detection

Consider an organization with a network environment where patterns of data transmission, user behavior, and system access vary widely. An unsupervised anomaly detection model, such as an Isolation Forest or autoencoder, could be trained on typical network behavior over time [20]. The model would recognize the “normal” patterns and could flag any significant deviations—such as unusual IP connections, unexpected data transmission volumes, or access from unusual geographic locations—as potential intrusions.

For instance, if an employee’s account suddenly starts downloading large volumes of data during off-hours, an unsupervised learning model trained on typical behavior could detect this anomaly and alert security teams to a potential insider threat or account compromise [21].

## 2.7 Semi-Supervised Learning in Intrusion Detection Systems (IDSs)

Semi-supervised learning combines the strengths of both supervised and unsupervised learning by using a mix of labeled and unlabeled data. This approach is particularly valuable in IDSs where labeled attack data is often limited, but large amounts of unlabeled network data are readily available [22]. Semi-supervised learning leverages the small labeled dataset to help the model better understand and categorize the larger pool of unlabeled data, thus improving detection accuracy and adaptability.

### Key Concepts of Semi-Supervised Learning in IDSs:

- **1) Label Propagation:** Semi-supervised learning models rely on label propagation to spread the information from the labeled data to the unlabeled data. In the IDS, this process allows the model to extend the characteristics of known attack patterns to similar, yet unlabeled, data points, helping detect potential threats in unlabeled data.
- **2) Anomaly Detection with Limited Labels:** Semi-supervised learning is particularly useful in anomaly detection within the IDS, where labeling data for every potential intrusion scenario is infeasible. By using a small set of labeled data, the model can detect patterns that deviate from normal behavior, even if it hasn’t seen a specific attack label.
- **3) Self-Training and Iterative Learning:** A semi-supervised IDS can use self-training methods, where the model iteratively labels its own predictions on unlabeled data and refines its accuracy over time. This iterative approach helps improve the model’s performance and adaptability, especially in dynamic environments where attack patterns evolve.

### Common Semi-Supervised Learning Techniques in IDSs:

- **1) Self-Training:** In self-training, the model is initially trained on a small labeled dataset. It then labels the unlabeled data points with high-confidence predictions and iteratively incorporates these newly labeled points into the training set. Over time, the model “learns” from both the labeled and the self-labeled data, improving its detection capabilities.
- **2) Co-Training:** Co-training involves training two or more models on different feature sets (or views) of the data. Each model labels the unlabeled data it finds with high confidence, and these labels are used to train the other models. In IDS, co-training could be applied by using one model to analyze network features (e.g., packet size and IP addresses) and another to analyze behavioral features (e.g., access patterns), allowing the system to detect complex attacks from different perspectives.
- **3) Graph-Based Approaches:** In a graph-based approach, data points are represented as nodes in a graph, with edges indicating similarity or proximity. Labels from known points (e.g., malicious or benign) are propagated through the graph based on connections, allowing the model to infer labels for unlabeled points. In IDSs, graph-based methods are useful for analyzing network traffic flows, where similar traffic behaviors are likely connected.
- **4) Generative Models:** Models like generative adversarial networks (GANs) and variational autoencoders (VAEs) can create synthetic examples of both normal and anomalous data based on a small labeled set. By generating new examples, these models help semi-supervised IDSs learn complex patterns and anomalies, aiding in more robust detection even with limited labels.

### Benefits of Semi-Supervised Learning in IDS:

- **Efficient Use of Labeled Data:** Semi-supervised learning maximizes the utility of small labeled datasets, helping the IDS perform well even when labels are sparse or difficult to obtain.
- **Improved Detection of Unknown Threats:** With a mix of labeled and unlabeled data, semi-supervised models can learn to identify both known and previously unknown types of intrusions.
- **Reduced Dependence on Labeling:** Reducing the need for exhaustive labeling saves time and resources, especially in environments where labeled attack data is difficult to gather.

### Challenges of Semi-Supervised Learning in IDSs:

- **Error Propagation:** If the model incorrectly labels data during the self-labeling process, these errors can propagate through the model, potentially leading to incorrect classifications and a higher rate of false positives or negatives.
- **Complexity of Model Training:** Semi-supervised learning can be computationally intensive, especially with iterative self-labeling or co-training techniques, making it challenging to implement in real-time IDSs.
- **Interpretability:** As with other ML techniques, understanding why the model flagged certain data points as malicious or benign can be challenging, especially in complex models using deep learning or generative approaches.

### 2.7.1 Semi-Supervised Algorithms and Applications

The following are the different Semi-Supervised Learning Algorithms, summary of all these algorithms are given in Table 2.5.

**1) Self-Training:**

- **Method:**
  - Train an initial classifier on the labeled data.
  - Predict labels for the unlabeled data.
  - Add the most confident predictions to the labeled set.
  - Retrain the model iteratively.
- **Use in IDS:** Detect anomalies by iteratively refining the classification boundaries for network traffic data.
- **Challenges:** Risk of propagating incorrect labels in early iterations.
