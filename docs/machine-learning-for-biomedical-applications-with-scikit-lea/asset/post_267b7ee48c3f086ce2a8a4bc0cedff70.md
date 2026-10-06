
## Classification 91

![](img/d219b4c20ff50f4b97845dec7a9acecb_109_0.png)

**Figure 4.4** Conditional probabilities for heart failure (label 1). Yellow and green colors represent high and low probabilities, respectively. The white star shows a sample with high confidence (left) and low confidence (right).

For the test data, we can obtain probabilistic predictions for all classes

```python
p = model.predict_proba(X_test)
```

The predicted probabilities for label zero can be obtained as p[:,0] and for label 1 as p[:,1].

In Fig. 4.4 we plotted conditional probabilities for class 1 (heart failure) predicted from two features (EF and GLS). Yellow color represents high probabilities (close to 1) and green color represent low probabilities (close to zero). The two plots show different samples, plotted by a white star, with a predicted label 1 (heart failure). However, the confidence in the predicted label is different. The first sample lies in the area of high confidence for heart failure (probability 0.99), while the second one lies close to the decision boundary (probability 0.55). Clearly, we would be more certain that the diagnosis of heart failure for the first case is correct.

## 4.1.4 Multi-label linear classification

In many applications we wish to assign our samples to more than two classes. For example, we would like to diagnose not only whether a patient has heart failure but how severe it is. We therefore have three classes: label 0 for healthy patients, label 1 for cases of mild heart failure, and label 2 for cases of severe heart failure, as described at the beginning of this chapter. We can generalize binary classifiers to multi-classifiers by fitting multiple decision functions. For each class k we have a linear decision function $h_k(\mathbf{x})$ with parameter vector $\mathbf{w}_k$ that separates class $k$ from the rest of the classes.

**A multinomial logistic regression** model generalizes logistic regression to multiple classes. To predict a label for sample $\mathbf{x}$, we first evaluate the decision functions for

# Machine Learning for Biomedical Applications

![](img/d219b4c20ff50f4b97845dec7a9acecb_110_0.png)

**Figure 4.5** Multi-label classification of heart failure. Left: separation of the feature space into three regions: dark green for healthy (label 0), light green for mild heart failure (label 1), and yellow for severe heart failure (label 2). Right: Conditional probabilities for mild heart failure (label 1). Yellow and green colors represent high and low probability, respectively.

each class $k$ (that we have defined $x_0 = 1$, in Chap. 3):

```python
$h_k(\mathbf{x}) = \mathbf{w}_k^T\mathbf{x}$.
```

Outputs of the decision functions are then converted to conditional probabilities $p_k(\mathbf{x}) = p(y=k|\mathbf{x})$ by passing through the *softmax* function

```python
$p_k(\mathbf{x}) = \frac{e^{h_k(\mathbf{x})}}{\sum_{j=1}^K e^{h_j(\mathbf{x})}}$
```

Finally, we assign the class with highest probability $p_k(\mathbf{x})$ to the sample $x$:

```python
$\hat{y} = \arg\max_k p_k(\mathbf{x}).$.
```

The parameters $\mathbf{w}_k$ for each class-dependent decision function are found by minimizing the *cross-entropy*

```python
$- \sum_{i=1}^N \sum_{k=1}^K y_{ik} \ln p_k(\mathbf{x}_i)
```

where $y_{ik}$ is 1 if label $y_i = k$ and otherwise.

The classification of patients into healthy or mild or severe heart-failure cases using features EF and GLS is shown in Fig. 4.5. On the left, we can see separation of the feature space into three regions corresponding to the three classes of patients. The plot on the right displays the predicted probability for patients with mild heart failure. Multinomial logistic regression is implemented in scikit-learn using

# LogisticRegression(multi_class="multinomial")

There is no need to set the parameter since scikit-learn will automatically detect when we have more than two labels. We will now demonstrate how we fit and plot the logistic regression model to obtain results presented in Fig. 4.5. We can select and fit the model using a standard scikit-learn API

```python
model = LogisticRegression()
model.fit(X,y)
```

To plot the classification results, we will predict the labels for the whole 2D feature space. First, we sample the relevant ranges of values for both features

```python
import numpy as np
x1 = np.linspace(-2.5, 2, 1000)
x2 = np.linspace(-3.3, 3.5, 1000)
```

Next, we combine the individual feature vectors into matrices of 2D coordinates, with sizes 1000 × 1000, suitable for plotting

```python
x1, x2 = np.meshgrid(x1,x2.T)
```

However, scikit-learn requires a matrix in shape number of samples × number of features, which is 1,000 × 2 in our case. We will achieve this by flattening x1 and x2 into 1D vectors and concatenating to form a feature matrix

```python
Feature_space = np.c_[x1.ravel(),x2.ravel()]
```

Now, we are to predict the labels for the sampled 2D feature space

```python
y_pred = model.predict(Feature_space)
```

Before we can plot these, we need to reshape them back to a 2D grid

```python
y_pred = y_pred.reshape(x1.shape)
```

We will plot the result using a matplotlib function contour that takes the coordinates and the intensity (color) to be plotted as input arguments

```python
import matplotlib.pyplot as plt
plt.contour(x1, x2, y_pred, cmap='summer')
```

The parameter cmap determines the colormap for the Final. Finally, we plot the data on and annotate the plot

```python
plt.plot(X[y==0,0],X[y==0,1],'bo')
plt.plot(X[y==1,0],X[y==1,1],'rd')
plt.plot(X[y==2,0],X[y==2,1],'g^')
plt.xlabel('Ejection Fraction')
```

```python
plt.ylabel('Global Longitudinal Strain')
plt.legend(['Healthy','Mild Heart Failure',
'Severe Heart Failure'])
plt.title('Predicted labels')
```

To plot the probability for the class 1, we use the following code:

```python
p = model.predict_proba(feature_space)
p = p[:,1].reshape(x1.shape)
plt.contour(x1, x2, cmap = 'summer')
```

## 4.1.5 Evaluating performance of classifiers

### Accuracy

We have already seen in Sect. 2.2.2 that we can measure the performance of classifiers using the **accuracy** score, which is the proportion of the correctly classified samples. Accuracy works for both binary and multi-label classifiers and is the default classification performance measure in scikit-learn.

We usually measure the accuracy error on the test set that has been excluded from the training, or using cross-validation on the training set, even though we can also check the accuracy on the whole set.

## 4.1.5 Evaluating performance of classifiers

### Sensitivity and specificity

The problem with the accuracy score for unbalanced datasets can be resolved by calculating the proportion of correctly labeled positive and negative samples. Sensitivity, also called recall, is the proportion of correctly labeled positive samples (e.g., samples with label 1). In scikit-learn it can be evaluated using the recall_score

