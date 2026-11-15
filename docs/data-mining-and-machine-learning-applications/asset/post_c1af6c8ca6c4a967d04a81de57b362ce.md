
| Incident ID | Incident Activity ID | Incident Activity | Assignment | # Reassignments | Handle Time | # Related | Status | Business | Severity | Priority |
|---|---|---|---|---|---|---|---|---|---|---|
| IM00000004 | 001A3689763 | Reassignment | TEAM0001 | 26 | 3871 | Other | Closed | 4 | 4 | 4 |
| IM00000005 | 001A5852941 | Reassignment | TEAM0002 | 33 | 4354 | Software | Closed | 3 | 3 | 3 |
| IM00000006 | 001A5852943 | Update from customer | TEAM0002 | 13 | 43 | Operator | Closed | 4 | 4 | 4 |
| IM00000007 | 001A5849980 | Operator Update | TEAM0003 | 2 | 3383 | Other | Closed | 4 | 4 | 4 |
| IM00000008 | 001A5849979 | Assignment | TEAM0003 | 4 | 3383 | Other | Closed | 4 | 4 | 4 |
| IM00000009 | 001A5852942 | Assignment | TEAM0002 | 2 | 3703 | Unknown | Closed | 4 | 4 | 4 |
| IM00000010 | 001A5852172 | Closed | TEAM0003 | 5 | 3294 | Other | Closed | 4 | 4 | 4 |
| IM00000011 | 001A5852173 | Caused By CI | TEAM0003 | 2 | 0 | Other | Closed | 3 | 3 | 3 |
| IM00000012 | 001A5849978 | Reassignment | TEAM0003 | 6 | 3067 | Software | Closed | 4 | 4 | 4 |
| IM00000013 | 001A5544096 | Operator Update | TEAM0003 | 8 | 1322 | Software | Closed | 4 | 4 | 4 |
| IM00000014 | 001A4725475 | Update | TEAM9999 | 5 | 1132 | Software | Closed | 4 | 4 | 4 |
| IM00000015 | 001A4327777 | Operator Update | TEAM0003 | 17 | 66 | Software | Closed | 4 | 4 | 4 |
| IM00000016 | 001A3689771 | Reassignment | TEAM0001 | 1 | 3114 | Data | Closed | 3 | 3 | 3 |
| IM00000017 | 001A5377163 | Operator Update | TEAM0003 | 3 | 2837 | Other | Closed | 4 | 4 | 4 |
| IM00000018 | 001A43996943 | Operator Update | TEAM0003 | 1 | 1223 | Other | Closed | 4 | 4 | 4 |

Figure 7.8 Raw data collected from organization.

![](img/48ffcb334b2fea865a1f194394911123_203_0.png)

Figure 7.9 Research methodology to develop effort prediction model.

## 7.4.1 Input Parameters

As per EDA, the L2 and L3 severity and L2 and L3 priority tickets have more average TTR compared to high and low priority tickets, altogether, and the volume of tickets logged during weekdays from 8 AM to 6 PM is more. Therefore, further in this research, L2 and L3 level severity and priority tickets logged on weekdays from 8 AM to 6 PM will be considered. Insights obtained from related research and the opinions from expert reviews are considered further for the selection of input parameters for the modeling of prediction of effort required in resolving different incidents. Based on the preliminary analysis, the following input parameters are identified in the developing the predictive model for incident closure effort.

- Application: An overall of tickets logged under seven applications are considered that comes under custom and packaged product technologies.
- Priority: In this research priority levels 2 and 3 are considered.
- Severity: Tickets with severity levels 2 and 3 are considered in this research
- SLA Compliance: Both tickets that met and could not meet the SLA clauses are considered.
- Primary Technology: Five different primary technologies are considered.
- Root Cause: Six different root causes are present in the tickets that are used in the modeling.
- Complexity: Tickets with four levels of complexity were present in the ticket logs.
- No. of reassignments: The number of reassignments required to resolve an incident and close the associated tickets depends on the ticket type and the associated data is considered as such.
- Risk Assessment: tickets with Medium and High level risk factors are considered in the research.

