**Not all ML needs feature scaling:** You will see when we start building ML models, sometimes we have **feature scaling** and not something. Because some ML models automatically understand that features have lower values than the **others** and they will actually **fix that automatically by playing with the coefficients.**

Linear regression has coefficients for each of the features and for the features having high values values will just compensate with a **very low coefficient**.

So that we won't have to apply **Feature Scaling** for **linear regression**

But you will see that other models like **Logistic Regression** and **SVR** we have to apply **Feature Scaling**.

+   Bounding Range: Normalization has a bounding range in (0, 1). Unlike normalization, standardization does not have a bounding range, in many cases it may be in (-3, 3).

# **The Question - NORMALIZE OR STANDARDIZE?**

Normalization vs. standardization is an eternal question about machine learning newcomers. Let me elaborate on the answer in this section.

+   **Normalization** is good to use when you know that your data **does not follow** a *Gaussian distribution*. This can be useful in algorithms **that do not assume any distribution** of the data by **K-Nearest Neighbors** and **Neural Networks**

+   **Standardization** on the other hand, can be helpful in cases where the data follows a *Gaussian distribution*. However, it does not have to be **truly true**. Also, unlike **normalization, standardization** does not have a Bounding Range. So if you have outliers in your data it will be **affected by standardization.

However, at the end of the day, the choice of using normalization or standardization will depend on your project and the machine learning algorithm you are using. There is no fast rule to tell you which to normalize or standardize your data. You can always start by fitting your data to max, normalized and standardized data and compare the performance for best results.

```
from sklearn.preprocessing import StandardScaler
sc = StandardScaler()

Will automatically apply x_stand = (x-μ)/σ

old_x = sc.fit_transform(old_x)
Will scale our features.
```

# 1 Splitting the Dataset into the Training-set and Test-set

In your machine or model is going to learn from data to make predictions or other machine learning goals. So **Machine Learning** is going to learn on your data by setting up *some correlations* that there is in your *dataset* and imagine your machine learning model is learning too much data on the set that it's *too much to learn correlations* then it's not performance would be great.

We are building our *machine learning models* on a **data set** but then we have to test it on a **new set** which is going to **slightly different from the dataset** on which we build the **machine model**.

So we have to make **two sets of Training Sets** on we build the **ML model** and a **Test set** on we test the performance of this **ML model** and the mean on the test set should not be different from the training sets because this would make the **ML model** understand the correlations and didn't learn them by heart so that you can **adapt to new sets and new situations**."

Learn train to apply **data (80/20)** on this **Test set** by setting up correlations between the *independent variables* and the *dependent variable* of the **Test Set**. And then once the machine learning model understands the correlations between *independent variables* and the *dependent variable* we will test **ML model** that it can apply the correlations based on the **training set** on the **test set**. That means that we use **ML model** can predict about the *dependent variable* on the *test dataset* (which is 20% in our case).

If ML learn from 100% from the data it doesn't understand well the logic and won be able to make good predictions. That is **overfitting** we will be talking about in further details the **regression section** and how we will learn to use **REGULARISATION** techniques to prevent this.