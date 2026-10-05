# Biological Pattern Discovery with R

Z=y.hat>0.5

If an expected vector of raw class labels is denoted by y, a confusion matrix is generated using the following code,

```
my.confusion=table(y,Z)
```

A general format of a confusion matrix with four summary statistics shown below,

$$\begin{pmatrix} TN & FP \ FN & TP \end{pmatrix} (3.27)$

In a confusion matrix, a class labelled by a zero is treated as the negative class and a class labelled by a one is treated as the positive class. TN, TP, FN, and FP thus stand for the true negative number, the true positive number, the false negative number, and the false positive number.

Normally the negative class is used to represent a class which may not have a severe outcome and the positive class is used to denote a class which may have a severe outcome in a medical practice. For instance, in cancer diagnosis, the negative class represents the benign tumours and the positive class represents the malignant tumours. Suppose a confusion matrix is used to evaluate a model for cancer diagnosis. TN is the number of correctly classified benign tumours. TP is the number of correctly classified benign tumours which should be malignant tumours. FP is the number of predicted benign tumours which should be malignant tumours.

Five measurements can be calculated based on these four statistics for the meaningful interpretation of a classifier. The specificity is the proportion of correctly classified negative data points (benign tumours). The sensitivity is the proportion of correctly classified positive data points (malignant tumours). The total accuracy is the proportion of all correctly classified data points (tumours). The negative prediction power is the proportion of negative predictions which are indeed negative. The positive prediction power is the proportion of positive predictions which are indeed positive. For instance, these five measurements have been included in Table 3.3 for the prediction table shown in Table 3.2. Suppose class A represented the benign tumour group and class B represented the malignant tumour group. The accuracy of diagnosing a malignant tumour