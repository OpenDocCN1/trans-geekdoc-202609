
Once statistical network flow characteristics were extracted, we annotated them to indicate whether or not they belonged to malicious or benign traffic.

## C. Pre-Processing of Data Packets

In order to get rid of extraneous information, this is performed. In this case, we improved the quality of the data by using `open refine` [[15](#ch23.xhtml#ref23_15)], formerly known as `Google refine`, as a pre-processing tool.

## D. Feature Extraction and Selection

An integral component of our investigation is portrayed here. We’ve retrieved a number of statistical characteristics of network traffic, but it’s still up to us to figure out which ones are most relevant to our study. With the help of a feature selection policy, we can zero down on the most important aspects of the data. We utilised the `Weka` tool’s `BestFirst` search to identify the most frequently occurring features, a wrapper approach that falls under the reverse feature selection strategy [[16](#ch23.xhtml#ref23_16)]. To further improve the model’s performance, backward elimination involves starting with the most basic elements and gradually eliminating the ones that aren’t absolutely necessary.

## E. Train and Test Model Using Random Forest (RF)

For both model development and testing, we used the `Weka` simulation framework. We used a 10-fold crossvalidation procedure to construct and train our model on 80% of the data, and then applied the `Random Forest` classifier on 20% of the data to see how well it performed under test conditions. `Random Forest`, functioning as an ensemble classifier, has superior performance compared to conventional classifiers in reliably classifying network traffic. When doing a comparative analysis of several machine learning classifiers, it is well recognised that the `Random Forest Algorithm` has a prominent position. It makes use of a voting system to produce predictions using an ensemble technique that comprises of different decision trees. The versatility of random forest lies in its ability to solve the two types of problems that make up the majority of modern machine learning systems: regression and classification.

## F. Evaluation Based on Metrics

Using these measures, we determined how well our suggested network classifier-based strategy performed.

The measure of accurate forecasting is determined by the proportion of true positives within a certain sample. The performance of an algorithm in accurately identifying all positive samples is evaluated by its recall metric. `Precision` and `Recall` are averaged in order to form the `F1 Score`.

(1)

`Precision = TP/(TP + FP)`

(2)

`Recall = TP/(TP + FN)`

(3)

`F1-score= 2 (Precision^(\*)recall)/(precision+recall)`

(4)

`Accuracy score = (TP + TN)/(TP + TN + FP + FN)`

Where `TP` denotes true positive, `TN` denotes true negative, `FP` denotes false positives and `FN` denotes false negatives.

## Result and Implementation

The first phase begins with capturing of packets using analyzer having source address, destination address, protocol and size of packets (in bytes).

It is seen from [Figure 23.2](#ch23.xhtml#fig23_2) that the live packets from Wi-Fi network are captured. Each packet contains timestamp, source address, destination address, type of protocol used and size of packets (in bytes). This statistical information is further used for categorization of packets as benign or malicious.

![Figure 23.2 Capturing of network packets using Wireshark analyzer.](images/fig23_2_C.jpg)

[Figure 23.2 Capturing of network packets using Wireshark analyzer.](#ch23.xhtml#R_fig23_2)

[Figure 23.3](#ch23.xhtml#fig23_3) displays the percentage distribution of packets captured in Wi-Fi network. It is seen that benign packets contribute to 43% of the total packets while malicious packets are 57% overall. The malicious packets are divided into ransomware, backdoor, spyware and Trojan horse.

![Figure 23.3 Categorization of network packets after capturing](images/fig23_3_C.jpg)

[Figure 23.3 Categorization of network packets after capturing](#ch23.xhtml#R_fig23_3)

[Figure 23.4](#ch23.xhtml#fig23_4) shows the features extracted in response to captured data packets for monitoring flow of traffic in the network. It is seen that there are 11 distinct features associated with packets. They are based on type of protocol used like `HTTP`, `TCP`, and `UDP` etc. It also contains forward and backward packets with their header lengths and so on.

![Figure 23.4 Features selection and extraction using WEKA](images/fig23_4_C.jpg)

[Figure 23.4 Features selection and extraction using WEKA](#ch23.xhtml#R_fig23_4)

[Figure 23.5](#ch23.xhtml#fig23_5) shows 10 folds cross validation of captured packets dataset with the help of `Random Forest` classifier. It takes only 0.03 seconds to build and validate the model.

![Figure 23.5 Training and testing of model using rf classifier](images/fig23_5_C.jpg)

[Figure 23.5 Training and testing of model using rf classifier](#ch23.xhtml#R_fig23_5)

The simulation programme provides detailed documentation of the installation of the `Random Forest` classifier on our dataset after its use.[Table 23.1](#ch23.xhtml#tab23_1) demonstrates that the implementation of a random forest classifier yields precise and dependable outcomes, exhibiting pertinent properties for the given testing dataset.

[Table 23.1 Classification results showing efficiency of the proposed approach.](#ch23.xhtml#R_tab23_1)

| Parameters || Values achieved |
| --- | --- |
| Correctly classified instances (%) || 90.565 |
| --- | --- |
| Incorrectly classified instances (%) || 9.435 |
| Kappa statistic || \- |
| Mean absolute error (`MAE`) || 0.0884 |
| Root mean squared error (`RMSE`) || 0.1339 |
| Relative absolute error (%) || 39.2822 |
| Root relative squared error (%) || 40.6189 |
| Total number of instances || 11 |

## Results

[Figure 23.6](#ch23.xhtml#fig23_6) shows that usage of `random forest` classifier in training and testing our packets captured model proves to be a reliable scheme with higher precision and recall as compared to the existing approach. The `precision`, `recall`, `F1-score` value, `TPR` and `FPR` values for the proposed approach are 0.94, 0.95, 0.94, 0.954 and 0.025 respectively.

![Figure 23.6 Comparison of proposed and existing approach used in the study](images/fig23_6_C.jpg)

[Figure 23.6 Comparison of proposed and existing approach used in the study](#ch23.xhtml#R_fig23_6)

[Figure 23.7](#ch23.xhtml#fig23_7) shows that accuracy achieved in our proposed approach with the use of machine learning classifier is 94% which is higher than existing approach (89%).

![Figure 23.7 . Accuracy comparison between our proposed approach and existing approach](images/fig23_7_C.jpg)

[Figure 23.7 . Accuracy comparison between our proposed approach and existing approach](#ch23.xhtml#R_fig23_7)

The results of our proposed method are shown in [Figures 23.7](#ch23.xhtml#fig23_7).

## Conclusion and Future Work
