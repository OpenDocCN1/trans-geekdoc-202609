
maximize an objective function.² To start with, the weights are initialized to random probability values. The gradient ascent method performs greedy hill-climbing in that, at each iteration or step along the way, the algorithm moves toward what appears to be the best solution at the moment, without backtracking. The weights are updated at each iteration. Eventually, they converge to a local optimum solution.

For our problem, we maximize the objective function \(P_w(D) = \prod_{d=1}^{|D|} P_w(X_d)\). This can be done by following the gradient of \(\ln P_w(D)\), which makes the problem simpler. (Recall that we have used the same trick to train a logistic regression classifier in Chapter 6.) Given the network topology and initialized \(w_{ijk}\), the algorithm proceeds as follows:

- 1. Compute the gradients: For each i, j, k, compute
  
  \(\frac{\partial \ln P_w(D)}{\partial w_{ijk}} = \sum_{d=1}^{|D|} \frac{\partial \ln(P(Y_i = y_{ij}, U_i = u_{ik} | X_d))}{\partial w_{ijk}}.\) (7.5)

The probability on the right side of Eq. (7.5) is to be calculated for each training tuple, \(X_d\), in \(D\). For brevity, let's refer to this probability simply as \(p\). When the variables represented by \(Y_i\) and \(U_i\) are hidden for some \(X_d\), the corresponding probability \(p\) can be computed from the observed variables of the tuple using standard algorithms for Bayesian network inference such as those available in the commercial software package HUGIN (http://www.hugin.dk).

- 2. Take a small step in the direction of the gradient: The weights are updated by
  
  \(w_{ijk} \leftarrow w_{ijk} + \eta \frac{\partial \ln P_w(D)}{\partial w_{ijk}},\) (7.6)

where \(\eta\) is the learning rate representing the step size, and \(\frac{\partial \ln P_w(D)}{\partial w_{ijk}}\) is computed from Eq. (7.5). The learning rate is set to a small constant and helps with convergence.

- 3. Renormalize the weights: Because the weights \(w_{ijk}\) are probability values, they must be between 0.0 and 1.0, and \(\sum_j w_{ijk}\) must equal 1 for all \(i, k\). These criteria are achieved by renormalizing the weights after they have been updated by Eq. (7.6).

Algorithms that follow this learning form are called adaptive probabilistic networks. Other methods for training belief networks are referenced in the bibliographic notes at the end of this chapter. Belief networks could be computationally intensive. Because belief networks provide explicit representations of causal structure, a human expert can provide prior knowledge to the training process in the form of network topology or conditional probability values. This can significantly improve the learning speed.

## 7.3 Support vector machines

In this section, we study support vector machines (SVMs), a method for the classification of both linear and nonlinear data. In a nutshell, an SVM is an algorithm that works as follows. It uses a nonlinear mapping to transform the original training data into a higher-dimensional space. Within this new space, it searches for the linear optimal separating hyperplane (i.e., a “decision boundary” separating the tuples of one class from another). With an appropriate nonlinear mapping to a sufficiently high-dimensional space, data from two classes can always be separated by a hyperplane. The SVM finds this hyperplane using support vectors (“essential” training tuples) and margins (defined by the support vectors). We will delve more into these new concepts later.

“I’ve heard that SVMs have attracted a great deal of attention lately. Why?” The first paper on support vector machines was presented in 1992 by Vladimir Vapnik and colleagues Bernhard Boser and Isabelle Guyon, even though the groundwork for SVMs has been around since the 1960s (including early work by Vapnik and Alexei Chervonenkis on statistical learning theory). Although the training of even the fastest SVMs could be slow, they are highly accurate, owing to their ability to model complex nonlinear decision boundaries. They are much less prone to overfitting than other methods. The support vectors also provide a compact description of the learned model. SVMs can be used for numeric prediction and classification. They have been applied to a number of areas, including handwritten digit recognition, object recognition, emotion recognition, and speaker identification, as well as benchmark time-series prediction tasks.

### 7.3.1 Linear support vector machines

To explain the mystery of SVMs, let’s first look at the simplest case—a two-class problem where the classes are linearly separable. Let the data set D be given as (X1, y1), (X2, y2), ..., (X|D|, y|D|), where Xi is the set of training tuples with associated class labels, yi. Each yi can take one of two values, either +1 or –1 (i.e., yi ∈ {+1, –1}), corresponding to the classes buys_ycomputer = yes and buys_ycomputer = no, respectively. To aid in visualization, let’s consider an example based on two input attributes, A1 and A2, as shown in Fig. 7.5. From the graph, we see that the 2-D data are linearly separable (or “linear” for short), because a straight line can be drawn to separate all the tuples of class +1 from all the tuples of class –1.

There are an infinite number of separating lines that could be drawn. We want to find the “best” one, that is, one that (we hope) will have the minimum classification error on previously unseen tuples. How can we find this best line? Note that if our data were 3-D (i.e., with three attributes), we would want to find the best separating plane. Generalizing to n dimensions, we want to find the best hyperplane. We will use “hyperplane” to refer to the decision boundary that we are seeking, regardless of the number of input attributes.

An SVM approaches this problem by searching for the maximum margin hyperplane. Consider Fig. 7.6, which shows two possible separating hyperplanes and their associated margins. Before we get into the definition of margins, let’s take an intuitive look at this figure. Both hyperplanes can correctly classify all the given data tuples. Intuitively, however, we expect the hyperplane with the larger margin to be more accurate at classifying future data tuples than the hyperplane with the smaller margin. This is why (during the learning or training phase) the SVM searches for the hyperplane with the largest margin, that is, the maximum margin hyperplane (MMH). The associated margin gives the largest separation between classes.

Getting to an informal definition of margin, we can say that the shortest distance from a hyperplane to one side of its margin is equal to the shortest distance from the hyperplane to the other side of its margin, where the “sides” of the margin are parallel to the hyperplane. When dealing with the MMH, this distance is, in fact, the shortest distance from the MMH to the closest training tuple of either class.

![](img/90c930779c8f928df6ff4481fc59f9a3_350_0.png)

**FIGURE 7.5**
The 2-D training data that are linearly separable. There are an infinite number of possible separating hyperplanes or "decision boundaries," some of which are shown here as dashed lines. Which one is best?

A separating hyperplane is essentially a linear classifier. Similar to other linear classifiers (such as perceptron, logistic regression) that were introduced in Chapter 7, it can be written as

```
$$ \mathbf{W} \cdot \mathbf{X} + b = 0, $$ (7.7)
```

where \mathbf{W} is a weight vector, namely, \mathbf{W} = {w1, w2, ..., wn}; n is the number of attributes; and b is a scalar, often referred to as a bias. To aid in visualization, let's consider two input attributes, A1 and A2, as in Fig. 7.6(b). Training tuples are 2-D (e.g., \mathbf{X} = (x1, x2)), where x1 and x2 are the values of attributes A1 and A2, respectively, for \mathbf{X}. Eq. (7.7) can be written as

```
$$ b + w_1 x_1 + w_2 x_2 = 0. $$ (7.8)
```

Thus any point that lies above the separating hyperplane satisfies

```
$$ b + w_1 x_1 + w_2 x_2 > 0. $$ (7.9)
```

Similarly, any point that lies below the separating hyperplane satisfies

```
$$ b + w_1 x_1 + w_2 x_2 < 0. $$ (7.10)
```
