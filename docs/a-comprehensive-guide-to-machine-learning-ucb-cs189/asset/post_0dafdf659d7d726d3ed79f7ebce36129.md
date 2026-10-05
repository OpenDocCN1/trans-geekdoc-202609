
Plugging these estimates for the tr covariance matrices, we arrive at the problem

```
$$\max_{u,v} \frac{u^{\top} (\frac{1}{n}X^{\top}Y) u}{\sqrt{u^{\top} (\frac{1}{n}X^{\top}X) \cdot v^{\top} (\frac{1}{n}Y^{\top}Y) v}}} = \max_{u,v} \frac{u^{\top} X^{\top}Y v}{\sqrt{u^{\top} X^{\top}X \cdot v^{\top} Y^{\top}Y}}} = \rho(Xu, Yv)$$
```

Let's try to manage the maximization problem into a form that we can reason with more easily. Our strategy is to choose matrices to transform $X$ and $Y$ such that the maximization problem is equivalent but easier to understand.

- 1. First, let's choose matrices $W_x, W_y$ to whiten $X$ and $Y$. This will make the (co)variance matrices $(W_x^{\top})(WX_x)$ and $(W_y^{\top})(YW_y)$ identity matrices and simplify our expression. To do this, note that $X^{\top}X$ is positive definite (hence symmetric), so we can employ the eigendecomposition

```
$X^{\top}X = U_x S_x U_x^{\top}$
```

Since all the diagonal entries are positive, we can define the "square root" of this matrix by taking the square root of every diagonal entry:

```
$S_x^{1/2} = \text{diag}(\sqrt{\lambda_1(X^{\top}X)}, \dots, \sqrt{\lambda_d(X^{\top}X)})$
```

Then, $W_x = U_x S_x^{-1/2}U_x^{\top}$, we have

```
$$(W_x^{\top})(WX_x) = W_x^{\top}X^{\top}WX_x
\= U_x S_x^{-1/2}U_x^{\top}X^{\top}WX_xU_x S_x^{-1/2}U_x^{\top}\
\= U_x S_x^{-1/2}S_x S_x^{-1/2}U_x^{\top}\
\= U_x U_x^{\top}\
\= I$$
```

which shows that $W_x$ is a whitening matrix for $X$. The same process can be repeated to produce a whitening matrix $W_y = U_y S_y^{-1/2}U_y^{\top}$ for $Y$.

Let's denote the whitened $u_w = W_x^{-1}u, v_w = W_y^{-1}v$ and $X_w = WX_x, Y_w = WY_y$. Then by the change of variables

```
$$\max_{u,v} \rho(Xu, Yv) = \max_{u,v} \frac{(Xu)^{\top}(Yv)}{\sqrt{(Xu)^{\top}(Xu) \cdot (Yv)^{\top}(Yv)}}\
\= \max_{u,v} \frac{(X_w^{\top}X_w)W_x^{-1}u^{\top}Y_w^{\top}W_y^{-1}v}{\sqrt{(X_w^{\top}X_w)W_x^{-1}u^{\top}W_x^{-1}u \cdot (Y_w^{\top}Y_w)W_y^{-1}v^{\top}W_y^{-1}v)}}\
\= \max_{u_w,v_w} \frac{(X_w^{\top}X_w)u_w^{\top}v_w}{\sqrt{(X_w^{\top}X_w)u_w^{\top}u_w \cdot (Y_w^{\top}Y_w)v_w^{\top}v_w}}}\
\= \max_{u_w,v_w} \frac{u_w^{\top}X_w^{\top}X_w u_w}{\sqrt{u_w^{\top}X_w^{\top}X_w u_w \cdot v_w^{\top}Y_w^{\top}Y_w v_w}}$$
```

## 3.3. CANONICAL CORRELATION ANALYSIS

```
= \max_{u_w, v_w} \frac{u_w^{\top} X_w^{\top} Y_w v_w}{\sqrt{u_w^{\top} X_w^{\top} X_w u_w \cdot v_w^{\top} Y_w^{\top} Y_w v_w}}}\
\= \rho(X_w, Y_w)
```

We have used the fact that $X_w^{\top} X_w$ and $Y_w^{\top} Y_w$ are identity matrices by construction.

- Second, let's choose matrices $D_x, D_y$ to **decorrelate** $X_w$ and $Y_w$. This will let us simplify the covariance matrix $(X_w D_x)^{\top} (Y_w D_y)$ into a **diagonal** matrix. To do this, we'll use the SVD:

```
$X_w^{\top} X_w = USV^{\top}$
```

The choice of $U$ for $D_x$ and $V$ for $D_y$ largely,

```
$(X_w U)^{\top} (Y_w V) = U^{\top} X_w^{\top} Y_w V = U^{\top} S V^{\top} = S$
```

