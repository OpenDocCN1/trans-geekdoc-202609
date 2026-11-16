solve the glass identification problem. Multiple classifiers will be used to achieve this goal (Dong et al. 2020; Rincy and Gupta 2020). The flow diagram used to solve this problem is shown in Figure 1 below.

![](bbox=[0.109, 0.142, 0.865, 0.363])

Figure 1. Flow diagram to be followed to solve this problem.

# 4.1 Data pre-processing

Despite the adherence to the appropriate structure of a dataset, it may nevertheless need pre-processing before using a data mining method. This will allow for a higher-quality analysis due to the study. There are a lot of different approaches to preparing data. Since there are no missing numbers, the data on glass is in a relatively clean state.

# 4.2 Feature selection

Feature analysis is done to identify the most relevant compounds influencing glass type. Various feature selection approaches may be used to ascertain the crucial variables required for classification, including correlation analysis, recursive feature removal, and feature significance derived from ensemble models.

# 4.3 Ensemble model selection

A method based on “ensemble learning” has been selected. In this instance, various machine learning models will be used to form the ensemble. These models aim to increase confidence in glass identification.

# 4.4 Support vector machine algorithm

The SVM method has a kernel and linear sections. SVM can solve classification and regression problems. SVM is better at finding deep patterns in complex datasets than other methods. For classification, we calculate the characteristic-based hyperplane that separates the two classes. Hyperplanes categorize decision boundaries. Comparing data points on opposing sides of the plane reveals distinct types(Colomban 2013b).

Support vector machines aim to maximize data point-hyperplane margin(Rincy and Gupta 2020).

Linear equation: y = a + b. We obtain ax1x2 + b = 0 if we replace x with x1 and y with x2. It can be shown that wx + b = 0 if x is defined as (x1,x2) and w as (a,1).