# CHAPTER 3

# # Regression

In Chap. 2 we have seen examples of univariate linear regression (Sect. 2.2.1) and univariate polynomial regression (Sect. 2.3). The word **univariate** refers to having only a single feature to predict the target values. In machine learning problems, we often wish to combine multiple features to achieve more accurate predictions. Regression that involves multiple features is called **multivariate**.

In this chapter we will demonstrate various multivariate regression models using the example of **predicting the age of preterm babies from volumes of brain structures** calculated from MRJ scans, see Fig. 3.1. The dataset consists of brain volume calculated from 164 MRJ scans of preterm babies between 27 and 45 weeks GA gathered by the Developing Human Connectome Project [13,29]. We will have a detailed look at the algorithms for the segmentation of brain structures in Chap. 6. We will first describe the multivariate linear regression (Sect. 3.1). Next, we will show how we prevent overfitting using regularization (Sect. 3.2). Finally, we will look at nonlinear multivariate regression (Sect. 3.3).

# 3.1. Regression basics

In this section we will look at a basic regression technique called multivariate regression. First, we describe this regression model in detail (Sect. 3.1.1), and then explain how we train it (Sect. 3.1.2), and finally we investigate its performance in Sect. 3.1.3.

# 3.1.1 Multivariate linear regression

**Multivariate linear regression model** is defined as

```
$\hat{y} = w_0 + w_1x_1 + \dots + w_Dx_D,$
```

where $x = (x_1, \dots, x_D)^T$ is a feature vector, weight vector $w = (w_0, w_1, \dots, w_D)^T$ forms parameters of the model, and $\hat{y}$ is a predicted target value.

We wish to fit the model (find the weight vector **w**) to $N$ training samples $x_i = (X_{i1}, \dots, X_{iD})$ with associated target values $y_i$, where $i = 1, \dots, N$. This can be done by minimizing the loss function that measures a **sum of squared errors between**