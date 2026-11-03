
Prediction using the `init_model` can be done by using the `predict` function and passing the `train_dt` or the `test_dt` along with the parameter `s` which takes the `lambda` value at which the prediction is to be made. We will also pass the argument `type = response`, which will report the conditional probability for (`Y` = 1). We will convert this probability to `class` at a default cut-off 0.50. To report the `class` directly, we can pass `type = class`.

![](images/page275-02.png)![](images/page276-01.png)![](images/page277-01.png)

### 7.9.4 Classification Model – Logistic Regression Using Caret

We will use the `tuneLength` parameter of the `train` function to finetune the `ElasticNet` model. Refer [Section 7.7.3](#15_Chapter07.xhtml#sec7.7.3) for details about `tuneLength`.

When `tuneLength=10`, for each `alpha`, 10 `lambda` values will be evaluated. Thus, a total of 100 models will be built.

![](images/page277-02.png)![](images/page278-01.png)![](images/page279-01.png)

The model coefficients for the `ElasticNet` model are as follows:

![](images/page280-01.png)

The prediction on the `train_dt` are as follows:

![](images/page280-02.png)![](images/page281-01.png)

The prediction on the `test_dt` are as follows:

![](images/page281-02.png)![](images/page282-01.png)

We have seen the use of `glmnet` method to solve for regression as well as classification problems.

### Summary

In this chapter, we learnt

**1.** Model building by defining a cost function and using an optimization algorithm to minimize the cost function.

**2.** Implementing a GD algorithm to optimize the cost function for regression-based model.

**3.** Bias and variance trade-off and how to avoid model overfitting using regularization.

**4.** Advanced regression models like `LASSO`, `ridge`, and `ElasticNet` models.

**5.** Building a machine learning model (regression as well as classification) using the `glmnet` package.

**6.** Building a machine learning model (regression as well as classification) using the `caret` package.

### Exercise

The dataset `SAheart.data` is taken from the link given below:

[http://www-stat.stanford.edu/~tibs/ElemStatLearn/datasets/SAheart.data](http://www-stat.stanford.edu/~tibs/ElemStatLearn/datasets/SAheart.data)

The dataset `SAheartrateData.txt` contains records of males in a heart-disease high-risk region of the Western Cape, South Africa. There are roughly two controls per case of CHD. Many of the CHD-positive men have undergone blood pressure reduction treatment and other programs to reduce their risk factors after their CHD event. In some cases, the measurements were made after these treatments. These data are taken from a larger dataset, described in Rousseauw et al. (1983), *South African Medical Journal.* It is a tab-separated file (.csv) and contains the following columns:

• `sbp` – Systolic blood pressure

• `tobacco` – Cumulative tobacco (kg)

• `ldl` – Low density lipoprotein cholesterol

• `adipos ity`

• `famhist` – Family history of heart disease (Present, Absent)

• `typea` – type-A behavior

• `obesity`

• `alcohol` – Current alcohol consumption

• `age` – Age at onset

• `chd` – Response, coronary heart disease

The `chd` = 1 and `chd` = 0 will be referred to as `chd` and `no chd` cases, respectively.

**1.** Find out the number cases available in the dataset for `chd` and `no chd`. Plot the findings using a bar plot, where `X` is chd or no chd and `Y` gives the count of samples in each group.

**2.** Build a `lasso` logistic regression model using `caret`. Use `K`\-fold cross validation (`K` = 5) and ROC AUC score for reporting the best model.

**3.** Build a `ridge` logistic regression model using `caret` `glmnet` method. Use `K`\-fold cross validation (`K` = 5) and ROC AUC score for reporting the best model.

**4.** Build an `ElasticNet` logistic regression model using `caret`. Use `tuneLength` parameter of `train()` to fine tune the model and ROC AUC score for reporting the best model.

**5.** Build a `lasso` logistic regression model using `glmnet` package. Use K-fold cross validation (`K` = 5) to report the best model. Compare and describe the outcome of this model with the model obtained in Question 2.

**6.** Build a `ridge` logistic regression model using `glmnet` package. Use `K`\-fold cross validation (`K` = 5) to report the best model. Compare and describe the outcome of this model with the model obtained in Question 3.

**7.** Build an `ElasticNet` logistic regression model using `glmnet` package. Use `K`\-fold cross validation (`K` = 5) to report the best model. Compare and describe the outcome of this model with the model obtained in Question 4.

### Bibliography

**1.** Anon (2018), *“Glmnet: How to select Lambda and Alpha”*, Web Address: [https://stats.stackexchange.com/questions/357190/glmnet-how-to-select-lambda-and-alpha](https://stats.stackexchange.com/questions/357190/glmnet-how-to-select-lambda-and-alpha), accessed on 10 May 2021.

**2.** Friedman J and Hastie T, *“Regularisation Paths for Generalized Linear Models via Coordinate Descent”*, Web Address: [https://web.stanford.edu/~hastie/Papers/glmnet](https://web.stanford.edu/~hastie/Papers/glmnet), accessed on 21 January 2021.

**3.** Friedman J, Hastie T, and Tibshirani R (2008), “Regularisation Paths for Generalized Linear Models via Coordinate Descent”, *Journal of Statistical Software*, 33(1), 1–22.

**4.** Hastie T and Qian J (2014), *“Glmnet and Vignette”*, Web Address: [https://web.stanford.edu/~hastie/glmnet/glmnet_alpha.html](https://web.stanford.edu/~hastie/glmnet/glmnet_alpha.html), accessed on 21 January 2021.

**5.** Hastie T, Qian J and Kenneth Tay (2021), “An *Introduction to Glmnet”*, Web Address: [https://glmnet.stanford.edu/articles/glmnet.html](https://glmnet.stanford.edu/articles/glmnet.html), accessed on 10 May 2021.

**6.** Malviya D (2020), *“Machine Learning”*, Web Address: [https://www.kaggle.com/deepprabhamalviya/ml-day8](https://www.kaggle.com/deepprabhamalviya/ml-day8), accessed on 10 May 2021.

**7.** Mitchell T M (2006), “The Discipline of Machine Learning”, Carnegie Mellon University Report (CMU-ML-06-108), available at [https://www.cs.cmu.edu/~tom/pubs/MachineLearning.pdf](https://www.cs.cmu.edu/~tom/pubs/MachineLearning.pdf), accessed on 02 August 2021.

**8.** Pradhan M and Kumar U D (2019), *“Machine Learning Using Python”*, Wiley, Indian Institute of Management, Bangalore.

**9.** Simon N, Friedman J, and Hastie T (2013), “A Blockwise Descent Algorithm for Group-Penalised Multiresponse and Multinomial Regression, Web Address: [https://arxiv.org/abs/1311.6529](https://arxiv.org/abs/1311.6529), accessed on 10 May 2021.

**10.** Simon N, Friedman J, Hastie T, and Tibshirani T (2011), “Regularisation Paths for Cox’s Proportional Hazards Model via Coordinate Descent”, *Journal of Statistical Software*, 39(5), 1–13.

**11.** Tibshirani R, Bien J, Friedman J, Hastie T, Simon N, Taylor J, Tibshirani R J (2010), “Strong Rules for Discarding Predictors in Lasso-type Problems”, Journal of the Royal Statistical Society: Series B *(Statistical Methodology)*, 74(2), 245–266.

________________________

[¹](#15_Chapter07.xhtml#ch7-fn1)[https://web.stanford.edu/~hastie/glmnet/glmnet_alpha.html](https://web.stanford.edu/~hastie/glmnet/glmnet_alpha.html)

[²](#15_Chapter07.xhtml#ch7-fn2)[https://web.stanford.edu/~hastie/Papers/glmnet.pdf](https://web.stanford.edu/~hastie/Papers/glmnet.pdf)

## Ensemble Methods

## 8

*All know the way; few actually walk it.*

**—Bodhidharma**

LEARNING OBJECTIVES

After reading this chapter, you would be able to:

• Learn the mathematics behind ensemble methods.

• Learn to develop ensemble techniques such as `Random Forest`, `Gradient boosting machine` and `Xtreme boosting`.

• Learn to generate `variable importance` (`feature importance`) using ensemble methods.

• Understand `hyper-parameters` in machine learning algorithms and how to search for optimal `hyper-parameters`.

### 8.1 | Overview
