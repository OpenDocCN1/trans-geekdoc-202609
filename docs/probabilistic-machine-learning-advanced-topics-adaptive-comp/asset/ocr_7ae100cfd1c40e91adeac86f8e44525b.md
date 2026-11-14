# 6.5.2 Example: logistic regression

If \(\ell(\theta)\) is a concave function we want to maximize, then one way to obtain a valid lower bound is to use a bound on its Hessian, i.e., to find a negative definite matrix **B** such that \(\mathbf{H}(\theta) \succ \mathbf{B}\). In this case, one can show (see [BCN18, App. B]) that

```
\(\ell(\theta) \ge \ell(\theta^t) + (\theta - \theta^t)^\mathsf{T} g(\theta^t) + \frac{1}{2}(\theta - \theta^t)^\mathsf{T} \mathbf{B} (\theta - \theta^t)\)
(6.125)
```

where \(g(\theta^t) = \nabla \ell(\theta^t)\). Therefore the following function is a valid lower bound:

```
\(Q(\theta, \theta^t) = \theta^\mathsf{T} (g(\theta^t) - \mathbf{B} \theta^t) + \frac{1}{2} \theta^\mathsf{T} \mathbf{B} \theta\)
(6.126)
```

The corresponding update becomes

```
\(\theta^{t+1} = \theta^t - \mathbf{B}^{-1} g(\theta^t)\)
(6.127)
```

This is similar to a Newton update, except we use **B**, which is a fixed matrix, rather than \(\mathbf{H}(\theta^t)\), which changes at each iteration. This can give us some of the advantages of second order methods at lower computational cost.

For example, let us fit a multi-class logistic regression model using MM. (We follow the presentation of [Kri+05], who also consider the more interesting case of _sparse_ logistic regression.) The probability that example _n_ belongs to class \(c \in \{1, \dots, C\}\) is given by

```
\(p(y_n = c | \mathbf{x}_n, \mathbf{w}) = \frac{\exp(\mathbf{w}_c^\mathsf{T} \mathbf{x}_n)}{\sum_{i=1}^C \exp(\mathbf{w}_i^\mathsf{T} \mathbf{x}_n)}\)
(6.128)
```

Because of the normalization condition \(\sum_{c=1}^C p(y_n = c | \mathbf{x}_n, \mathbf{w}) = 1\), we can set **_w_**_<sub>C</sub>_=**0**. (For example, in binary logistic regression, where _C_=2, we only learn a single weight vector.) Therefore the parameters \(\theta\) correspond to a weight matrix **_w_** of size _D_(_C_-1), where \(\mathbf{x}_n \in \mathbb{R}^D\).

If we let \(\mathbf{p}_n(\mathbf{w}) = [p(y_n = 1 | \mathbf{x}_n, \mathbf{w}), \dots, p(y_n = C-1 | \mathbf{x}_n, \mathbf{w})]\) and \(\mathbf{y}_n = [\mathbb{I}(y_n = 1), \dots, \mathbb{I}(y_n = C-1)]\), we can write the log-likelihood as follows:

```
\(\ell(\mathbf{w}) = \sum_{n=1}^N \left[ \sum_{c=1}^{C-1} y_{nc} \mathbf{w}_c^\mathsf{T} \mathbf{x}_n - \log \sum_{c=1}^C \exp(\mathbf{w}_c^\mathsf{T} \mathbf{x}_n) \right]\)
(6.129)
```

The gradient is given by the following:

```
\(\mathbf{g}(\mathbf{w}) = \sum_{n=1}^N (\mathbf{y}_n - \mathbf{p}_n(\mathbf{w})) \otimes \mathbf{x}_n\)
(6.130)
```

where \(\otimes\) denotes Kronecker product (which, in this case, is just outer product of the two vectors).

The Hessian is given by the following:

```
\(\mathbf{H}(\mathbf{w}) = -\sum_{n=1}^N (\text{diag}(\mathbf{p}_n(\mathbf{w})) - \mathbf{p}_n(\mathbf{w}) \mathbf{p}_n(\mathbf{w})^\mathsf{T}) \otimes (\mathbf{x}_n \mathbf{x}_n^\mathsf{T})\)
(6.131)
```