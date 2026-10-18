
Intending to improve IIoT applications, so the performance and security could achieve better results, ML and DL algorithms are being used. An example of the use of ML in IIoT environments is presented in [13], where ML algorithms are used to detect reconnaissance attacks in a water storage tank, where the treatment and distribution of water are carried out. Some of the ML algorithms used were random forest, logistic regression, and KNN; the authors even highlight the efficiency of ML models to detect attacks in real time and affirm that the test scenario provides a good understanding of the effects and consequences of attacks in real SCADA (supervisory control and data acquisition) environments.

To achieve high levels of performance using ML and DL for training models, the used datasets must be classified correctly and balanced. Real-world IIoT systems may have a significant number of attacks and intrusions [6]. However, this number is small compared to the total amount of data that is not attacked (normal data). For this reason, IIoT datasets usually present an uneven proportion of normal samples and samples under attack.

According to Melo [15], a dataset with 50% of a unique class can be already considered as an imbalanced dataset. Zolanvari et al. [16] presented a study about the problems of imbalanced datasets during the training of a model to IDSs. The training of an ML model with this kind of dataset can be turned into a big issue in the industry environment, since it can result in lots of false alarms, classifying an attack as a “normal flow” for not being able to classify it as a malicious activity due to the low number of attack samples.

Designed to meet the needs of the industry environment, an IDS must be developed with ML and DL algorithms trained with balanced and well classified datasets. Beyond that, the dataset must contain only pertinent information, so the time and computational resources spent could be minimal.

## 15.4 PRACTICAL APPLICATION OF ML ALGORITHMS IN IIOT

Several research projects about IDSs development can be found, as shown in the previous section, using different technologies. However, there is still a gap in the intrusion detection in IIoT networks, which needs a better security system, since each data manipulation or theft could result in terrible consequences. In this section, the best approach to develop an IDS for industrial environments using ML algorithms is discussed. To this end, the best features to make a satisfactory training for the IDS are analyzed, as well as several tests with prediction algorithms in order to choose the best algorithm to design the model. The dataset used in this experiment was developed by Teixeira et al., and all details about the dataset can be found in [17].

To develop our IDS, we will use two different datasets, each with a different type of cyber attack, and the goals are divided into two steps. Step 1 involves analysis and choosing the best approach, and step 2 is using the best approach.

In step 1, the Pearson correlation coefficient and the random forest are used to pick only the features with the higher scores. After feature selection, prediction tests are made with the datasets containing only the best features, using different prediction algorithms.

To implement this step, three different scenarios are used:

- 1. (RF) dataset with only the features selected with the random forest algorithm
- 2. (PC) dataset with only the features selected with the Pearson correlation coefficient
- 3. (AF) dataset with all the features

The same experiments will be made with these datasets using different prediction algorithms to find the best algorithm for this purpose.

Afterward, the datasets are balanced using the under sampling method, and the same experiments are made to analyze whether there is any impact on the training with an imbalanced dataset.

At the end of step 1, all the experiments made are evaluated to pick up the best approach, which must satisfy the following terms: balanced or imbalanced dataset according to the best performance; specific features of each cyber attack or general features as attested by the best performance on the tests; the prediction algorithm with the best rate at the evaluation.

In step 2, the best approach is put into practice using ensemble learning to develop the IDS to detect malicious activities in industrial networks. In order to implement this approach, the features are extracted – using the features selection approach from the first step – and standardized, so that the dataset can be divided into two parts: 80% of the dataset for training and 20% for testing. At the testing point, the developed IDS makes its predictions, which are finally evaluated.

To measure the performance of our approach, metrics from the confusion matrix are used, as shown in Table 15.2.

**TABLE 15.2 Confusion Matrix**

| Input |  | Classified as normal | Classified as attack |
|---|---|---|---|
|  | **Normal** | True-negative (TN) | False-positive (FP) |
|  | **Attack** | False-negative (FN) | True-positive (TP) |

The confusion matrix, illustrated in Table 15.2, can be read in the context as follows:

- *Input* represents the network flow input that will be analyzed by the model; the input value can be 0 – normal flow – or 1 – flow under attack.
- *True-negative* represents the number of normal flows correctly predicted as normal.
- *False-positive* represents the number of normal flows incorrectly predicted as under attack.
- *False-negative* represents the number of under attack flows incorrectly predicted as normal.
- *True-positive* represents the number of under attack flows correctly predicted as under attack.

The metrics from the confusion matrix used are accuracy, false alarm rate (FAR), undetected rate (UR), Matthews correlation coefficient (MCC), and sensitivity.

Accuracy is the rate of predictions made correctly considering the total number of predictions and can be represented as shown in equation (15.4.1).

FAR is the percentage of normal traffic incorrectly predicted as an attack (15.4.2).

UR is the fraction of traffic under attack incorrectly predicted as normal (15.4.3).

The MCC measures the prediction quality, presenting the correlation between the predictions and the real classification of the flow (15.4.4).

The effectiveness in predicting flows under attack correctly is measured using sensitivity (15.4.5).

### 15.4.1 Results

For the development of this practical application, two different datasets were used – available in [13] – with different cyber attacks:

- **A:** distributed denial of service (DDoS)
- **B:** reconnaissance attack

To find the best algorithm to choose the most important dataset features, two different techniques are used: the random forest algorithm and the Pearson correlation coefficient. These techniques are used in three different scenarios:

- **RF:** dataset with only the features selected with the random forest algorithm
- **PC:** dataset with only the features selected with the Pearson correlation coefficient
- **AF:** dataset with all the features

In the first scenario (**RF**), the random forest [18] was used to find the features with the best scores in the dataset **A**. As a result, the best features found were *DstBytes*, *DstLoad*, and *DstRate*, described in Table 15.3, where the description and score are shown.

**TABLE 15.3 Best Features Selected with the Random Forest Algorithm from Dataset A**

| FEATURES | SCORES | DESCRIPTION |
|---|---|---|
| Destination bytes (DstBytes) | 0.272996 | Destination/source bytes count |
| Destination load (DstLoad) | 0.182034 | Destination bits per second |
| Destination rate (DstRate) | 0.181972 | Destination packets per second |

Still in the scenario **RF**, the best features from the dataset **B** were found, with a score over 0.15: *Ploss*, *Dport*, *SrcPkts*, and *TotPkts*. The features are described in Table 15.4.

**TABLE 15.4 Best Features Selected with the Random Forest Algorithm from Dataset B**

| FEATURES | SCORES | DESCRIPTION |
|---|---|---|
| Total percent loss (Ploss) | 0.309460 | Percent packets retransmitted/dropped |
| Destination port (Dport) | 0.183496 | Destination port number |
| Source packets (SrcPkts) | 0.181972 | Source/destination packet count |
| Total packets (TotPkts) | 0.180653 | Total transaction packet count |

For the scenario **PC**, the Pearson correlation coefficient was calculated so that the features achieving the higher scores – over 0.55 – of correlations with the target – which identify the flow as 0 (normal) or 1 (under attack) – could be identified. Using the dataset **A**, the best features were: *DstLoss*, *Ploss*, *Mean*, and *SrcLoss*. The description and scores of these features are illustrated in Table 15.5.

**TABLE 15.5 Best Features Selected with the Pearson Correlation Coefficient from Dataset A**

| FEATURES | SCORES | DESCRIPTION |
|---|---|---|
| Destination loss (DstLoss) | 0.949714 | Destination packets retransmitted/dropped |
