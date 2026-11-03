
Finding the best effective data mining algorithms for use in clinical diagnostics is a time-consuming process. The purpose of this research was to determine which predicted algorithms for data mining are the most effective when used to make dental disease diagnoses. Predictive data mining model was constructed using `K-nearest neighbor` (`KNN`) and `multilayer perceptron` (`MLP`) processors in this work. To further assess the classifiers’ prediction abilities off the bat, we employed `10-fold crossvalidation` and a variety of performance indicators. The results of the comparison reveal that `MLP` has the highest accuracy (97.4%), followed by `KNN` (94.6%). Expertise in the predictive capacity of various data mining algorithms usable in clinical diagnosis, in particular in the identification of dental or oral illnesses, was gained through the assessment of such classifications on medical datasets.

**Keywords:** Dental diseases, `MLP`, `KNN`, predictive data mining

## Introduction
Predictive analytics is a subfield of data mining that aims to foresee possible outcomes by analysing past data for patterns and linkages \[[1](#ch27.xhtml#ref27_1)\]. Predictive analytics is a broad field that includes disciplines like statistics, data mining, and game theory \[[2](#ch27.xhtml#ref27_2)\]. Predictive modelling entails four stages: data collection, model development, prediction, and model validation/refinement based on new information \[[3](#ch27.xhtml#ref27_3), [4](#ch27.xhtml#ref27_4)\]. Strategic research is the foundation of clinical data mining, which is used to obtain, analyse, and interpret qualitative and quantitative data from healthcare datasets or records \[[4](#ch27.xhtml#ref27_4)\]. To anticipate the categories of new datasets that have not yet been labelled, predictive data mining first generates a classification model using a training dataset \[[5](#ch27.xhtml#ref27_5)\]. In order to aid doctors in their diagnostic, therapeutic, or monitoring endeavours, predictive data mining focuses on learning models \[[6](#ch27.xhtml#ref27_6)\]. It uses machine learning techniques to construct multivariate approaches from medical information and, using those models, to draw conclusions about previously unseen data \[[7](#ch27.xhtml#ref27_7)\]. The use of guided classification methods is central to the machine learning model. The data is cleaned up and the data mining principles are tested on real data before the learning model is implemented \[[8](#ch27.xhtml#ref27_8), [9](#ch27.xhtml#ref27_9)\]. knowledge discovery in databases (`KDD`) refers to the process of preparing, mining, and analysing data for insights into business and the real world. Predictive data mining is the most popular subset of `KDD`. Several instances include the use of gender, years of age, smoking and status, hypertension, and different biomarkers to predict surgical outcomes \[[10](#ch27.xhtml#ref27_10)\], tumour survival \[[11](#ch27.xhtml#ref27_11)\], and risk factors for coronary heart disease \[[12](#ch27.xhtml#ref27_12), [13](#ch27.xhtml#ref27_13)\]. First, consider the individual’s overall condition (healthy, diabetic, pressure patient, pregnant) and age (baby, child, and young, adult) before studying the patient’s symptoms to pinpoint the source of pain and the nature of the disease \[[14](#ch27.xhtml#ref27_14)\]. It’s important to remember that oral illnesses can progress to a critical stage before any obvious signs in the oral cavity or teeth show. Therefore, it’s important to make sure the dental and oral health clinic is up to par.

“The given paper is organized into following sections. Section 2 provides a review of studies conducted in the context of applications of data mining to predict various diseases. Section 3 presents methodology of the proposed approach. It involves defining `K-nearest neighbor` (`KNN`) and `multilayer perceptron` (`MLP`) classifiers. Section 4 presents empirical results and analysis. Section 5 presents summary of the findings and proposes recommendations for further research.”

## Literature Review
Only accuracy, error rate, precision, and recall were included in \[[15](#ch27.xhtml#ref27_15)\]’s comparison of decision tree (`DT`), artificial neural network (`ANN`), and support vector machine (`SVM`) for illness detection. A `10-fold cross-validation` test of these prediction models’ objectivity is not used. In \[[16](#ch27.xhtml#ref27_16)\], the authors showed how to use a Bayesian modelbased clinical expert system for detecting the presence of coronary artery disease based on the available data. When compared to logistical and linear regression models, the Bayesian was thought to be superior when coping with many missing variables. To determine which machine learning method is most effective and efficient for determining the severity of asthma using a skilled system, the authors of \[[17](#ch27.xhtml#ref27_17)\] compared Bayesian networks, `ID3`, and `C4.5`. Studies attempted to validate \[[18](#ch27.xhtml#ref27_18)\]’s proposal of an Advanced learning machine and Artificial Neural Network for better differentiating skin disorders. The search techniques sequential forward floating search (`SFFS`) and sequential backward floating search (`SBFS`) were utilized; with feature significance determined using the generalized `F-score` \[[19](#ch27.xhtml#ref27_19)\]. It was stated that the two-phase hybrid model improved upon previous algorithms for identifying skin and dental problems in terms of classification accuracy.

## Proposed Methodology
[Figure 27.1](#ch27.xhtml#fig27_1) illustrates the procedures to be followed.

![Figure 27.1 Workflow of the proposed approach](images/fig27_1_B.jpg)

[Figure 27.1 Workflow of the proposed approach](#ch27.xhtml#R_fig27_1)

### A. Dataset Collection
Caries, gingivitis, tooth discoloration, and hypodontia are just few of the many dental issues we looked at using the oral health dataset. This dataset is available for use in the development and instruction of models for detecting and classifying dental conditions, and it was obtained from the Kaggle repository \[[20](#ch27.xhtml#ref27_20)\].

### B. Pre-Processing and Features Extraction
“It is done with the help of `WEKA` \[[21](#ch27.xhtml#ref27_21)\] - a data mining and analysis tool for performing classification and predictive mining in diagnosis of various diseases.”

### C. Classifiers- `KNN` and `MLP`
The `KNN` is a supervised-learning-based classifier that uses the proximity of data points to one another to generate predictions about the appropriate categories for those data points. Classification issues are where this approach shines, however it has applications in regression as well. It does this by assuming that related points tend to cluster together.

For many classification and prediction tasks, the go-to feed forward neural network is the `MLP`. During the learning phase, `MLP`’s input variables (`weights` and `biases`) are fine-tuned utilizing a gradient-based approach to ensure optimal behavior.

### D. n Folds Cross Validation
Estimating a model’s accuracy in practice may be done with the help of `n-fold cross-validation`, also known as rotation estimation. It entails arbitrarily dividing a dataset `D` into `s` distinct groups. It is taught each time on the entire dataset and then tested on the remainder of folds. In the method we have presented, `n` equals 10.

### E. Evaluation based on metrics
The assessment of prospective data mining algorithms may be conducted by considering several metrics. When evaluating the predictability of various predictive data mining algorithms, it is necessary to evaluate certain metrics that assess the quality of model fit and error measures \[[22](#ch27.xhtml#ref27_22)\]. The metrics utilized in the study are as follows. The ideal data-splitting properties may be established with the use of an “`entropy calculation`”, this is a statistical technique for measuring how much data has been skewed.

(1)
```
Entropy = ∑ - p[i] log p[i]
```
(2)
