
# A linear classifier

A linear classifier aims to find a `(p-1)`-dimensional hyperplane to separate a given collection of data points into two categories. Mathematically, suppose that each data point is represented by a `p`-dimensional feature vector `x = (x1, ..., xp) ∈ R^p` together with a label `y ∈ {-1, +1}`, representing to which category it belongs. A linear classifier is a hyperplane defined by the equation `f(x) = x^T ω + b = 0`, where `ω ∈ R^p` is the weight vector and `b ∈ R` is the bias. A data point `(xi, yi)` is classified as belonging to the category of “`+1`” if `f(xi) > 0`; and is classified as belonging to the category of “`-1`” if `f(xi) < 0`. The data point is correctly classified by this hyperplane if `f(xi) · yi > 0`; but it is misclassified if `f(xi) · yi < 0`.

[Figure 11.1](#c11.xhtml#c11-fig-0001) illustrates a dataset `{(xi1, xi2, yi)}_{i=1}^n` of two-dimensional feature vectors, which is linearly separated by the line:

[(11.1)](#c11.xhtml#R_c11-disp-0001) `f(x) = b + ω1x1 + ω2x2 = 0.`

Given its feature vector `x`, an observation is classified as the category `+1` (resp. `-1`) if it lies above (resp. below) this separating line of ([11.1](#c11.xhtml#c11-disp-0001)). In this chapter, we shall introduce two traditional binary linear classifiers, namely the `perceptron` and `support vector machine` (SVM).

![FIGURE 11.1 An example of a linear classifier for two-dimensional feature vectors with blue dots (resp. orange crosses) having a label plus 1 (resp. negative 1).](images/c11f001.png)

[**FIGURE 11.1**](#c11.xhtml#R_c11-fig-0001) An example of a linear classifier for two-dimensional feature vectors with blue dots (resp. orange crosses) having a label `+1` (resp. `-1`).

Both methods are processes of reducing the number of misclassified data. Intuitively, the algorithms improve the separating hyperplane by leaning it forward to the misclassified data in order to reduce their distances to the hyperplane. During the training, a `loss function` is chosen as a measure of misclassification. A greater value of the loss function indicates a lower accuracy in the prediction. Perceptron and SVM differ from the choice of the loss function. In addition, SVM can perform non-linear classification while the perceptron is mostly restricted to linear classification.

## 11.1 PERCEPTRON
