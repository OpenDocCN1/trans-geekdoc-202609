measure that computes how the regression model fits the real data. The obtained results are shown in Table 3.1. As it is shown, the learned model performs well on training data, but it does work on the test data. This situation happens frequently with machine learning, which is called overfitting. To cope with this challenge in machine learning, regularization term is added to the loss function, which controls the size of the parameter vector, and it prevents the parameter vector from becoming large. Hence, the loss function is changed as follows:

```
$L\left(\theta;\left\{x^{(i)}, y^{(i)}\right\\}_{i=1}^{N}\right)=\sum_{i=1}^{N}\|\left|y^{(i)}-h\left(x^{(i)}\right);\theta\rightrightrightright\|^2=\lambda\sum_{j}\left|\theta_{j}\right\|^q\quad(3.7)$
```

$\lambda$ is a regularization coefficient. If $q$ is set to one, then it is known as Lasso, and if $q$ is set to two, it is known as Ridge loss. The class **sklearn.linear_model.Ridge** and **sklearn.linear_model.Lasso**, create an object that fits a ridge regression and a lasso regression model on the training samples. The obtained results utilizing Ridge regression and Lasso regression on the ESOL dataset are shown in Table 3.1. As it is shown, both of these approaches prevent overfitting and perform better on the ESOL dataset compared to the simple linear regression approach.

To visualize the learned model, 1024 features of each sample are mapped to one dimension using the PCA algorithm. The obtained models on the ESOL dataset using three versions of the linear regression (simple linear regression, linear regression with Ridge regularization, and linear regression with Lasso regularization) are shown in Fig. 3.3. In Fig. 3.3, the red dots and purple dots show the test samples. Also, the blue line show the predicted line for the training sample.

# 3.3 Classification

In this section, the classification approaches are studied. Up to now, many classification algorithms are introduced; however, in this section, three main algorithms that perform well in the state-of-the-art are investigated: (1) logistic regression, (2) support vector machine (SVM), and (3) random forest. In the following, each of these algorithms is explained practically.

In this section, to evaluate the classification models, we have used the Tox21 dataset. This dataset is a multi-task dataset that contains 12 tasks (assays) where each task measures the human toxicity of a biological target.