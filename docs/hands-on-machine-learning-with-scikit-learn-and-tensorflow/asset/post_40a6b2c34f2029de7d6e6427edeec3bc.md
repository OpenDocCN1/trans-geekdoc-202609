
## Select a Performance Measure

Your next step is to select a performance measure. A typical performance measure for regression problems is the Root Mean Square Error (RMSE). It gives an idea of how much error the system typically makes in its predictions, with a higher weight for large errors. Equation 2-1 shows the mathematical formula to compute the RMSE.

Equation 2-1. Root Mean Square Error (RMSE)

```
$RMSE(\mathbf{X}, h) = \sqrt{\frac{1}{m} \sum_{i=1}^{m}(h(x^{(i)})-y^{(i)})^2}$
```

## # Notations

This equation introduces several very common Machine Learning notations that we will use throughout this book:

- $m$ is the number of instances in the dataset you are measuring the RMSE on.
- For example, if you are evaluating the RMSE on a validation set of 2,000 districts, then $m=2,000$.
- $x^{(0)}$ is a vector of all the feature values (excluding the label) of the $i^{th}$ instance of the dataset, and $y^{(0)}$ is its label (the desired output value for that instance).
- For example, if the first district in the dataset is located at longitude $-118.29^{\circ}$, latitude $33.91^{\circ}$, and it has 1,416 inhabitants with a median income of $38,372$, and the median house value is $156,400$ (ignoring the other features for now),

```
$x^{(1)} = \begin{pmatrix} -118.29 & 33.91 & 1,416 \end{pmatrix}$
```

and:
$y^{(1)} = 156, 400$

- $X$ is a matrix containing all the feature values (excluding labels) of all instances in the dataset. There is one row per instance and the $i^{th}$ row is equal to the transpose of $x^{(i)}$, noted $(x^{(i)})^T$.
- For example, if the first district is just described, then the matrix $X$ looks like:

```
$X = \begin{pmatrix} (x^{(1)})^T & (x^{(2)})^T & \vdots & (x^{(1999)})^T & (x^{(2000)})^T \end{pmatrix} = \begin{pmatrix} -118.29 & 33.91 & 1,416 & 156,400 \\ \vdots & \vdots & \vdots & \vdots \end{pmatrix}$
```

- $h$ is your system's prediction function, also called a hypothesis. When your system is given an instance feature vector $x^0$, it outputs a predicted value $y^0 = h(x^0)$ for instance $\hat{y}$ is pronounced "y-hat".
- For example, if your system predicts the median housing price in the first district is 158,400, then $y^0 = h(x^0) = 158,400$. The prediction error for this district is $\hat{y} - y^0 = 2,000$.
- RMSE(X,h) is the cost function measured on the set of examples using italic font for scalar values (such as $m$ or $y^0$) and function names (such as $h$), lowercase bold for vectors (such as $x^0$), and uppercase bold font for matrices (such as $X$).

We use italic font for scalar values (such as $m$ or $y^0$) and function names (such as $h$), lowercase bold for vectors (such as $x^0$), and uppercase bold font for matrices (such as $X$).

Even though the RMSE is generally the preferred performance for regression tasks, in some contexts you may prefer another function. For example, suppose there are many outlier districts. In that case, you may consider the Mean Absolute Error (also called the Average Absolute Deviation; see Equation 2-2):

## Equation 2-2. Mean Absolute Error

```
MAE(X,h) = \sum_{i=1}^{m} |h(x^i) - y^i|
```

The RMSE and the MAE are used to measure the distance between two vectors: the vector of predictions and the vector of target values. Various distance measures, or norms, are possible:

- Computing the root of a sum of squares (RMSE) corresponds to the Euclidean norm: it is the distance you are from unbiased. It is also called the $l_2$ norm, denoted $\|\cdot\|_2$ (or just $\|\cdot\|_2$).
- Computing the sum of absolutes (MAE) corresponds to the $l_1$ norm, denoted $\|\cdot\|_1$. It is called the Manhattan norm because it measures the distance between two points in a city if you can only travel along orthogonal city blocks.
- More generally, the $l_k$ norm of a vector containing $n$ elements is defined as $\|v\|_k = (|v^0|^k + |v^1|^k + ... + |v^{n-1}|^k)^{1/k}$. $l_0$ gives the number of non-zero elements in the vector, and $l_{\infty}$ gives the maximum absolute value in the vector.
- The higher the norm index, the more it focuses on large values and neglects small ones. This is why RMSE is more sensitive to outliers than the MAE. But outliers are exponentially rare (like in a bell-shaped curve), the RMSE performs very well and is generally preferred.

## Check Assumptions

Lastly, it is good practice to list your assumptions. We will make the following assumptions about the data:

- We assume that the data is independent and identically distributed (i.i.d.).
- We assume that the data is stationary.
- We assume that the relationship between the features and the target is linear.
- We assume that there are no significant outliers in the data.

If these assumptions do not hold, you may need to use more robust methods or transform the data.
