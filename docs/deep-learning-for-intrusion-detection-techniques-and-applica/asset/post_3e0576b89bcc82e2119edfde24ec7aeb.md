
Table 2.6 Summary table of reinforcement learning (RL) approaches in intrusion detection systems (IDSs).

| RL approach | Key idea | Strengths | Weaknesses | Applications in IDS |
|---|---|---|---|---|
| Q-Learning | It learns a Q-value function to estimate rewards for state-action pairs. | • Simple and effective for small state spaces. • Does not require a model of the environment. | • Struggles with large or continuous state spaces. • Slow convergence. | • Basic anomaly detection. • Optimizing response actions. |
| Deep Q-Networks (DQN) | Combines Q-Learning with deep neural networks to handle high-dimensional states. | • Handles large, complex state spaces. • Effective for dynamic environments. | • High computational cost. • Requires careful tuning. | • Network traffic anomaly detection. • Threat response in complex systems. |
| SARSA | Similar to Q-Learning but updates Q-values based on the action actually taken. | • Policy-aware learning. • More stable than Q-Learning in some cases. | • May converge to suboptimal policies. • Less exploration compared to Q-Learning. | • Real-time threat mitigation. • Refining intrusion response strategies. |
| Policy gradient (PG) | Directly optimizes the policy by estimating reward gradients. | • Works well in continuous action spaces. • Can handle complex policies. | • Sensitive to reward design. • Slower convergence. | • Adaptive security policies. • Learning optimal resource allocation. |
| Proximal policy optimization (PPO) | Balances exploration and exploitation using trust region constraints. | • Stable and robust. • Efficient in training complex policies. | • Computationally intensive. • Requires large datasets. | • Dynamic rule adaptation for firewalls. • Advanced malware detection. |
| Model-Based RL | Builds a model of the environment to predict outcomes of actions. | • Efficient learning with fewer interactions. • Useful for planning. | • Requires accurate environment modeling. • Struggles with dynamic, unpredictable systems. | • Simulating attack scenarios. • Planning resource deployment. |
| Multi-agent RL (MARL) | Multiple agents collaborate or compete in a shared environment. | • Scalability for distributed systems. • Suitable for complex, multi-faceted problems. | • Complex coordination. • High computational cost. | • Collaborative threat detection. • Coordinated responses across network nodes. |

## 2.9 Feature Engineering, Model Training, and Hyperparameter Tuning in IDS

### 2.9.1 Feature Engineering in IDS

**Feature engineering** is the process of selecting, transforming, and creating new data attributes to enhance model performance [26]. Feature engineering involves transforming raw data into meaningful features suitable for training ML models. In IDSs, effective feature engineering is crucial to accurately capture network behaviors and differentiate between normal and malicious activities.

### Key Techniques in Feature Engineering:

- 1) **Feature Creation:**
  - **Combining Features:** Creating new features by combining existing ones (e.g., calculating age from birth date and current date).
  - **Discretization:** Converting continuous numerical features into discrete categories (e.g., dividing age into ranges like “young,” “middle-aged,” and “old”).
  - **Interaction Features:** Creating features that capture the interaction between two or more existing features (e.g., multiplying “income” and “education level”).
- 2) **Feature Transformation:**
  - **Normalization:** Scaling numerical features to a common range (e.g., 0–1 or −1 to 1).
  - **Standardization:** Rescaling features to have a mean of 0 and a standard deviation of 1.
  - **Log Transformation:** Transforming skewed data to a more normal distribution.
- 3) **Feature Selection:**
  - **Filter Methods:** Selecting features based on statistical measures (e.g., correlation, chi-squared test).
  - **Wrapper Methods:** Evaluating feature subsets based on model performance (e.g., forward selection, backward elimination).
  - **Embedded Methods:** Selecting features during the model training process (e.g., L1 regularization).

### Common Features for IDSs:

