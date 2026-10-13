
| --- | --- |

| \[1\] || Yan X., Su X.G.. , . Linear regression analysis: Theory and computing.. Singapore, Singapore: World Scientific Publishing; 2009. |

| \[2\] || Montgomery D.C., Peck E.A., Vining G.G.. , . Introduction to Linear Regression Analysis.. 6th ed. Standards Information Network; 2021. |

| \[3\] || Casson R.J., Farmer L.D.M.. Understanding and checking the assumptions of linear regression: a primer for medical researchers., *Clin. Exp. Ophthalmol..* **2014;** 42(6): 590-596.  

\[[CrossRef](http://dx.doi.org/10.1111/ceo.12358)\] \[[PubMed](http://www.ncbi.nlm.nih.gov/pubmed/24801277)\] |

| \[4\] || Kutner M.H., Neter J., Nachtsheim C.J., Wasserman W.. , . Applied linear statistical models (int’l ed). 4th ed. Maidenhead; England: 2004. |

| \[5\] || Wang Z., Irfan S.A., Teoh C., Bhoyar P.H.. , . Regularization” in Numerical Machine Learning.. Bentham Science; 2023. |

| \[6\] || Wang Z., Irfan S.A., Teoh C., Bhoyar P.H.. , . Logistic Regression” in Numerical Machine Learning.. Bentham Science; 2023. |

# Regularization

**Zhiyuan Wang**, **Sayed Ameenuddin Irfan**, **Christopher Teoh**, **Priyanka Hriday Bhoyar**  

## Abstract

This chapter delves into L1 and L2 regularization techniques within the context of linear regression, focusing on minimizing overfitting risks while maintaining a concise presentation of mathematical theories. We explore these techniques through a concrete numerical example with a small dataset for predicting house sale prices, providing a step-by-step walkthrough of the process. To further enhance comprehension, we supply sample codes and draw comparisons with the Lasso and Ridge models implemented in the `scikit-learn` library. By the end of this chapter, readers will acquire a well-rounded understanding of L1 and L2 regularization in the context of linear regression, their implications on model implementation and performance, and be equipped with the knowledge to apply these methods in practical use.

**Keywords:** L1 Regularization, L2 Regularization, Linear Regression, Numerical Example, Small Dataset, Housing Price Prediction, Scikit-Learn, Lasso, Ridge.  

## 3.1. INTRODUCTION TO L1 AND L2 REGULARIZATION

Regularization is the process of adding an extra penalty to a more complicated model with larger values of weights to prevent overfitting. A problem known as overfitting happens when a machine learning model is made specifically for training datasets and is unable to generalize well to previously unseen datasets. Introducing regularization techniques into machine learning models is essential for achieving better generalization and improved performance on new data. By penalizing overly complex models, regularization helps lead to more accurate and stable predictions. Some popular regularization methods include L1 and L2 regularization, which differ in the way they penalize the model's complexity. Regularization has proven to be a critical component in the development of robust and reliable models, particularly when dealing with high-dimensional data or noisy datasets. It enables practitioners to build more efficient models, capable of adapting to new and diverse situations while reducing the risk of overfitting and maintaining interpretability.

This chapter focuses on L1 and L2 regularization, which are demonstrated in detail by making necessary changes from the original linear regression model discussed in Chapter 2. Bear in mind, however, that L1 and L2 regularization can also be applied to other machine learning models (e.g., logistic regression), as well as deep learning neural networks.

The names of L1 and L2 regularization come from the corresponding L1 and L2 norms of the weight vector `W`.

The L1 norm is defined as:

![](Images/9789815136982-C3-E1.jpg)

A linear regression model with the L1 regularization is known as Lasso (least absolute shrinkage and selection operator) regression \[[1](#9789815136982-C3.html#r1), [2](#9789815136982-C3.html#r2)\], whereas a linear regression model with the L2 regularization is called Ridge regression \[[3](#9789815136982-C3.html#r3), [4](#9789815136982-C3.html#r4)\].

## 3.2. MATHEMATICS OF L1 REGULARIZATION FOR LINEAR REGRESSION

The general equation of linear regression if having more than one independent variable `X` (i.e., input feature) is as follows:

![](Images/9789815136982-C3-E2.jpg)

The goal of linear regression is to find the best-fit linear equation model that maps the relationship between input `X` and output `Y`, in the form of Equation (3.1) with the optimal weights and bias, which produces the least error (synonymously known as loss in machine learning) between the known true output `Y` values and predicted output `Y` values by the model.

![](Images/9789815136982-C3-E3.jpg)

![](Images/9789815136982-C3-F1.jpg)**Fig. (3.1))**  

Illustration of notations using an exemplary training dataset. 

![](Images/9789815136982-C3-E4.jpg)

![](Images/9789815136982-C3-E5.jpg)

![](Images/9789815136982-C3-E6.jpg)

Next, the Gradient Descent optimization algorithm is used to find the optimal bias and weights by iteratively tweaking their values a tiny bit at a time in the direction of reducing the loss. In order to carry out the optimization, we first need to find the partial derivative of the mean loss (`L`) with respect to the bias and weights, namely, `∂L/∂b` and `∂L/∂wj`, denoting the contribution to the mean loss by the bias and each of the weights. This can be done by applying the chain rule, shown in Equations (3.4) to (3.9).

![](Images/9789815136982-C3-E7.jpg)

![](Images/9789815136982-C3-E8.jpg)

It is worth noting that the mathematical notations and Python codes in this chapter are somewhat similar to those in Chapters 2 and 4 of this book \[[5](#9789815136982-C3.html#r5), [6](#9789815136982-C3.html#r6)\]. However, the focuses of Chapters 2 and 4 are on linear regression and logistic regression, respectively, whereas the focus of this chapter is on regularization.

## 3.3. NUMERICAL EXAMPLE OF L1 REGULARIZATION FOR LINEAR REGRESSION

Same as the original linear regression discussed in Chapter 2, suppose we have a small training dataset presented in (Table **3.1**) with only 3 samples (i.e., `m=3`), which pertains to the sale price of houses in millions of dollars (abbreviated as `sale_price_million`) based on 2 input features (i.e., `n=2`), namely, the size of a house in square feet (abbreviated as `size_sqft`) and the total number of bedrooms in the house (abbreviated as `num_bedrooms`). In other words, for this example, `X` is `size_sqft` and `num_bedrooms`, and `Y` is `sale_price_million`. Our task is to build a best-fit linear regression model that maps the `X` and `Y` under L1 regularization.

Table 3.1 **The small dataset for linear regression under regularization.**  

| **size_sqft** || **num_bedrooms** || **sale_price_million** |

| --- | --- | --- |

| 1600 || 5 || 2.28 |

| --- | --- | --- |

| 1200 || 4 || 1.5 |

| 740 || 2 || 0.88 |

Next, normalize the feature values (i.e., the values of `size_sqft` and `num_bedrooms` columns) to bring them to a common scale between 0 and 1, using Max-min normalization, as shown in Equation (3.12). Without normalization, some feature(s) might dominate the machine learning process.

![](Images/9789815136982-C3-E9.jpg)

The maximum and minimum of `size_sqft` are 1600 and 740, respectively. Likewise, the maximum and minimum of `num_bedrooms` are 5 and 2, respectively. The output values (i.e., `sale_price_million`) are left as they are, without any normalization. The small dataset after Max-min normalization on the features is presented in (Table **3.2**).

Table 3.2 **The small dataset after Max-min normalization for linear regression under regularization.**  

| **size_sqft** || **num_bedrooms** || **sale_price_million** |

| --- | --- | --- |

| 1 || 1 || 2.28 |

| --- | --- | --- |

| 0.5349 || 0.6667 || 1.5 |

| 0 || 0 || 0.88 |

![](Images/9789815136982-C3-E10.jpg)
