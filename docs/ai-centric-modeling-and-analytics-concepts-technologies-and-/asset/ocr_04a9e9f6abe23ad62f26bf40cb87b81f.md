The correlation coefficient (ρ) is a metric that assesses how closely the movements of two different variables are related, with range of potential values from −1.0 to 1.0. Therefore, the numbers cannot be more than 1.0 or lower than −1.0.

A perfect negative correlation is represented by a correlation of −1.0, and a perfect positive correlation is represented by a correlation of 1.0. A positive link exists between the status of a website and any of the 112 attributes if the correlation coefficient between them is greater than zero.

However, a negative association exists if the value is less than zero. If the value is zero, then there is no correlation between the two variables. Before determining the correlation, the covariance of the two variables must first be calculated, and hence, the standard deviation of each variable.

By dividing the covariance by the sum of the standard deviations of the two variables, the correlation coefficient was computed as Equation 17.5:

```
$$\mathrm{Correlation}=P=\frac{\mathrm{COV}(x,y)}{\sigma_X\sigma_Y}\tag{17.5}$$
```

where X and Y are the attribute and ground truth, respectively.

The IQR and correlation evaluation analysis, through box and heat map plots, were implemented using the object-oriented Python programming libraries of Seaborn, Matplotlib, and DataFrame in a Jupyter notebook.

The IG computation for feature selection was implemented using the Orange data mining toolkit (Borondics et al., 2020) with Python libraries. The result of feature selection determines the dataset features that will be used to train the algorithm for the next phase of the conceptual framework.

# 17.3.3 Predictive Analytics of Uniform Resource Locators

This subsection describes the supervised machine learning approach of the conceptual framework for detecting phishing in website URLs.

The machine learning algorithms to be trained with the prominent parameters emerging from the IG analysis are presented and discussed.

The training set, which consists of the prominent parameters returned by IG, is used to train the learner algorithms of NB and a neural network.

Bayes theorem and strong (naive) independence assumptions between the features serve as the foundation for the collection of simple probabilistic classifiers known as NB (Olaleye et al., 2023). The mathematical model of the supervised NB learning is presented as follows.

# 17.3.3.1 Naive Bayes Mathematical Model

The NB algorithm assumes that all independent variables are conditionally independent given the response variable.

+   - **Y**: the target variable (1 if the URL is phishing; 0 if otherwise)
+   - **X1, X2, …, X11**: the URL predictive attributes to approximate the target variable **Y**