Let's denote the decorated $X_d = D_x^{-1}X_w$ and $Y_d = D_y^{-1}Y_w$. Then by the change of variables $u_d = D_x^{-1}u_w$ and $v_d = D_y^{-1}v_w$,

```
$\max_{u_w, v_w} \rho(X_w u_w, Y_w v_w) = \max \frac{(X_w u_w)^{\top} (Y_w v_w)}{\sqrt{(X_w u_w)^{\top} (X_w u_w) \cdot (Y_w v_w)^{\top} (Y_w v_w)}}\
\= \max_{u_w, v_w} \frac{(D_x D_x^{-1} X_w u_w)^{\top} (D_y D_y^{-1} Y_w v_w)}{\sqrt{(D_x D_x^{-1} X_w u_w)^{\top} (D_x D_x^{-1} X_w u_w) \cdot (D_y D_y^{-1} Y_w v_w)^{\top} (D_y D_y^{-1} Y_w v_w)}}\
\= \max_{u_w, v_w} \frac{(X_d u_d)^{\top} (Y_d v_d)}{\sqrt{(X_d u_d)^{\top} (X_d u_d) \cdot (Y_d v_d)^{\top} (Y_d v_d)}}\
\= \max_{u_d, v_d} \frac{u_d^{\top} X_d^{\top} Y_d v_d}{\sqrt{u_d^{\top} X_d^{\top} X_d u_d \cdot v_d^{\top} Y_d^{\top} Y_d v_d}}\
\= \rho(X_d, Y_d)\
\= \max_{u_d, v_d} \frac{u_d^{\top} S v_d}{\sqrt{u_d^{\top} u_d \cdot v_d^{\top} v_d}}
```

With loss of generality, suppose $u_d$ and $v_d$ are unit vectors so that the denominator becomes 1, and we can ignore it:

```
$\max_{u_d, v_d} u_d^{\top} S v_d = \max_{\|u_d\|=1, \|v_d\|=1} u_d^{\top} S v_d = \max_{\|u_d\|=1} \|Su_d\|$
```

The diagonal of $S$ implies $0$ for $i \neq j$, so our simplified objective expands as

```
$u_d^{\top} S v_d = \sum_{i,j} S_{ij}(u_d)_i(v_d)_j = \sum_{i} S_{ii}(u_d)_i(v_d)_i$
```

Where $S_{ii}$, the singular values of $X_d, Y_d$, are arranged in descending order. Thus we have a weighted sum of these singular values, where the weights are given by the entries of $u_d$ and $v_d$, and which are

> 4 Why can we assume this? Observe that the value of the objective does not change if we replace $u_w$ by $\alpha u_w$ and $v_w$ by $\beta v_w$, where $\alpha$ and $\beta$ are any positive constants. Thus if there are maximizers $u_d, v_d$ which are not unit vectors, then $u_d/\|u_d\|$ and $v_d/\|v_d\|$ (which are unit vectors) are also maximizers.

## CHAPTER 3. LOW-RANK APPROXIMATION

constrained to have norm. To maximize the sum, we “put all our eggs in one basket” and extract $S_{11}$ by setting the first components of $u_d$ and $v_d$ to 1, and the rest to 0:

```
$u_d = \begin{bmatrix} 1 & 0 \\ \vdots \\ 0 \end{bmatrix} \in \mathbb{R}^p \quad v_d = \begin{bmatrix} 1 & 0 \\ \vdots \\ 0 \end{bmatrix} \in \mathbb{R}^q$
```

Any other arrangement would put weight on $S_{dd}$ at the expense of taxing that weight away from $S_{11}$, which is the largest, reducing the value of the sum.

Finally we have an analytical solution, but it is in a different coordinate system than our original problem! In particular, $u_d$ and $v_d$ are the best weights in a coordinate system where the data has been whitened and correlated. To bring it to our original coordinate system and find the vectors we care about ($u$ and $v$), we must invert the changes of variables:

```
$u = W_u D_u u_d \quad v = W_v D_v v_d$
```

More generally, to get the best $k$ directions, we

```
$U_d = \begin{bmatrix} I_k & O_{p-k,k} \end{bmatrix} \in \mathbb{R}^{p \times k} \quad V_d = \begin{bmatrix} I_k & O_{q-k,k} \end{bmatrix} \in \mathbb{R}^{q \times k}$
```

where $I_k$ is the identity matrix.

$u_d$ and $v_d$ are the best weights in a coordinate system where the data has been whitened and correlated.

$u_d$ and $v_d$ are the best weights in a coordinate system where the data has been whitened and correlated.

$u_d$ and $v_d$ are the best weights in a coordinate system where the data has been whitened and correlated.

$u_d$ and $v_d$ are the best weights in a coordinate system where the data has been whitened and correlated.

$u_d$ and $v_d$ are the best weights in a coordinate system where the data has been whitened and correlated.

$u_d$ and $v_d$ are the best weights in a coordinate system where the data has been whitened and correlated.
