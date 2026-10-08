
## 174 Multi-Criteria Decision-Making with Machine Learning

### 13.4.1.2 Ensemble Methods and Predictive Analytics

Ensemble techniques like bagging and boosting multiple models to improve prediction accuracy. In MCDM, ensembles can provide more robust evaluations of alternatives by aggregating predictions from multiple models. This can lead to more reliable rankings and decisions by mitigating the bias of individual models. Supervised learning can be used for predictive analytics, where historical data is used to make predictions about future outcomes (Dutta et al., 2023). For instance, supervised learning models in health care management can predict patient readmission rates based on medical and demographic factors, aiding in resource allocation and treatment planning.

### 13.4.1.3 Weight Assignment and Preference Modeling

Supervised learning can assist in assigning weights to criteria based on historical or expert knowledge. By analyzing past decisions and their outcomes, these models can provide insights into how different criteria have influenced previous decisions. This helps in reducing subjectivity in the weight assignment process. Supervised learning can capture decision-maker preferences learning from past choices. This allows the model to predict which alternatives a decision-maker will likely prefer, considering their preferences' historical data. Preference modeling can be valuable when dealing with decision-makers who have made similar choices in the past (Henrique Alves Ribeiro & Reynoso-Meza, 2023).

## 13.4.2 UNSERVISED LEARNING

Unsupervised learning in MCDM is employed to uncover hidden patterns, group similar alternatives, or reduce the dimensionality of data without the need for labeled training examples. The following are some common unsupervised learning techniques and their applications in MCDM.

### 13.4.2.1 Clustering Algorithms and Dimensionality Reduction

Clustering techniques like k-means, hierarchical clustering, and density-based spatial clustering of alternatives with noise (DBSCAN) group similar alternatives based on shared characteristics. In MCDM, clustering can help segment alternatives with similar performance across multiple criteria, aiding decision-makers in identifying distinct categories of alternatives. Dimensionality reduction techniques, for example, t-SNE and principal component analysis, are used to reduce the number of variables while preserving important information (Shakaibi et al., 2023). In MCDM, these techniques can be employed to handle high-dimensional data with many criteria by transforming it into a lower-dimensional space.

### 13.4.2.2 Self-Organizing Maps, Association Rule Mining, and Anomaly Detection

Self-organizing mapping is a neural network-based technique that maps high-dimensional data onto a lower-dimensional grid. In MCDM, SOM can help visualize and understand relationships between criteria and alternatives, assisting decision-makers in identifying clusters or patterns within the data. Association rule mining discovers patterns in large data sets by identifying frequent item sets and their associations. In MCDM, this technique can uncover relationships between criteria and alternatives that might not be apparent through manual analysis, aiding in understanding decision factors. Anomaly detection identifies that that deviate significantly from the norm (Rashidi Shikhoury et al., 2023). In MCDM, these techniques can be applied to outliers or unusual alternatives requiring special consideration due to their extreme behavior across criteria.

### 13.4.2.3 Exploratory Data Analysis and Pattern Recognition

Exploratory data analysis (EDA) involve visualizing and summarizing data to uncover trends and relationships. In MCDM, it can help decision-makers gain initial insights into the distribution and interactions of criteria, guiding further analysis and decision processes (Agarwal et al., 2023). Unsupervised learning techniques can identify patterns in data that might not be immediately apparent and provide valuable tools for exploring and understanding the structure and relationships within MCDM data (Jari et al., 2023). By revealing patterns and grouping similar alternatives, these techniques contribute to more informed decision-making by helping decision-makers identify clusters, outliers, and trends that might impact their choices.

## 13.4.3 REINFORCEMENT LEARNING

Reinforcement learning (RL) can be applied to MCDM scenarios where decisions are made in sequential steps to maximize cumulative rewards. Here are some RL techniques and their applications in MCDM.

### 13.4.3.1 Dynamic Programming and Markov Decision Processes

Dynamic programming algorithms, such as the Bellman equation and policy iteration, solve decision problems involving sequential. In MCDM, dynamic programming can be applied to scenarios where decisions at each step affect future outcomes, such as resource allocation over time. Markov decision process model-making problems with uncertainty and rewards; they can capture the dynamic nature of decisions by considering the probabilistic outcomes of different alternatives and optimizing decisions to maximize expected rewards (Sookhall & Fonou-Boumdey, 2023).

### 13.4.3.2 Q-learning and Policy Gradient Methods

Q-learning is a popular technique that helps an agent maximize cumulative rewards. In MCDM, Q-learning can guide decisions over multiple steps, considering criteria and objectives to reach optimal or near-optimal solutions. Policy gradient methods optimize policies directly to find actions that maximize cumulative rewards (Ahmed et al., 2023). In MCDM, these methods can be applied to decision processes that involve complex interactions among criteria and alternatives, where traditional optimization methods might be challenging.

### 13.4.3.3 Monte Carlo Methods and Adaptive Learning

Monte Carlo methods such as Monte Carlo tree search different decision paths to estimate optimal strategies and can help navigate complex decision trees and explore alternative paths to find solutions that satisfy multiple criteria. RL can enable adaptive decision-making, where policies are continuously updated based on new data (Bardini & DiCarlo, 2023). In MCDM, this is useful when criteria or preferences change over time, allowing the decision process to remain relevant.

## 13.4.4 Stochastic Optimization and Sequential Decision-Making

RL can be used for stochastic optimization, where decisions are made under uncertainty. In MCDM, this can involve selecting alternatives with the highest utility or reward. RL techniques can handle sequential decision-making scenarios in MCDM, where decisions at each step affect future choices and their outcomes (Bardini & DiCarlo, 2023). By optimizing decision over time to maximize cumulative rewards, these techniques provide a framework for tracking complex decision scenarios and finding strategies that align with multiple criteria (Mba Kouhou et al., 2023).

### 13.4.5 Deep Learning

Deep learning techniques leverage neural networks with multiple layers to capture complex patterns and relationships within data. In MCDM, these techniques offer enhanced capabilities for handling intricate decision landscapes and making accurate evaluations. The following are some common deep learning techniques and their applications in MCDM.

### 13.4.5.1 Neural Networks and Convolutional Neural Networks

Neural networks can model nonlinear relationships between criteria and alternatives. In MCDM, neural networks can predict outcomes, evaluate alternatives, or in assigning criteria weights based on historical data. They can capture decision patterns that traditional methods might not easily capture. Convolutional neural networks (CNNs) are particularly effective for scenarios with grid-like structures such as images or spatial data (Rathoriya et al., 2023). In MCDM, CNNs can be applied to spatial criteria or multidimensional scenarios. For instance, they can analyze satellite images to assess the impact of different criteria on land use decisions.

### 13.4.5.2 Recurrent Neural and Long Short-Term Memory Networks

Recurrent neural networks (RNNs) are designed for sequential data, making them suitable for scenarios where the order of decisions or criteria matters. In MCDM, RNNs can model decision processes that unfold over time, such as project scheduling or resource allocation. They can consider historical decisions and criteria values.
