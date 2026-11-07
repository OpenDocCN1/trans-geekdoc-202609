
* **Deep Learning**: It is an advanced machine learning development or technique based on neural networks, which is capable of learning from enormous volumes of data.
* **Classification**: It falls under the category of supervised learning. It deals with discrete data and predicts the class to which the data belong. A simple example is categorizing emails as “spam” and “not spam.” A classification problem can be either binary or multiclass.
* **Regression**: It falls under the category of supervised learning and provides predictions based on input features that are continuous values, for example, predicting the price of a house based on its features such as the plot size, location, etc.
* **Feature Extraction**: The process of extracting features from the given raw dataset necessary for building machine learning algorithms.
* **Test Set**: A subclass of the given dataset required to test the trained model. This set must represent the entire population and be large enough to yield meaningful results.
* **Training Set**: A subclass of the given dataset required to train the model.
* **Model Building**: The process of building a model using machine learning algorithm to solve the given problem.
* **Model Deployment**: The model is finalized based on multiple criteria and performance measures that include accuracy, costs, and performance speed. This is the final stage that involves developing strategies for deploying the model.

## 1.3 Distance-Based Signal Classification, Nearest Neighbor Classifier, and Hilbert Space

### 1.3.1 Distance-Based Signal Classification

Various real-world applications require machine learning algorithms to classify signals or objects. Identifying input data patterns is fundamental for such classification applications, and choosing the right distance metric is critical to make informed decisions. Good distance metrics can be used to enhance model accuracy and performance of machine learning algorithms. This section focuses on various distance metrics and how they contribute to SPML. Few key definitions are fundamental to distance metrics as that of metric space, normed linear space, and inner product space. From the definitions, you will notice that normed linear spaces and inner product spaces are just types of metric spaces that belong to the same family.

#### 1.3.1.1 Metric Space

