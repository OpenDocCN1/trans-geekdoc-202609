
# Protease Cleavage Pattern Discovery

A classifier with its ROC curve approaching the top-left corner is a good classifier. In this scenario, no matter what the threshold variation, the true positive rate is always 100% and the false positive rate is 0%. When an ROC curve is approaching the diagonal line, a classifier makes decisions by chance. In this scenario, the false positive rate equals the true positive rate all the times. For instance, when the false positive rate is 10% for a threshold, correspondingly, the true positive rate is also 10%. When the true positive rate becomes 90%, the false positive rate is also 90%. This means when the false positive rate is controlled, the true positive rate is also dropping to the same level. When an ROC curve is below the diagonal line, it is very likely that the predictions are on the opposite side of the raw class labels. If this happens, a higher prediction value is delivered by a model for a lower-class label value and a lower prediction value is delivered for a higher class label value. This happens when a simulation is inappropriately designed.

Based on an ROC curve, the area under a curve (AUC) is calculated, which is between zero and one. Using AUC as a measurement, a qualitative robustness visualisation using an ROC curve turns to a quantitative robustness analysis result.

ROC has a wide application in biological/medical pattern analysis research. For instance, ROC has been used to evaluate the performance of a classification model for assessing the prognostic function of EEG in cardiac arrest practice [Barbella, et al., 2020] and to predict postoperative pancreatic fistula for patients who suffer from distal pancreatectomy with geriatric nutritional risk index [Funamizu, et al., 2020].

One of the widely used R packages for ROC analysis is ROC. To do an ROC analysis using this package, two main functions are required for a complete ROC analysis. They are the prediction function and the performance function. The former is to establish an ROC model. The latter is to extract data for drawing an ROC curve or the AUC or the accuracy, etc. Suppose two vectors y and y.hat (ŷ) are ready, an ROC model can be established using the following code:

```
my.roc=prediction(y.hat,y)
```

The ROC model my.roc is composed of many useful information. Two are important for further analysis. To draw an ROC curve, a false positive rate and a true positive rate are required to be extracted from such an ROC object using the following code, where x.measure stands for the horizontal axis of an ROC curve and measure stands for the vertical axis of an ROC curve,

```
my.curve=performance(my.roc,measure='tpr',
x.measure='fpr')
```

Based on my.curve, the plot function is called to generate an ROC curve. To acquire the AUC, the performance function is called again, where auc must be specified for the measure parameter,

```
my.obj=performance(my.roc,measure='auc')
```

The AUC value can be extracted from this AUC object using the following R code, where my.auc is the calculated AUC value and the use @ key is because my.auc.obj is an S4 object,

```
my.auc=unlist(my.auc.obj@y.values)
```

## 3.4.3 Generalisation

An important issue associated with a supervised machine learning model is its generalisation power. The generalisation power of a supervised machine learning model is an estimation of how a constructed supervised machine learning model can work for new data. Whether a model works well for new data is much more important than a model works well for data which is used to construct the model. A process of testing the generalisation power of a supervised machine learning model is called the generalisation test, which has to be implemented on new data. The meaning of new data is that the data has not been used for model construction.

All classification models are supervised machine learning models, which entirely require a supervised test in place [Devroye, et al., 1996; Bishop, 1996; Ripley, 1996]. The subject of the generalisation test of a supervised earning model has been well-exercised for analysing biological/medical data as well. For instance, classification models have been constructed for gastric and colonic epithelial tumour [Izuka, et al., 2020] and histopathology data classification [Jones, et al., 2019] and generalisation performance of these models have been tested.

In most situations it is infeasible to have new data on hand to test a supervised model. Therefore an in-house test will employ part of the available data to mimic a real-world out-house test on new data. This part of the available data is commonly reserved from the whole available data and is called a testing data set. In contrast, the data used to construct a classifier is called a training data set. The final or ultimate evaluation of a supervised machine learning model must be based on the performance of the generalisation test applied on a testing data set.

A common exercise for the generalisation test of a supervised machine learning model is to randomly divide a collected data set into two parts. One of them is used as the training data set and the other is reserved as the testing data set. However, it can be difficult to guarantee a robust distribution from an available data so to deliver unbiased generalisation performance. The robustness here means whether a random division can generate a testing data set which represents the data distribution of a training data set. This is a very important point to address and is the key of a successful generalisation test process.

Three approaches have been used for a generalisation test for a supervised machine learning model so far. They are the random sampling approach, the K-fold cross-validation approach [Devijver and Kittler, 1982, Bishop, 1996] and the Jackknife test [Quenouille, 1949; Efron and Stein, 1981].

The random sampling is an application of the Monte Carlo simulation [Metropolis, 1987]. The basic principle of Monte Carlo simulation is to draw samples from a population many times to estimate a parameter. It is proved that when the sampling time increases, the trend of a parameter will be approaching the true. Therefore, a parameter can be well-estimated if sufficient sampling times can be. To demonstrate how this works, a one-dimensional Gaussian distribution centred at zero was generated with one million data points. Many samples were then drawn from this population with a varying number from ten to 10,000 to estimate the mean of the Gaussian distribution. Figure 3.13 shows the simulation result. It can be seen that the estimated mean of the Gaussian distribution was gradually converged to the true sample, i.e., zero.

![](img/c3caa39b5c0f40fb2a44f2ab6e940f78_122_0.png)

Fig. 3.13. The estimated mean of a Gaussian distribution with varying sampling sizes.

The breast cancer data set with 569 samples [Wolberg, et al., 1995] Wolberg, et al., also used to demonstrate how the random sampling approach can help reach real data proportion. Among these 569 samples, 212 were malignant tumours. The malignancy ratio was therefore 0.373, i.e., 37.3% were malignant tumours in this data set. Many sets of half samples were drawn from this data set randomly. The malignancy ratio was calculated within the drawn sample for varying sampling times from ten to 1,000. For instance, K sampling times, K samples were drawn. K malignancy ratios were calculated for K samples. Afterwards, the mean values of K malignancy ratios within the drawn sample were recorded. It was expected when the times of random sampling was increasing, the estimated malignancy ratio within the drawn sample should approach the true ratio, i.e., 0.373. Figure 3.14 shows this simulation. From this plot, it can be seen that when the sampling times increased, the estimated malignancy ratio among randomly drawn samples was indeed approaching 0.373.

![](img/c3caa39b5c0f40fb2a44f2ab6e940f78_122_1.png)

Fig. 3.14. The malignancy ratio within sampled data with varying sampling times for the breast cancer data set.

As discussed above, it can be seen that the random sampling approach may need many repeats to reach a reasonable approximate of real value of
