
The literature on PLS is extensive and the method has been studied both algorithmically and from its performance point of view. The interested reader can obtain more on PLS from [153]. In all the techniques we have discussed so far, a major focus is on computing the eigenvalues-eigenvectors. To this end, although one can use general packages and algorithms, a number of more efficient alternatives have been derived. A common approach is to solve the task in a two-step iterative procedure. In the first step, the largest eigenvalue (eigenvector) is computed, for which there exist efficient algorithms, such as the power method (e.g., [83]). Then, a procedure known as *deflation* is adopted; this consists of removing from the covariance matrices the variance that has been explained with the features extracted from the first step (see, for example, [135]). Kernelized versions of PLS have also been proposed (for example, [9,152]).

### Remarks 20.3

*   Another dimensionality reduction method results if we set in Eq. [(20.39)](#Chp020_1103-1179_B9780443292385000263.xhtml#deq53)

    ```
    B = [[Σ̂_xx, O], [O, I]].
    ```

*   The resulting method is known as *multivariate linear regression* (MLR). This is the task of finding a set of basis vectors and corresponding regressors such that the MSE in a regression problem is minimized [26].

*   CCA is *invariant* with respect to affine transformations. This is an important advantage with respect to the ordinary correlation analysis (for example, [6]).

*   Extensions of CCA and PLS to more than two data sets have also been proposed (see, for example, [56,110,185]).

## 20.5 Independent component analysis

The latent variable interpretation of PCA was summarized in Eqs. [(20.17)](#Chp020_1103-1179_B9780443292385000263.xhtml#deq22)–[(20.19)](#Chp020_1103-1179_B9780443292385000263.xhtml#deq25), where each one of the observed random variables, `x[i]`, is (approximately) written as a linear combination of the latent variables (principal components in this case), `z[i]`, which are in turn obtained via Eq. [(20.19)](#Chp020_1103-1179_B9780443292385000263.xhtml#deq25), imposing the uncorrelatedness constraint.

The kick-off point for ICA is to assume that the following latent model is true:

```
x = A s, (20.44)
```

where the (unknown) latent variables of `s` are assumed to be mutually statistically *independent* and we refer to them as the *independent components* (ICs). The task then comprises obtaining estimates of both the matrix `A` and the independent components. We will focus on the case where `A` is an `l × l` square matrix. Extensions to fat and tall matrices, corresponding to scenarios where the number of latent variables, `m`, is smaller or larger than the number of the observed random variables, `l`, have also been considered and developed (see, e.g., [100]).

Matrix `A` is known as the *mixing matrix* and its elements, `a[ij]`, as the *mixing coefficients*. The resulting *estimates* of the latent variables will be denoted as `z[i], i = 1, 2…, l`, and we will also refer to them as independent components. The observed random variables, `x[i], i = 1, 2, …, l`, are sometimes called the *mixture variables* or simply mixtures.

To obtain the estimates of the latent variables, we adopt the model

```
ŝ := z = W x, (20.45)
```

where `W` is also known as the *unmixing* or *separating* matrix. Note that

```
z = W A s,
```

and we have to estimate the unknown parameters, so that `z` is as close to `s` as possible. For square matrices, `A = W^(−1)`, assuming invertibility.

### 20.5.1 ICA and Gaussianity

Although in general in statistics adopting the Gaussian assumption for a PDF seems to be rather a “blessing,” in the case of ICA this is not true anymore. This can easily be understood if we look at the consequences of adopting the Gaussian assumption. If the independent components follow Gaussian distributions, their joint PDF is given by
