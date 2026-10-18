
In other words, you map the existing features onto a feature space of higher dimensionality in hopes of finding a way to separate the classes linearly. This is the same process as shown in [Chapter 13](#c13.xhtml) when trying polynomial expansion (where you discovered how a linear model captures nonlinear relationships between features automatically). Automatic feature creation using polynomial expansion, which is also possible for SVMs, has some important limits:

*   The number of potential features increases exponentially, making computations cumbersome and saturating the in-memory dataset. (Some datasets can’t be expanded beyond a power of 2 or 3.)

*   The expansion creates many redundant features, causing overfitting.

*   It’s difficult to determine the level of expansion where the classes will become linearly separable, thus requiring many iterations of expansion and test.

Because of these limitations, SVM has adopted a different way, called `kernel functions`, to redefine the feature space without occupying more memory or increasing the number of computations too much. Kernel functions aren’t magic; they rely on algebraic calculations, and they are the more mathematically demanding part of an SVM. As a means of understanding how they work, you could say that kernel functions project the original features into a higher dimensional space by combining them in a nonlinear way. They do so in an implicit way because they don’t provide SVM with a new feature space to use for learning (as a polynomial expansion would do). Instead, they return a vector of transformed values that the SVM can use directly to fit a nonlinear separating hyperplane on the original data.

Kernel functions, therefore, provide the result of a combination of features (precisely a dot product, a multiplication between vectors), without calculating all the combinations involved in such result. They act as a translator, converting implicitly the original data into a higher dimensional space, finding a linear separator and then returning the information of that linear separator in higher dimensions into the original space (where it is nonlinear). This is called the `kernel trick`.

### Explaining the kernel trick by example

Kernel functions are convenient mapping functions that allow SVMs to obtain a transformed dataset of limited size, which is equivalent to a more complicated and data-intensive nonlinear transformation. Computationally accessible by most computers in terms of processing and memory, kernel functions allow solving a data problem using a nonlinear separating hyperplane automatically, without requiring human intervention for feature creation.

In its implementations in Python, SVM offers quite a large range of nonlinear kernels. Here is the list of all the kernels and their parameters:

*   `Linear`: No extra parameters

*   `Radial Basis Function`: Shape parameters: `gamma`

*   `Polynomial`: Shape parameters: `gamma`, `degree`, and `coef0`

*   `Sigmoid`: Shape parameters: `gamma` and `coef0`

*   `Custom-made kernels`: Depends upon the kernel

Even though the choice of kernels is large (and possibly larger if you design your own custom kernels), you normally use the Radial Basis Function (`RBF`). `RBF` is the most popular kernel because it's more powerful than other kernels because it can map and approximate almost any nonlinear function if you tweak its shape parameter, `gamma`.

The `RBF` works in a simple but smart way. It creates a margin around every support vector — drawing bubbles in the feature space, as shown in [Figure 15-3](#c15.xhtml#c15-fig-0003). Then, according to the `gamma` hyper-parameter value, it expands or restricts the volume of the bubbles so that they fuse with each other and shape classification areas. The `gamma` value defines the radius of all the bubbles that `RBF` creates. The resulting margin and the hyperplane passing through it will consequently show very curvy boundaries, demonstrating that it can be quite flexible, as in the examples provided by [Figure 15-3](#c15.xhtml#c15-fig-0003).

![FIGURE 15-3: An RBF kernel that uses diverse hyper-parameters to create unique SVM solutions.](images/9781119724018-fg1503.png)

[FIGURE 15-3:](#c15.xhtml#rc15-fig-0003) An RBF kernel that uses diverse hyper-parameters to create unique SVM solutions.

The `RBF` kernel can adapt itself to different learning strategies, resulting in a bended hyperplane when the `C` parameter, for instance in the Python Scikit-learn implementation, is high, and creating a smoother curve line when `C` is low. It can also fit complex shapes, such as the bull's eye, when a class is placed inside another. All this flexibility comes at the expense of a larger estimate variance, but it also detects complex classification rules that other algorithms may fail to find.

![Remember](images/remember.png)When tuning an `RBF` kernel, first fix the `C` parameter, sometimes mentioned as the regularization term, to define a bended separating hyperplane; then tune `gamma` to make the margin shape rough and broken when the hyper-parameter `gamma` is low or regular and fused into large bubble-shaped areas when it is high.

The polynomial and sigmoid kernels aren't as adaptable as `RBF`, thus showing more bias, yet they are both nonlinear transformations of the separating hyperplane. If the sigmoid features a single bend, the polynomial function can have as many bends or separated hyperplanes as its set degree. The higher the degree, the longer it takes to compute.

![Remember](images/remember.png)You have many shape values to fix when using the sigmoid and polynomial kernels: `gamma` and `coef0` for both and `degree` for polynomial. Because determining the effects that different values have on these parameters is difficult, you need to test different value combinations, using a grid search, for instance, and evaluate the results on a practical basis. [Figure 15-4](#c15.xhtml#c15-fig-0004) provides visual representations of what you can do with the polynomial and the `RBF` kernels.

![FIGURE 15-4: A polynomial (left) and an RBF kernel (right) applied to the same data.](images/9781119724018-fg1504.png)

[FIGURE 15-4:](#c15.xhtml#rc15-fig-0004) A polynomial (left) and an RBF kernel (right) applied to the same data.

![Tip](images/tip.png)In spite of the possibility of creating your own kernel function, most data problems are easily solved using the `RBF`. Simply look for the right combination `C` and `gamma` by trying different values systematically until you achieve a best result for your validation set or cross-validation procedure.

## Classifying and Estimating with SVM

Although SVMs are complex learning algorithms, they are versatile and easy to use when implemented in Python. The Scikit-learn implementation relies on an external C++ package, LIBSVM, developed at National Taiwan University. You can find more on the shared LIBSVM for SVM classification and regression at [`https://www.csie.ntu.edu.tw/~cjlin/libsvm/`](https://www.csie.ntu.edu.tw/~cjlin/libsvm/). The Scikit-learn implementation also uses the LIBLINEAR C package, which specializes in classification problems using linear methods on large and sparse datasets. This package is from the same authors at National Taiwan University who produced the LIBSVM package (see more at [`https://www.csie.ntu.edu.tw/~cjlin/liblinear/`](https://www.csie.ntu.edu.tw/~cjlin/liblinear/)).
