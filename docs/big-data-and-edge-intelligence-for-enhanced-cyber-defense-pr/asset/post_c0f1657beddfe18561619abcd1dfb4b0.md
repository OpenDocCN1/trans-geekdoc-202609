 # Big Data and Edge Intelligence for Enhanced Cyber Defense

instances, achieving a 93.95% accuracy in detecting DoS attacks by BPNNs [33]. Another approach employs a binary and multi-class neuro-fuzzy inference systems (NFIS), achieving detection rates from 89.43% to 91.14% and a minuscule false rate [35]. Decision trees are widely employed for their efficiency in time complexity and high detection accuracy [36, 37]. For instance, a Snort-based IDS using decision tree classification successfully identifies threats with 99% accuracy by estimating Snort priorities [37]. Hybrid approaches have also been introduced, as a multi-layer hybrid IDS C4.5-based decision tree classification with a multilayer perceptron (MCP) classifier, demonstrating an impressive 99.50% detection rate and a low false rate of 0.03% [38]. NeuroC4.5, a decision tree based on a neural network, achieved 94.55% detection rate for DoS attacks [39]. Recursive feature attention (RFA) feature selection contributes to improved detection performance in a model developed by Hamed et al. [40]. Furthermore, Sidique et al. present a parallel machine learning technique using XGBoost for big-speed data networks, achieving a remarkable 99.60% detection rate and an accuracy of 99.65% with a minimal false rate [41]. Hidden Markov models (HMMs) have been applied but struggle with modeling long-range dependencies between annotations [30, 42]. Other rule-based mechanisms and supervised models, including logistic regression, deep belief, and k-nearest neighbor models, have also made contributions, each with its own set of advantages and limitations, tailored to specific domains and constraints [43, 44].

## 6.3 PROPOSED METHODOLOGY

The methodology proposed here has a two-stage detection mechanism. At the first stage the data is sent for pre-processing, and during the detection stage threats are detected across their signatures. The block diagram of the detection mechanism has been given in Figure 6.1.

### 6.3.1 DATA Pre-PROCESSING

In the data preparation phase for training and testing the IDS, we utilized the CICIDS2017 [45, 46] dataset provided by the Canadian Institute for Cybersecurity. This dataset is particularly valuable as it contains both the most and prevalent cyberattack data, However, due to its substantial size, with 2,830,743 instances and 85 features, it posed a potential bottleneck for the IDS. To address this challenge, we decided to select a more manageable number of features while maintaining a reasonable size for training and testing. Prior to feature selection and sampling, a critical step involved removing duplicate instances from the dataset to prevent any bias in the sample selection process. We accomplished this by employing Weka's unsupervised RemoveDuplicates filter. Once the remaining unique instances were then subjected to feature selection and subsequent sampling procedures.

![](img/aeaf5e4a1e1020ca53a1da35e316de95_145_0.png)

**FIGURE 6.1** The proposed IDS for detecting threats.

### 6.3.1.1 Infinite Feature Selection (IFS)

In the field of intrusion detection, the infinite feature selection (IFS) [47] algorithm offers a powerful approach to feature selection. Unlike other feature selection methods, IFS operates in two distinct steps. Initially, it independently ranks every feature within the dataset, an unsupervised evaluation of their relevance. Then, it employs a robust cross-validation strategy to select the top-performing m features. What sets IFS apart from its counterparts is its inclusive nature—every feature contributes to the assessment of each feature’s weight. This methodology is implemented by constructing an affinity graph from the entire feature set, wherein the relationship between features is represented as a path connecting them. By considering the collective influence of all features, IFS enhances the accuracy and efficiency of IDSs, ultimately enabling them to identify and mitigate potential threats with greater precision and effectiveness.

### 6.3.1.2 Generating Training and Test Data

