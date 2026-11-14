
### 10.5.2 Unsupervised learning

`Unsupervised ML` works with unlabeled data to find the pattern within an existing dataset [[39](#ch10.xhtml#ref10_39)]. This algorithm typically works on the method of grouping data on the basis of similarity. `K-means` clustering is the most well-known and widely utilized method. The association task related to clustering is also solved with the help of such a clustering method. The standard `k-means` clustering was further modified and named `k-medians` or `k-medoids`. In the case of `k-clusters`, the nearest center and mean are calculated based on `Euclidean distance`. The most common problem associated with this method is that it needs a probable number of means [[40](#ch10.xhtml#ref10_40)].

### 10.5.3 Semi-supervised learning

In such types of `ML` techniques, the model is trained by utilizing labeled and unlabeled datasets. In such datasets, the amount of unlabeled data is very large as compared to the labeled dataset. In such a learning technique, the first `unsupervised learning` approach is followed to cluster the unlabeled dataset, and, after that, they are labeled by utilizing the existing labeled dataset. Mostly in healthcare, such type of learning approach is followed for speech analysis and protein classification sequences [[41](#ch10.xhtml#ref10_41)].

### 10.5.4 Reinforcement learning

In such types of `ML` approach, a model learns from the moments of activities within an environment rather than by openly trained with the given set of inputs and outputs. Such types of trained machines learn from previous experiences and take an immediate new decision based on `trial and error learning`. This technique is highly utilized to generate expert systems for healthcare applications [[41](#ch10.xhtml#ref10_41)].

## 10.6 Working Process

`ML process` mainly describes the way followed by any `ML algorithm` for the implementation of any data. `ML process` starts with the collection of data from multiple sources and is followed by a tweaked interaction of information; after that, the information would be fed to any `ML algorithm` based on the statement of the problem. The complete working process is divided into five stages as discussed below. Before the application of any `ML algorithm`, the objective for which the `ML` is to be applied must be clear. For finding the solution to any problem, first of all, data must be collected and the below strategies must be applied appropriately [[42](#ch10.xhtml#ref10_42)], [[43](#ch10.xhtml#ref10_43)].

![Figure 10.5 Machine learning working process [43].](images/fig10_5_C.jpg)

Figure 10.5 Machine learning working process [[43](#ch10.xhtml#ref10_43)].

*   `Data collection:` This phase collects the data from multiple sources, be it the sensor collected or recorded data depending upon the nature of the application. In terms of smart healthcare, data may be collected from different worn and implanted sensors on the patient’s body or some other medical device.
*   `Data cleaning:` Data collected from different sources may consist of noise and some irregularities. The data cleaning process starts with the removal of noise and inconsistency among data to find a better result.
*   `Selecting right algorithm:` As there exist lots of `ML algorithms` and each algorithm is evaluated with different evaluation measures like `root mean square error`, `confusion matrix`, `sensitivity`, `error rate`, and `time-consumption`. Depending upon these evaluation parameters, the best algorithm is selected.
*   `Building model:` Building a model means training the model using the `training dataset`. `Training dataset` is computed from original dataset by splitting it into `training` and `testing dataset` using some `splitting criteria`.
*   `Prediction:` Prediction mainly refers to the outcomes generated after the application of the model.

## 10.7 Machine Learning Algorithms in the Healthcare Industry

`ML algorithms` are highly employed in the healthcare industry for the forecast of diverse diseases and are described below.

### 10.7.1 Support vector machine

This is the most common `ML algorithm` highly utilized in the healthcare industry. This algorithm can classify the hidden information by deriving the nominated features and by creating a high-dimensional hyperplane to classify the data into different classes to derive a decision model. Due to the ability to classify the high-dimensional data by utilizing a minimum training set of features, it is highly utilized for handling physiological data for healthcare applications. This technique is enabled by `kernel techniques`; various optimization problems in high dimensional space utilized `kernel functions`. During `SVM` implementation, `training data` is plotted onto a new `feature space` by using the `kernel optimization function` and produces a large marginal separation between the `training data` in the novel `feature space` [[44](#ch10.xhtml#ref10_44)], [[45](#ch10.xhtml#ref10_45)]. For example, a given labeled sequence (*A*[1], *B*[1]), ... (*A[m]*, *B[m]*), where `A` represents the `covariant` and *B* Ɛ {-1,1}, is the answer. A `kernel function` *k* is operated through `SVM` by means of using the following equation:

`f(x) = a^T x + c`

At this point, `a` denotes the dimensional coefficient and `c` is the offset. `SVM` has fewer overfitting complications and can simply work with composite structured datasets.

In the healthcare sector, normal wellbeing boundaries considered by `SVM` are `HR`, `ECG`, and `SpO[2]` which are short and annotated health parameters. Hu *et al.* [[46](#ch10.xhtml#ref10_46)] utilized the `SVM` technique to diagnose arrhythmia disease from `ECG` signals captured from `ECG` devices. Similarly, Lee *et al.* [[47](#ch10.xhtml#ref10_47)] also proposed an `SVM` method for identifying arrhythmia using `ECG` signals. The result displayed that the `SVM` method with `polynomial kernel` provides an improved outcome as compared to other kernels. Most of the researchers have used `SVM` for the classification and diagnosis of different diseases on both sensor and clinically recorded data. However, from the conclusion made by different researchers, they found that `SVM` cannot be used as an appropriate technique to integrate domain knowledge and symbolic knowledge seamlessly on data collected from sensors. Along with that, `SVM` cannot be applied to find unforeseen info from unlabeled data.

### 10.7.2 Logistic regression (LR)

`LR` is a highly flexible and robust method used for dichotomous classification purposes. This method is highly effective to make a classification in terms of binary outcomes or states like yes or no, success or failure, and will occur or not occur. This method is highly effective in most cases where `linear regression` does not work. This is because along with making numerical value predictions, it also predicts a dichotomous value. Due to this associated feature, this method is named `logistic regression`. In most healthcare problems, this method provides the best result; for example, it will answer a question like whether or not a person suffers from a specific disease or not based on the symptom [[48](#ch10.xhtml#ref10_48)].

`Logistic regression` is exceptionally valuable when a dependent variable is categorical. `Logit function` utilized for assessment of likelihood is given by the following equation:

$$
\hat{p} = h_{\phi}(x) = \sigma(x^{T}\theta)
$$

where

$$
\sigma(t) = \frac{1}{1 + e^{-t}}
$$

### 10.7.3 Decision tree (DT)
