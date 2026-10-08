# Optimizing Ti-6Al-4V Milling Under MQL Conditions

SVR constructed the regression models that form the foundation for the optimization challenge using NSGA II. The feasible optimal milling parameters (Pareto Set), determined by NSGA II, were then prioritized through TOPSIS to identify the best parameter set.

# 3.3.1 SUPPORT VECTOR REGRESSION

Support vector machine (SVM) stands out as a supervised learning method extensively applied in machine learning for classification purposes. Its primary aim is to identify the optimal hyperplane, which might be linear or nonlinear, or the space, that separates data into two separate classes. This objective is accomplished by strategically placing the hyperplane to maximize the margin, or the space, between the hyperplane and the closest data point from each class. Figures 3.3 and 3.4 illustrate the configuration of a hyperplane along with its associated margin. Given a hyperplane equation $w \cdot x + b = 0$, the core objective of SVM is to calculate $w$ and $b$ to ensure the largest margin between the two classes.

The SVM algorithm, well-known for its proficiency in classification tasks, extends its capabilities to regression problems via its variant known as support vector regression. SVR aims to construct a function that precisely represents the relationship between input features and a continuous outcome variable, focusing particularly on reducing the discrepancies in predictions. While SVR is grounded in the same underlying principles as SVM, it is specifically adapted to cater to regression contexts.

At the heart of SVR is a unique loss function introduced by Vapnik (Cortes and Vapnik, 1995; Vapnik, 2000, 1998). This loss function is characterized by its tolerance for errors within a specified epsilon range for points that are not close to the true value. In essence, the function assigns zero error to all training set points that fall within this range of epsilon.

![](bbox=[0.225, 0.635, 0.775, 0.883])

FIGURE 3.3 The hyperplane and the margin.