Metric space is simply a collection of objects (e.g., numbers and matrices), and a metric or distance function is a function that defines a distance between each pair of point elements of a set [[17](#ch01.xhtml#r1_17)]. Some applications in SPML require the use of functions for measurement of distances in arbitrary spaces, and distance metrics belong to this class of functions. An arbitrary space can be any space including vector spaces. The simplest example of a metric space is a number line with real numbers, and the associated metric is ∥`a`−`b`∥, where `a`, `b` ∈ ℝ.

Let us consider `Z` as an arbitrary space; `a` and `b` are two points in this space, and `d` is a distance function. The distance function `d` is a distance metric if it satisfies the following four conditions:
1. The distance `d(a, b)` ≥ 0
2. The distance `d(a, b)` = 0 only if `a` = `b` (implies that distance from a point to itself is zero).
3. The distances must be symmetric which means `d(a, b)` = `d(b, a)`
4. It must satisfy the triangle inequality property where `d(a, k)` ≤ `d(a, b)` + `d(b, k)`

#### 1.3.1.2 Normed Linear Space

A complex normed linear space is a linear space with a function ∥ . ∥:`L`→ℝ is called a norm called a norm [[17](#ch01.xhtml#r1_17)]. The Euclidean distance and `l[p]` norms fall under this category, and norms are used to measure distance as well as lengths in vector spaces. Let us consider a Euclidean plane ℝ^(`n`) with `n` dimensions. The Euclidean distance or `l[2]` distance (where `p` = 2) is the most commonly used distance metric. It is simply the distance measured between any two points in this plane using the Pythagorean theorem. For example, the Euclidean distance between two points `a` and `b` shown in [Figure 1.5](#ch01.xhtml#f1_5) can be calculated using Equations (1.10a).

![FIGURE 1.5 Representation of Euclidean distance.](images/Fig01_05.jpg)

[**FIGURE 1.5**](#ch01.xhtml#f1_5b) Representation of Euclidean distance.

$$l_{2} = \\left\\| {a - b} \\right\\|_{2} = \\sqrt{\\sum\\limits_{i = 1}^{n}\\left( {a_{i} - \\left. b_{i~} \\right)} \\right.^{2}}$$
(1.10a)

This is a two-dimensional Euclidean space, and `a[i]` and `b[i]` are the variables of vectors `a` and `b` in this space, i.e., `a` = (`a[1]`, `a[2]`, `a[3]`,…) and `b` = (`b[1]`, `b[2]`, `b[3]`,…).

Therefore, `a[i]`− `b[i]` = (`a[1]`− `b[1]`) + (`a[2]`− `b[2]`) + … + (`a[n]`− `b[n]`).

For example, the Euclidean distance between two vectors, let us say points `a` (1, 2) and `b` (3, 5) in the ℝ² plane can be calculated as follows:

$$l_{2} = \\left\\| {a - b} \\right\\|_{2} = \\sqrt{\\left( {a_{i} - \\left. b_{i~} \\right)} \\right.^{2}} = \\sqrt{\\left( {3 - 1)} \\right.^{2} + \\left( {5 - 2)} \\right.^{2}} = \\sqrt{13}$$
(1.10b)

So, $\sqrt{13}$ is the Euclidean distance between `a` and `b` in two dimensions.

While Euclidean distance is sufficient to capture distance measurements in a given space, some applications require measurement of larger distances, and `l[p]` norms are used for such applications. `l[p]` norm where `p` ≥ 1 is represented as in Equation (1.11).

$$l_{p} = \\left\\| {a - b} \\right\\|_{p} = \\left( {\\sum\\limits_{i = 1}^{n}\\left| {a_{i} - b_{i}} \\right|^{p}} \\right)^{\\frac{1}{p}}$$
(1.11)

Accordingly, `l[1]` and `l[∞]` distances can be computed as in Equations (1.12) and (1.13), respectively.

$$l_{1} = \\left\\| {a - b} \\right\\|_{1} = \\sum\\limits_{i = 1}^{n}\\left| {a_{i} - ~b_{i}} \\right|$$
(1.12)

`l[∞]` = ∥`a`−`b`∥[∞] = max[`i`]|`a[i]`− `b[i]`|
(1.13)

##### 1.3.1.2.1 `l[p]` Norm for Signal Classification

Suppose we have a class of signals that are of length `N`, and `x[n]` is in that class and is of length `N`. If we apply `l[p]` norms to `x[n]`, the resulting `l[1]`, `l[2]`, `l[p]`, and `l[∞]` norm distances will be as follows:

$$l_{1~\\text{norm~}}\\left( {p = 1} \\right) = \\sum\\limits_{n = 0}^{N - 1}\\left| {x\\left\\lbrack n \\right\\rbrack} \\right|$$
(1.14)

$$l_{2~\\text{norm~}}\\left( {p = 2} \\right) = \\left( {\\sum\\limits_{n = 0}^{N - 1}\\left| {x\\left\\lbrack n \\right\\rbrack^{2}} \\right|} \\right)^{\\frac{1}{2}}$$
(1.15)

$$l_{p~\\text{norm~}}\\left( {p \\geq 2} \\right) = \\left( {\\sum\\limits_{n = 0}^{N - 1}\\left| {x\\left\\lbrack n \\right\\rbrack^{p}} \\right|} \\right)^{\\frac{1}{p}}$$
(1.16)

`l[∞ norm]` = max[`n` ∈ {0,…`N`−1}]|`x[n]`|
(1.17)

#### 1.3.1.3 Inner Product Space

A linear vector space `F` is an inner product space if it has an inner product function⟨ , ⟩: `F` × `F`, where `F` ∈ ℝ, ℂ. Inner products are used to measure distances and lengths as well as angles between vectors. Hilbert space is a complete inner product space which will be explained in this chapter at a later stage.

### 1.3.2 Nearest Neighbor Classification

The nearest neighbor classification is one of the oldest and robust distance classification methods that was introduced. Machine learning classification problems use two algorithms, namely, nearest neighbor (NN) and k-nearest neighbors (kNN), which have been successful in numerous machine learning classification problems such as image classification and pattern recognition to name a few. The difference between NN and kNN is that in NN, the value of `k` is 1. The value of `k` generally depends on the training set and typically `k` = $\sqrt{n}$ for a size of `n`.