## 7.4.2 Predictive Modeling

Effort prediction models for the tickets raised are modeled using random forest tree based algorithm. The same is presented further in this chapter. Further, analysis of the model is based on the result obtained.

## 7.4.3 Random Forest Model

Random Forest is a tree based ensemble model. Multiple trees are grown as per the training set data. Each tree is grown based on a subset of variables and a subset of data points. The process of growing the trees are called tree bagging. Its main advantage is that it overcomes overfitting of the model and change in the dataset has little effect on the outcome. Average of the trees when adopted in prediction will decrease the noise. Further, optimization is achieved using cross validation that estimates the level of fit. The algorithm for random forest is as follows:

Given a training dataset X = x1, x2, x3 ..., xn and the response be Y = y1, y2, y3, ..., yn.

- Initialize B which is a random value and the number of times bagging should be repeated
- For b = 1, 2, ..., B:
  - Sample the dataset with replacement, training dataset from X, Y. Xb, Yb be the sampled subsets of X and Y respectively.
  - Grow a regression tree fb on Xb, Yb

Prediction on test dataset x' is a function f(x') which is

```
f(x') = \frac{1}{B} \sum_{i=1}^{n} f_b(x')
```

A total of 500 decision trees are randomly modeled using the training dataset. The development of the model is performed using the Random Forest package meant for the classification and regression based on a forest of trees using random inputs. The Breiman and Cutler’s Random Forests for Classification and Regression package [17] provides a randomForest() function that is used to build the model using training dataset and is further used in the prediction of incident resolution effort in the test dataset. Error measures like MAPE, MSE, RMSE and MAE tests are performed in order to validate the same.

The actual and the predicted effort by the developed models, for the training and test dataset are represented in Figures 7.10 and 7.11 for regression tree and random forest respectively.

![](img/48ffcb334b2fea865a1f194394911123_206_0.png)

Figure 7.10 Effort values predicted vs. observed using training and test dataset.

![](img/48ffcb334b2fea865a1f194394911123_206_1.png)

Figure 7.11 Effort values predicted vs. observed using training and test dataset.

Table 7.2 Overfitting, testing error and accuracy of the random forest model.

| Model | Overfitting | Accuracy | Testing error |
|---|---|---|---|
| Random Forest | 0.3475 | 0.88 | 0.3228 |

## 7.4.4 Performance of the Predictive Model

The tabulated results presented in Table 7.2 shows that the decision tree based predictive model can predict the effort required in resolving an incident with an accuracy of 88%. The overfitting value is less while considering random forest algorithm. But a general property of random forest is its inability to predict accurately in the presence of data values that are not present in the dataset. Therefore, this general property of random forest model makes it unsuitable for considering it as a predictive model for incident resolution effort. In such a situation, alternate approaches has to be adopted. Other machine learning based models can be developed in the similar way and its performance can be compared. Analyze the features that is required and whether it is suitable for the problem under consideration need to be addressed. An optimum model that will give more accurate result with the minimum error need to be deployed for predictive analytics and effort prediction.

## 7.5 Conclusion

All the services provided by your IT team can be termed—IT services and ITSM is a framework that has detailed steps that need to be followed when a service request comes up or an incident occurs. The data generated in the ITSM process is not friendly enough to easily produce metrics and reports. Adopting of predictive analytics can help in dealing with these issues. Increased speed of execution, cost reductions, improved customer experience, reduced human error, increased task adaptability, self-service are some of the advantages that predictive analytics offer enterprises when adopted with ITSM. Day to day operation in ITSM can further result in TTR effort prediction, root cause analysis, predicting occurrence of maintenance activity, track and manage the performance of IT assets efficiently, automated solutions, proactive prevention of tasks, automatic classification of incidents and service requests, predict SLA/contract violations, workload optimization, etc. This chapter further presents a case study on Ticket Analytics. The effort required to resolve an incident is predicted
