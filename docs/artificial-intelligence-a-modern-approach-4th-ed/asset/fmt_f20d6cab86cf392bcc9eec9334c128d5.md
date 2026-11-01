
It is possible to learn a probability model without making any assumptions about its structure and parameterization by adopting the nonparametric methods of [Section 19.7](#Chapter19-07.xhtml#sec19-7). The task of nonparametric density estimation is typically done in continuous domains, such as that shown in [Figure 21.8(a)](#Chapter21-02.xhtml#fig21-8). The figure shows a probability density function on a space defined by two continuous variables. In [Figure 21.8(b)](#Chapter21-02.xhtml#fig21-8) we see a sample of data points from this density function. The question is, can we recover the model from the samples?

Description

Part (“a”): An arrow labeled `w` subscript `x`, `z` from a node labeled `x` points to a node labeled `z`. An arrow labeled `w` subscript `z`, `y` from node `z` points to a node labeled `y`. A self-loop labeled `w` subscript `z`, `z` from node `z` points back to node `z`. A point on the self-loop is labeled `delta`. Part (b): Arrows labeled `w` subscript `z`, `z` and `w` subscript `x`, `z` from nodes labeled `z` subscript `0` and `x` subscript `1`, respectively, point to a node labeled `z` subscript `1`. An arrow labeled `w` subscript `z`, `y` from node `z` subscript `1` points to a node labeled `y` subscript `1`. Arrows labeled `w` subscript `z`, `z` and `w` subscript `x`, `z` from nodes `z` subscript `1` and `x` subscript `2` point to a node labeled `z` subscript `2`. An arrow labeled `w` subscript `z`, `y` from node `z` subscript `2` points to a node labeled `y` subscript `2`. Arrows labeled `w` subscript `z`, `z` and `w` subscript `x`, `z` from nodes `z` subscript `2` and `x` subscript `3` point to a node labeled `z` subscript `3`. An arrow labeled `w` subscript `z`, `y` from node `z` subscript `3` points to a node labeled `y` subscript `3`.

×![](images/Fig-312.jpg)

Figure 21.8(a) A 3D plot of the mixture of Gaussians from [Figure 21.12(a)](#Chapter21-03.xhtml#fig21-12). [(b)](#Chapter21-03.xhtml#fig21-12) A 128-point sample of points from the mixture, together with two query points (small orange squares) and their 10-nearest-neighborhoods (large circle and smaller circle to the right).

<p class="sidebar">Nonparametric density estimation</p>

First we will consider `k`-nearest-neighbors models. (In [Chapter 19](#Chapter19-00.xhtml) we saw nearest-neighbor models for classification and regression; here we see them for density estimation.) Given a sample of data points, to estimate the unknown probability density at a query point `x` we can simply measure the density of the data points in the neighborhood of `x`. [Figure 21.8(b)](#Chapter21-02.xhtml#fig21-8) shows two query points (small squares). For each query point we have drawn the smallest circle that encloses 10 neighbors—the 10-nearest-neighborhood. We can see that the central circle is large, meaning there is a low density there, and the circle on the right is small, meaning there is a high density there. In [Figure 21.9](#Chapter21-02.xhtml#fig21-9) we show three plots of density estimation using `k`-nearest-neighbors, for different values of `k`. It seems clear that (b) is about right, while (a) is too spiky (`k` is too small) and (c) is too smooth (`k` is too big).

Description

Photograph 1 minus Photograph 2 plus Photograph 3 equals a set of nine photographs. Photograph 1 is of the face of a man with glasses. Photograph 2 is of the face of another man without glasses. Photograph 3 is of the face of a woman without glasses. The set of nine photographs are the faces of the woman with different glasses and slightly altered facial features.

×![](images/Fig-313.jpg)

Figure 21.9 Density estimation using `k`-nearest-neighbors, applied to the data in [Figure 21.8(b)](#Chapter21-02.xhtml#fig21-8), for `k` = 3, 10, and 40 respectively. `k` = 3 is too spiky, 40 is too smooth, and 10 is just about right. The best value for `k` can be chosen by cross-validation.

Another possibility is to use kernel functions, as we did for locally weighted regression. To apply a kernel model to density estimation, assume that each data point generates its own little density function. For example, we might use spherical Gaussians with standard deviation `w` along each axis. Then estimated density at a query point `x` is the average of the data kernels:

$\\begin{matrix} {P(\\mathbf{x}) = \\frac{1}{N}{\\sum\\limits\_{j = 1}^{N}{K(\\mathbf{x},\\mathbf{x}\_{j})}}} & \\text{where} & {K(\\mathbf{x},\\mathbf{x}\_{j}) = \\frac{1}{{(w^{2}\\sqrt{2\\pi})}^{d}}e^{- \\frac{D{(\\mathbf{x},\\mathbf{x}\_{j})}^{2}}{2w^{2}}}} \\\\ \\end{matrix},$

where `d` is the number of dimensions in `x` and `D` is the Euclidean distance function. We still have the problem of choosing a suitable value for kernel width `w`; [Figure 21.10](#Chapter21-02.xhtml#fig21-10) shows values that are too small, just right, and too large. A good value of `w` can be chosen by using cross-validation.

×![](images/Fig-314.jpg)

Figure 21.10 Density estimation using kernels for the data in [Figure 21.8(b)](#Chapter21-02.xhtml#fig21-8), using Gaussian kernels with `w` = 0.02, 0.07, and 0.20 respectively. `w` = 0.07 is about right.

## 21.3 Learning with Hidden Variables: The EM Algorithm

The preceding section dealt with the fully observable case. Many real-world problems have hidden variables (sometimes called latent variables), which are not observable in the data. For example, medical records often include the observed symptoms, the physician’s diagnosis, the treatment applied, and perhaps the outcome of the treatment, but they seldom contain a direct observation of the disease itself! (Note that the diagnosis is not the disease; it is a causal consequence of the observed symptoms, which are in turn caused by the disease.) One might ask, “If the disease is not observed, could we construct a model based only on the observed variables?” The answer appears in [Figure 21.11](#Chapter21-03.xhtml#fig21-11), which shows a small, fictitious diagnostic model for heart disease. There are three observable predisposing factors and three observable symptoms (which are too depressing to name). Assume that each variable has three possible values (e.g., none, moderate, and severe). Removing the hidden variable from the network in (a) yields the network in (b); the total number of parameters increases from 78 to 708. Thus, latent variables can dramatically reduce the number of parameters required to specify a Bayesian network. This, in turn, can dramatically reduce the amount of data needed to learn the parameters.

×![](images/Fig-315.jpg)

Figure 21.11(a) A simple diagnostic network for heart disease, which is assumed to be a hidden variable. Each variable has three possible values and is labeled with the number of independent parameters in its conditional distribution; the total number is 78. (b) The equivalent network with `HeartDisease` removed. Note that the symptom variables are no longer conditionally independent given their parents. This network requires 708 parameters.

<p class="sidebar">Latent variable</p>

Hidden variables are important, but they do complicate the learning problem. In [Figure 21.11(a)](#Chapter21-03.xhtml#fig21-11), for example, it is not obvious how to learn the conditional distribution for `HeartDisease`, given its parents, because we do not know the value of `HeartDisease` in each case; the same problem arises in learning the distributions for the symptoms. This section describes an algorithm called expectation–maximization, or `EM`, that solves this problem in a very general way. We will show three examples and then provide a general description. The algorithm seems like magic at first, but once the intuition has been developed, one can find applications for `EM` in a huge range of learning problems.

<p class="sidebar">Expectation-maximization</p>

### 21.3.1 Unsupervised clustering: Learning mixtures of Gaussians
