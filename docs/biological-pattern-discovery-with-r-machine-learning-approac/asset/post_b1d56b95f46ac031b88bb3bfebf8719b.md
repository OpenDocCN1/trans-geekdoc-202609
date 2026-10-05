
## Biological Pattern Discovery with R

dependent variable (class) and independent variables (expressed by the dot),

```
my.lda=lda(class ~,x)
```

In the above code, my.lda is a LDA object and is composed of eight components, namely $prior, $counts, $means, $lev, $svd, $N, $call, $terms and $scaling are the main components for further analysis.

Figure 3.3 shows two data sets with two clusters but different distributions of data points from two clusters. Figure 3.3(a) shows a data set with an even data distribution across two classes but Figure 3.3(b) shows a data set with an odd data distribution across two classes. Two classes had different centres, but had the same covariance matrix shown below.

> $S_W = \begin{pmatrix} 4 & 2 \\ 2 & 4 \end{pmatrix}$

![](img/c3caa39b5c0f40fb2a44f2ab6e940f78_104_0.png)

Fig. 3.3. Two data sets for illustrating LDA and the Bayes rule work for data sets with even or odd data number. Both classes (the triangles and the crosses) were composed of 200 data points. (a) The triangle class was composed of 200 data points, but the cross class was composed of 2000 data points.

Figure 3.4 shows the densities of the LDA predictions ($\hat{Y}_A$ and $\hat{Y}_B$) for two data sets shown in Figure 3.3. Because two clusters had an even data distribution across two classes (both have 200 data points) in the data set shown in Figure 3.3(a), a *a priori* probabilities were identical, i.e., $\pi_{Triangle} = \pi_{Cross} = 0.5$. The two density functions of two classes

## Protease Cleavage Pattern Discovery

therefore displayed similar shapes and similar heights – as shown in Figure 3.4(a). However, the numbers of the data points from two classes were very different in Figure 3.3(b). The proportion of the cross-class data points was about 90.9%. Therefore, two posterior probabilities derived from the LDA model constructed for this data set were very different, i.e., $\pi_{Triangle} = 0.09$ and $\pi_{Cross}=0.91$. The shapes and the heights of two density functions shown in Figure 3.4(b) therefore demonstrated a significant difference.

![](img/c3caa39b5c0f40fb2a44f2ab6e940f78_105_0.png)

Figure 3.4. (a) The density of estimated based on the LDA predictions ($\hat{x}_A$) for data shown in Figure 3.3(a). (b) The density of estimated based on the LDA predictions ($\hat{y}_A$) for the data shown in Figure 3.3(b).

![](img/c3caa39b5c0f40fb2a44f2ab6e940f78_105_1.png)

Figure 3.5. The posterior probabilities estimated by LDA for two data sets shown in Figure 3.3. The solid line stands for the posterior probability curve for the triangle class and the dotted line stands for the posterior probability curve for the cross class. (a) The posterior probability curves for the data shown in Figure 3.3(a). (b) The posterior probability curves for the data shown in Figure 3.3(b).

Figure 3.5 shows the posterior probability distributions estimated by the Bayes rule for two LDA models for these two data sets. The major difference was the location of the crossover point between two posterior probability curves. In Figure 3.5(a), two posterior probability curves were crossed in the center (zero) because two classes of data points had the same number. In Figure 3.5(b), the crossover point of two posterior probabilities deviated from zero towards the left side because the data set had odd data distribution across two classes.

To evaluate the performance such as the discrimination power of a constructed LDA model, new data should be inputted into a constructed LDA model to examine whether the outputs of a constructed LDA model are as expected. When inputting new data to a constructed LDA model, the outputs of the LDA model are called the predictions. To make prediction based on a constructed LDA model for new data, the predict function is called,

```
my.output=predict(my.lda, newdata, ...)
```

The main components of my.output include $class, $posterior and $x. $x is composed of the predictions ($\hat{Y}$) which are the mapped data on the optimised projection direction ($\hat{W}$) from the independent variables. The posterior probabilities are saved in a matrix of two columns for two classes and is named as $posterior. Its first column is composed of the posterior probabilities for the first class and the second column is composed of the posterior probabilities for the second class of the data set for which the LDA model is constructed. If the first posterior probability in a row is greater than the second posterior probability in the same row, the data point at that row is assigned a label of the first class. Otherwise, it is assigned a label of the second class. Based on a default threshold (0.5) for using the posterior probabilities for decision-making, the posterior probability $posterior$ is converted to the predicted binary variable which is binary and is named as $class in the output object (my.output) of the predict function. For a row, if the first posterior probability is greater than the second, $class is one.

### The other discriminant algorithms

The LDA model is a linear model because the decision boundary is a linear hyperplane. However, when the covariance matrices of the classes are different, the decision boundary is no longer linear. In such cases, a quadratic decision boundary should be used instead of a linear one.

### The quadratic discriminant analysis

It has been discussed above that two classes have an identical covariance matrix, i.e., $\Sigma_1 = \Sigma_2$. This is only valid when the difference between two classes is insignificant. When this difference becomes significant, the use of an identical covariance matrix may no longer be a good approach. To deal with significantly different covariance matrices across two classes, the quadratic discriminant analysis (QDA) is an alternative [Tharat, 2016]. The algorithm is also called generalised discriminant analysis (GDA)[Cover, 1965]. It extends LDA in the format shown below,

```
$y = \mathbf{x}^T W \mathbf{x} + \mathbf{\beta}^T \mathbf{x} + c$
```

In a QDA model, two covariance matrices are allowed to be different, i.e., $\Sigma_1 \neq \Sigma_2$. The R function for constructing a QDA model is qda. Because of the use of different covariance matrices for two classes, the discrimination boundary between two classes will not be a straight line. Figure 3.6 shows a data set with two classes. The cross class has a larger variance than the triangle class.

Figure 3.7(a) is the use of the R package to show the LDA discrimination boundary for the data shown in Figure 3.6. It can be seen that the LDA discrimination boundary was a straight line. The use of this boundary of this discriminant analysis model caused 5 misclassified data points. Figure 3.7(b) shows the QDA discrimination boundary for the data shown in Figure 3.6 as well. It can be seen that the QDA was bounded. The bending pushed two sides of the boundary towards the triangle class with a smaller variance. In this way, the cross class with a greater variance occupied more space than the triangle class which had a smaller variance. In other words, the bended boundary shows a quadratic curve. The use of this bended boundary for the data set caused two misclassified data points. The reason that the QDA model outperformed the LDA model for this data set was because the QDA model employed different covariance matrices for two classes with different variances for this data set.

![](img/c3caa39b5c0f40fb2a44f2ab6e940f78_108_0.png)

Fig. 3.6. A data set with different covariance matrices in two classes.

![](img/c3caa39b5c0f40fb2a44f2ab6e940f78_108_1.png)

Fig. 3.7. (a) The LDA model for data shown in Figure 3.6. (b) The QDA model for data shown in Figure 3.6.