After the requisite features were carefully chosen, the process of extracting training and testing data from the dataset connected. To ensure an impartial evaluation of threat detection accuracy, a deliberate approach was taken in which the intersection of the training set (T₁) and the testing set (T₂) was intentionally null (T₁ ∩ T₂ = ∅). This was achieved through the implementation of two distinct filter-based techniques: Reservoir sampling and SRF, both employed for random selection of training and testing data. Notably, Reservoir sampling stands out for its equitable probability of being included in the reservoir for each instance from the data stream. This mechanism proves particularly advantageous for handling extensive datasets, where memory constraints make loading the entire dataset impractical. This choice was motivated by the need for efficient training sample generation. Consequently, the randomly generated data using Reservoir sampling possessed the following distinctive

Similarly, test data has been generated as 10 different sets with similar number of instances with random attack ratio. Test instances are generated homely using SRF filter available in Weka. The dataset excluding the training instances is subjected to this filter for generating test cases. The test cases contain similar number of instances with varying class balances. This creates an unbiased environment for evaluating our IDS. A sum total of 3586 instances for test data have been considered with 10 equal partitions for test cases.

#### TABLE 6.1 Characteristics of Training Dataset Generated by Reservoir Sampling

| Characteristics | Description |
|---|---|
| Dataset name | CICIDS2017 |
| Type of class | Multi Class |
| Number of training instances generated | 7166 |
| Number of distinct classes | 15 |
| Minority Class | Class label | BENIGN |
| | Instances | 1658 |
| | % of total instances | 23.13% |
| Majority Class | Class label | HEARTBLEED |
| | Instances | 7 |
| | % of total instances | 0.09% |

## 6.3.2 TRAINING THE IDS MODEL

The IDS model is fortified by the CTC algorithm, as proposed by Ibarguren et al. [11]. CTC contracts an innovative resampling approach [12], which leverages the concept of "coverage." Coverage represents the minimum percentage of instances from any class within the training sample that should be present in the subsample with a different class distribution. This approach employs a dynamic strategy for determining the optimal number of samples. This determination is based on various criteria, including the class distribution of the dataset, the type of subsample being used, and the desired coverage value. Unlike traditional methods that rely on a fixed quantity of subsamples, the chosen parameters. Notably, in situations where significant class imbalances exist in the training data, more subsamples are generated to maintain consistent coverage. The distinctive characteristic of this method renders it very suitable for our IDS scenario, guaranteeing resilient performance when confronted with significant class imbalance in the training data.

## 6.4 RESULTS AND DISCUSSION

The IDS engine is validated using 10 test cases. The outcome of the evaluation is recorded and presented through Table 6.2–11 and from Figure 6.2–61. Table 6.2–11 represent the attack-wise performance outcomes of the detector for test case 1 to case 10. Similarly, Figures 6.4, 6.7, 6.10, 6.13, 6.16, 6.19, 6.22, 6.28, and 6.31 represent confusion matrix generated by the detector for test case 1 to case 10, respectively. Further the actual vs. predicted threads along with their prediction margin also have been visualized through appropriate figures.

#### TABLE 6.2 Attacks Wise Performance of Detector for Test Case #1

| Attack Groups/Benign | Attacks/Benign | TPR | FPR | PPV | ROC |
|---|---|---|---|---|---|
| BENIGN | BENIGN | 0.94 | 0 | 0 | 1 |
| PATOR | SSH | 1 | 0.003 | 0.947 | 0.999 |
| | FTP | 1 | 0.003 | 0.958 | 0.999 |
| HEARTBLEED | HEARTBLEED | 0 | 0 | 0 | 1 |
| DOS | SLOWLORIS | 0.941 | 0 | 1 | 0.971 |
| | SLOWHTPTTEST | 1 | 0 | 0 | 1 |
| | HULK | 1 | 0.003 | 0.981 | 0.999 |
| | GOLDENEYE | 1 | 0.006 | 0.939 | 0.998 |
| INFILTRATION | INFILTRATE | 1 | 0 | 0 | 1 |
| WEB ATTACK | BRUTE FORCE | 1 | 0.006 | 0.846 | 1 |
| | XSS | 1 | 0.003 | 0.9 | 1 |
| | SQL IN | 0 | 0 | 0 | 0.5 |
| PORTSCAN | PORTSCAN | 0.955 | 0 | 1 | 0.995 |
| DDOS | DDOS | 1 | 0 | 1 | 1 |
| BOT | BOT | 1 | 0.003 | 0.929 | 1 |