- **Network-Based Features:** These include packet-level information like source and destination IP addresses, ports, packet sizes, and protocol types, which can help distinguish between normal and suspicious traffic.
- **Behavioral Features:** Features related to user behavior, such as frequency of access attempts, login times, and duration of sessions, are useful in detecting insider threats or unusual access patterns.
- **Temporal Features:** These capture time-based patterns, such as traffic volume during specific intervals, which help in identifying time-based attacks like DDoS.
- **Statistical Features:** Aggregated statistics (e.g., mean, variance) on data traffic can highlight deviations in network patterns that may signal attacks.

### Challenges in Feature Engineering:

- **High Dimensionality:** An IDS often deals with vast datasets with many features, leading to high-dimensional data that can overwhelm ML models.
- **Feature Selection:** Identifying the most informative features is difficult and often requires domain expertise, as certain features (e.g., specific protocols or header fields) may be more relevant for certain types of attacks.
- **Data Quality and Noise:** Network data can contain noise or irrelevant features that may mislead the model if not properly filtered out. For example, certain network requests may appear unusual but are legitimate.

### 2.9.2 Model Training in IDS

**Model training** involves feeding the engineered features into an ML algorithm to recognize patterns in the data. In IDS, model training can be challenging due to the nature of network traffic data and the need for accurate threat detection [27].

### Common Machine Learning Models for IDS:

- **Supervised Models:** Decision Trees, Random Forests, SVMs, and gradient boosting models are commonly used for their interpretability and high accuracy in binary and multiclass intrusion classification.
- **Unsupervised Models:** K-means clustering, Isolation Forests, and DBSCAN are often used for anomaly detection, identifying outliers in data without requiring labeled examples.
- **Deep Learning Models:** CNNs and RNNs are utilized for complex, high-dimensional data. Autoencoders are commonly used for anomaly detection by learning normal patterns and flagging deviations.

### Training Process:

- **Data Preprocessing:** Clean and normalize data to ensure consistent format and scale.
- **Splitting Data:** Divide the dataset into training and testing sets to evaluate model performance.
- **Model Training:** Train the chosen model on the training set using optimization algorithms like gradient descent.
- **Model Evaluation:** Assess the model's performance on the testing set using metrics like accuracy, precision, recall, F1-score, and ROC curve.

### Challenges in Model Training:

- **Class Imbalance:** In IDS datasets, the majority of traffic data represents normal behavior, with only a small fraction being malicious. This imbalance can cause models to favor the majority class, missing rare but critical intrusion patterns.
- **Scalability:** Network data is generated at a high rate, requiring models capable of handling large-scale data and making real-time predictions.
- **Overfitting:** IDS models may overfit to training data, learning specific patterns that don’t generalize well to new data. This is especially problematic if the training data doesn’t include a comprehensive range of attack types.

### 2.9.3 Hyperparameter Tuning in IDSs

**Hyperparameter tuning** is the process of optimizing model parameters that control learning behavior, such as learning rates, regularization terms, and tree depths. Proper hyperparameter tuning is essential for achieving a balance between accuracy and efficiency, especially in the resource-constrained setting of real-time IDSs [28].

### Common Hyperparameters for IDS Models:

- **Learning Rate:** Determines how fast a model learns. Lower rates prevent rapid changes in weights, helping avoid overfitting in noisy data but requiring more time to converge.
- **Regularization:** Adds penalties for complexity to prevent overfitting, particularly useful in deep learning models.
- **Tree Depth and Number of Trees:** In ensemble models like Random Forests, controlling the depth and number of trees helps strike a balance between capturing sufficient patterns and avoiding excessive computational costs.
- **Cluster Size:** In clustering models, such as K-means or DBSCAN, cluster size or density thresholds affect the sensitivity of the model to anomalies.

### Challenges in Hyperparameter Tuning:

- **Computational Cost:** Hyperparameter tuning can be resource-intensive, especially with complex models and large IDS datasets. Techniques like grid search or random search require extensive computation.
