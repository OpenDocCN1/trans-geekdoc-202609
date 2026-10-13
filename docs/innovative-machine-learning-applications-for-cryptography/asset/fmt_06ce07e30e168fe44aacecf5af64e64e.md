
# LightGBM Tree Growth Strategy

The LightGBM tears the tree leaf-wise as contrasting to other boosting algorithms that develop tree level-wise as shown in [Figure 2](#979-8-3693-1642-9.ch005.xhtml#f02). Since the leaf is predetermined, the leaf-wise algorithm has a minimal loss compared to the level-wise algorithm. Furthermore, histogram-based procedures in LightGBM enables transferring continuous attribute values from bucket to discrete bins (Ping et al., 2007, Liang et al., 2019, [Devan and Khare 2020](#979-8-3693-1642-9.ch005.xhtml#r7)). This increased speedup training and decrease memory usage. LightGBM uses graph deduction to speed up training. Based upon this, we may converse histograms only for one leaf, and get its neighbor's histograms by deduction as fine. Thus, in LightGBM depth limit is exploited to obtain highest prediction accuracy without overfitting problem.

| Figure 2. LightGBM leaf-wise tree growth |
| --- |
| ![Figure979-8-3693-1642-9.ch005.f02](i/ch005.f02.png) |

# 4. DATASET AND METHODOLOGY

Narrow search is the limitations of popular grid search method and also difficult in finding optimal parameters (Cheng and Shi, 2021). Python provides toolkits to optimize parameters using WOA, learning rate, sampling rate and identifying depth of a tree ([Zhou et al., 2018](#979-8-3693-1642-9.ch005.xhtml#r32), [Wu 2024](#979-8-3693-1642-9.ch005.xhtml#r27)). The dataset, NSL-KDD, is the benchmark dataset of the proposed model. The KDD dataset is utilized for experiments and this model reduces the frequency of false detection. This dataset is a boosted modification of the 'KDDCup99' dataset with a larger set of features that afford the basis for the accuracy of archetypal in sensing and prevention intrusions (Theepa 2023). The dataset is free off redundant and repeated data which enables instant use of dataset in the training and testing stages (Nadiya et al., 2020). Training data includes around 126,000 data and 4 types of threats classes such as

*   Gathering information regarding networks and identifying security control system avoidance techniques.
*   Causing the machine network to slow down or stop service access.
*   Illegal system accessing through remote packets spoofing.
*   Finding system vulnerability and using it as a normal handler.

Initially preprocess the dataset and then normalize dataset by applying MIN-MAX normalization technique. One-hot-encoding method converts symbolic features into numerical values which can be further processed for feature selection from 41 existing features. The highest accuracy of 99.2% is obtained when number of features is reduced to 21 using LightGBM algorithm (Nadiya et al., 2020). Several features along with threshold values for feature selection and their respective accuracy percentages are shown in [Table 2](#979-8-3693-1642-9.ch005.xhtml#t2).

## Table 2. Features with threshold and accuracy values (Nadiya et al., 2020)

| S. No | Number of Features | Threshold Value | Accuracy |
| --- | --- | --- | --- |
| 1 | 1 | 0.154 | 88.55% |
| 2 | 2 | 0.087 | 92.88% |
| 3 | 3 | 0.061 | 94.17% |
| 4 | 4 | 0.049 | 95.05% |
| 5 | 6 | 0.048 | 98.40% |
| 6 | 7 | 0.047 | 98.34% |
| 7 | 9 | 0.044 | 98.37% |
| 8 | 10 | 0.037 | 98.55% |
| 9 | 11 | 0.036 | 98.67% |
| 10 | 13 | 0.031 | 98.72% |
| 11 | 14 | 0.029 | 98.69% |
| 12 | 17 | 0.019 | 99.06% |
| 13 | 20 | 0.013 | 99.07% |
| 14 | 21 | 0.009 | 99.20% |
| 15 | 23 | 0.007 | 99.18% |
| 16 | 25 | 0.006 | 99.13% |
| 17 | 28 | 0.005 | 99.10% |
| 18 | 29 | 0.004 | 99.07% |
| 19 | 30 | 0.003 | 99.07% |
| 20 | 31 | 0.002 | 99.10% |
| 21 | 33 | 0.001 | 99.10% |
| 22 | 41 | 0 | 99.12% |

## 4.1 Whale Optimization Algorithm With LightGBM Methodology

Assign the LightGBM parameters such as learning rate, number of boosted trees to fit, Maximum number of tree depth and tree leaves. These parameters define the position vector for every whale. The WOA finds the global optimal point through iterative search which is the ending parameter of the LightGBM model (Cheng and Shi, 2021 and [Xiang et al., 2022](#979-8-3693-1642-9.ch005.xhtml#r28)).

This paper proposes WOA optimization parameters with LightGBM algorithm. Python toolkit LightGBM optimizes the parameters with fast learning rate and maximum depth limit of the decision tree without overfitting ([Xiang et al., 2022](#979-8-3693-1642-9.ch005.xhtml#r28)).

The following steps involved in the proposed method are as follows:

*   Step 1: Preprocess the data set with normalization and perform the dimensionality reduction.
*   Step 2: Initialize the WOA and set whales in a 3-D space with population density, number of iterations
*   Step 3: Set Upper and lower limits of LightGBM and generate initial whale population within the search space boundary.
*   Step 4: Calculate fitness of each whale location based on LightGBM model where the strength task is opted as the Mean Square Error (MSE) task.
*   Step 5: Identify the location of whale according to the following three components prey search, spiral and random search within predetermined boundary.
*   Step 6: Find the best whale location of the current whale by sorting all extracted fitness values. This best location is considered as the current global optimal location.
*   Step 7: Using equations (1) to (5) update the whale position.
*   Step 8: Repeat steps 2 to 4 to produce iterative optimization until the maximum number of iterations is reached. Thus, the best parameter and absolute whale position is obtained.
*   Step 9: The finest parameters and WOA search results are integrated with the LightGBM model to find the best intrusion detection model once trained.

# 5. EXPERIMENTS AND RESULTS

The experimental environment consists of a windows 10 operating system, Python 3.6, PyTorch 1.3 and system with 64 GB of memory. For the given dataset, the experiment result of 10-fold CV is concise as shown in [Table 3](#979-8-3693-1642-9.ch005.xhtml#t3). The WOA with LightGBM model detects intrusion effectively compare to all other models, WOA with SVM, WOA with XGBoost and GirdSearch with XGBoost. The proposed model WOA with LightGBM algorithm results in high accuracy which is depicted in the [Table 3](#979-8-3693-1642-9.ch005.xhtml#t3).

While comparing the accurateness of our projected type and general machine learning algorithms XGBoost -78.61 LightGBM – 89.82 as shown in [Table 3](#979-8-3693-1642-9.ch005.xhtml#t3).

## Table 3. Model with specificity, sensitivity, and accuracy

| Model | Specificity | Sensitivity | Accuracy |
| --- | --- | --- | --- |
| GridSearch with XGBoost | 0.981 | 0.907 | 0.981 |
| WOA with SVM | 0.998 | 0.906 | 0.980 |
| WOA with XGBoost | 0.996 | 0.955 | 0.991 |
| WOA with LightGBM | 0.999 | 0.976 | 0.998 |

On average WOA- LightGBM model is more than 10 times faster than WOA-XGBoost as shown in [Figure 3](#979-8-3693-1642-9.ch005.xhtml#f03).

| Figure 3. Comparison chart for WOA-XGBoost and WOA-LightGBM |
| --- |
| ![Figure979-8-3693-1642-9.ch005.f03](i/ch005.f03.png) |

## 4.2 Performance Evaluation for Intrusion Detection

The system of measurement used to evaluate the performance of a binary classification model are Precision, Recall, and F1-score. These systems of measurement are valuable in gauging the performance of an archetypal when the classes are imbalanced. Measure the effectiveness of intrusion detection using a confusion matrix (see below) ([Zhao et al., 2021](#979-8-3693-1642-9.ch005.xhtml#r31)) to deduct normal or abnormal (intrusion) with the subsequent notations,

*   TP - true positive
*   FP - false positive
*   TN - true negative, and
*   FN - false negative

![Mathtype979-8-3693-1642-9.ch005.m05](i/ch005.m05.png)

| Figure 4. Relationship of precision, recall, and specificity with TP, FP, FN, and TN |
| --- |
