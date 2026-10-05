$y = \mathbf{m}^tX$

Where $\mathbf{m}$ is a posterior mean vector and is defined below,

$\mathbf{m} = \beta(\beta XX^t + \alpha I)^{-1}XY$

# 3.4 Evaluation and generalisation of a supervised machine learning model

Discriminant analysis or classification analysis belong to the supervised machine learning category. A critical issue of a supervised machine learning model is whether it has been properly evaluated before being delivered for real use, i.e., for the inference on new data. There are mainly two approaches for evaluating a discriminant analysis model. They are the confusion matrix for the fix-point evaluation and the receiver operating characteristic analysis for the robustness evaluation. The other issue in relationship with a supervised machine learning model is whether the performance of the model has been well tested using a novel data set. This process is called the generalisation test of a supervised machine learning model. This section will address these two practical issues.

# 3.4.1 Confusion matrix

A confusion matrix is a fix-point evaluation approach [Stehman, 1997]. The outputs of most discriminant models are continuous. A threshold is required to convert the continuous model output variable ($\hat{y}$) to a binary prediction class variable. Suppose a threshold $(\delta$) $\hat{y} < \delta$ will lead to one class label as zero and $\hat{y} \geq \delta$ will lead to other class label as such.

After a discriminant model has been constructed and predictions have been made, an output (prediction) table will be received as shown in Table 3.1. Suppose a threshold has been decided. The prediction variable $\hat{y}$ is converted to the prediction label variable $Z$. It is also suspected that the data is composed of two classes of data points, which are labelled by $A$ and $B$. Table 3.2 shows such a prediction table, in which two columns were