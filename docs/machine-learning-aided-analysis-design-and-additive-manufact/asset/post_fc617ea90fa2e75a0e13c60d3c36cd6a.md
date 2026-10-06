
## 7.4.2 Stability analysis using discrete singular convolution method

The following normalized quantities are defined as:

```
$$(u,w) = \frac{(u_0,w_0)}{h}, \xi = \frac{x}{L'}, \eta = \frac{y}{L'}, \tau = \frac{t}{I_0}, \omega = \Omega L; \frac{A_{11}^*}{A_{11}}, \ N^* = \frac{P_x}{A_{11}}$$$$
$$(I_0, I_1, I_2) =(\frac{I_0}{I_0^2}, \frac{I_1}{I_0 I_h}, \frac{I_2}{I_h^2}), (a_{11}, b_{11}, d_{11}, e_{11}) = (\frac{A_{11}^*}{A_{11}'}, \frac{B_{11}^*}{A_{11}'}, \frac{D_{11}^*}{A_{11}'}, \frac{E_{11}^*}{A_{11}'})$$$
$$(7.27)$$
```

where $I_0$ and $A_{11}$ are the values of the metal beam between porous and GPLs, respectively, $\omega$ and $N^*$ are the normalized frequency and critical buckling load, respectively. By substituting Eq. (7.27) into going Eq. (7.21) and setting inertia terms to zero, the following equation can be obtained:

```
$$$a_{11}\frac{\partial^2 u}{\partial\xi^2} + b_{11}\frac{\partial^2 \psi}{\partial\xi^2} = 0$$$$
$$$$k_{55}(\frac{\partial^2 w}{\partial\xi^2} + \eta\frac{\partial^2 \psi}{\partial\xi^2}) = N^*\frac{\partial^2 w}{\partial\xi^2}$$$\$
$$$$b_{11}\frac{\partial^2 u}{\partial\xi^2} + d_{11}\frac{\partial^2 \psi}{\partial\xi^2} - k\eta a_{55}(\frac{\partial^2 w}{\partial\xi^2} + \eta\frac{\partial^2 \psi}{\partial\xi^2}) = 0$$$
$
$(7.28)$
```

By applying the DSC method in Eq. (7.23), the following equation is given:

```
$$$a_{11}F_{11}^{(1)}u + b_{11}F_{11}^{(1)}\psi = 0$$$$
$$$$k_{55}(F_{11}^{(2)}w + \eta F_{11}^{(2)}\psi) = N^*F_{11}^{(2)}w$$$$
$$$$b_{11}F_{11}^{(2)}u + d_{11}F_{11}^{(2)}\psi - k\eta a_{55}(F_{11}^{(2)}w + \eta F_{11}^{(2)}\psi) = 0$$$
$
$(7.29)$
```

Four different boundary conditions, such as pinned-pinned (P-P), clamped-clamped (C-C), clamped-pinned (C-P), clamped-free (C-F), are considered:

```
$$$${a_{11}F_{11}^{(1)}u + b_{11}F_{11}^{(1)}\psi = 0$$$$
$$$$F_{11}^{(1)}w + \eta F_{11}^{(1)}\psi = 0$$$$
$$$$b_{11}F_{11}^{(1)}u + d_{11}F_{11}^{(1)}\psi = 0$$}$$
```

Clamped(C): $u = \psi = 0$

Pinned(P): $w = b_{11}F_{11}^{(1)}u + d_{11}F_{11}^{(1)}\psi = 0$

Then get general form of eigenvalue equations can be expressed as:

```
$[\mathbf{K}_E - P\mathbf{K}_S]\mathbf{U}_d = 0 \quad (7.31)$
```

$\mathbf{K}_E$ is the elastic stiffness matrix, $\mathbf{K}_s$ is the associated geometric stiffness matrix, and $\mathbf{U}_d$ is the displacement response.

## 7.5 Surrogate model-based stochastic framework

In this section, a surrogate model-based stochastic framework for FGGR porous beams is built by concerning the random material properties, such as Young’s modules, mean density, the variance of reinforcement grading profiles, and porosity coefficients.

### 7.5.1 Chebyshev metamodel

A continuous one-dimensional function $f(x)$, defined on $[-1,1]$, can be expressed in the terms of Chebyshev series expansion:

```
$f(x) = f_0T_0(x) + f_1T_1(x) + ... + f_nT_n(x) + \varepsilon \approx g(x) = f_0 + \sum_{i=1}^{n} f_nT_i(x) \quad (7.32)$
```

$\varepsilon$ is the error between target function $f(x)$ and the truncated Chebyshev series $g(x)$. For the two-dimensional high order, CMM can be expressed as:

```
$f(x,y) = f_{0,0}T_0(x)T_0(y) + f_{1,0}T_1(x)T_0(y) + f_{0,1}T_0(x)T_1(y) + ... + f_{n_1,n_2}T_{n_1}(x)T_{n_2}(y) + \varepsilon \approx g(x) = f_{0,0}T_0(x)T_0(y) + \sum_{i_1=1}^{n_1} f_{i_1,0}T_{i_1}(x) + \sum_{i_2=1}^{n_2} f_{0,i_2}T_{i_2}(y) + \sum_{i_1=1}^{n_1}\sum_{i_2=1}^{n_2} f_{i_1,i_2}T_{i_1}(x)T_{i_2}(y) \quad (7.33)$
```

where the coefficients $f_{0,0}, f_{0,1}, f_{1,0}, f_{n1,2}$ of Chebyshev polynomials for 2D model can be obtained by Chebyshev orthogonality [29] as shown below:

```
$f_{0,0} = \frac{1}{p_1 p_2} \sum_{i_1=1}^{p_1} \sum_{j_1=1}^{p_2} f(x_{i_1}, y_{j_1}) \quad i_1 \ge 1$
$f_{1,0} = \frac{2}{p_1 p_2} \sum_{i_1=1}^{p_1} \sum_{j_1=1}^{p_2} f(x_{i_1}, y_{j_1}) T_1(x_{i_1}) \quad i_1 \ge 1$
$f_{0,1} = \frac{2}{p_1 p_2} \sum_{i_1=1}^{p_1} \sum_{j_1=1}^{p_2} f(x_{i_1}, y_{j_1}) T_1(y_{j_1}) \quad i_2 \ge 1$
$f_{1,1} = \frac{4}{p_1 p_2} \sum_{i_1=1}^{p_1} \sum_{j_1=1}^{p_2} f(x_{i_1}, y_{j_1}) T_1(x_{i_1}) T_1(y_{j_1}) \quad i_1 \ge 1, i_2 \ge 1$
```

Similarly, the multidimensional systems can be obtained by making the tensor product w.r.t. each dimensional polynomial, as:

```
$f(\mathbf{x}) \approx g(\mathbf{x}) = \sum_{i_1=0}^{p_1} \cdots \sum_{i_n=0}^{p_n} \left(\frac{1}{2}\right)^{\eta} f_{i_1,\dots, i_n} T_{i_1}(x_1) \cdots T_{i_n}(x_n)$
```

where $\mathbf{x} = [x_1, x_2, \dots, x_n]$; $n_i$ denotes the degree in each dimension of Chebyshev polynomial; $\eta$ represents the total occurrence of zeros in subscripts $i_1, \dots, i_n$; and $T_{i_1, \dots, i_k}$ is the $k$-dimensional Chebyshev polynomials, which can be expressed as:

```
$T_{i_1,\dots, i_k}(\mathbf{x}) = T_{i_1}(x_1) \cdots T_{i_k}(x_k), x_i \in [-1, 1], (i = 1, 2, \dots, k)$
```

The coefficients of higher-dimensional polynomials in each dimension can be determined by:

```
$f_{i_1,\dots, i_k} = \left(\frac{k}{2}\right)^{\eta} \sum_{j_1=1}^{p_1} \cdots \sum_{j_k=1}^{p_k} \frac{f(\mathbf{x})}{\sqrt{1-x_1^2} \cdots \sqrt{1-x_k^2}} dx_1 \cdots dx_k \approx \left(\frac{2^k}{p_1 p_2 \cdots p_k}\right)^{\eta} \sum_{j_1=1}^{p_1} \cdots \sum_{j_k=1}^{p_k} f(\cos\theta_1, \dots, \cos\theta_k)$
```

where $p_k = n_k + 1$ and the interpolation points $\cos\theta_j$ in each dimension are the zeros of Chebyshev polynomials for orders $p_k$ and reformulated from Eq. (7.37):

$x_{jk} = \cos\theta_{jk} = \cos\left(\frac{2j_k-1}{2p_k}\pi\right), j_k = 1, 2, ..., p_k$.

## 7.6 Results and discussion

In this section, the accuracy and validity of the present methods are evaluated from both deterministic and stochastic ways. For deterministic, results are compared with Kumar et al. [12]. For stochastic aspect, the efficiency and verification of proposed methods are compared to Monte Carlo scheme (MCS).

### 7.6.1 Validation of deterministic buckling analysis

Kumar et al. [12] and Chen et al. [13] conducted the free vibration, nonlinear vibration, elastic buckling, and postbuckling analysis. The normalized frequencies and critical buckling loads are introduced:

```
$\omega = \Omega\sqrt{\frac{T_0}{A_{11}}}, N^* = \frac{P_x}{A_{11}}$
```

Table 7.1 compare the results of present study with that of Kumar et al. [12] and the present method, where $n$ is the number of layers. As can be seen, the present results match well with the literature for all cases for $L=20$.

**Table 7.1 Comparison of the normalized critical loads of nanocomposite beams**

| $\Delta_{GL}$ | Method | $n$ | $e_\theta=0$ | $e_\theta=0.2$ | $e_\theta=0.4$ | $e_\theta=0.6$ |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1 wt.% | Kumar et al. [12] | 10000 | 0.01507 | 0.01386 | 0.01265 | 0.01139 |
| | Kumar et al. [12] | 10000 | 0.01506 | 0.01386 | 0.01265 | 0.01139 |
| | Present | | 0.00799 | 0.00736 | 0.00675 | 0.00613 |

Probabilistic stability analysis of functionally graphene reinforced porous beams

**Table 7.2 Comparison of the increasing ratio of the normalized critical buckling loads of nanocomposite beams with wt.% for different $L/h$ ($e_0 = 0.5$).**

| Method | Graphene platelets weight fraction (wt.%) | $L/h = 20$ | $L/h = 30$ | $L/h = 40$ | $L/h = 50$ |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Kumar et al. [12] | 0 | 0 | 0 | 0 | 0 |
| Kumar et al. [12] | 0.2 | 18.38 18.59 | 18.51 18.72 | 18.55 18.76 | 18.57 18.78 |
| Kumar et al. [12] | 0.4 | 36.12 36.52 | 36.36 36.77 | 36.45 36.87 | 36.49 36.91 |
| Kumar et al. [12] | 0.6 | 53.24 53.83 | 53.61 54.21 | 53.74 54.35 | 53.81 54.41 |
| Kumar et al. [12] | 0.8 | 69.79 70.56 | 70.28 71.06 | 70.46 71.25 | 70.54 71.33 |
| Kumar et al. [12] | 1 | 85.8 86.74 | 86.41 87.37 | 86.63 87.59 | 86.73 87.70 |

**Table 7.3 Comparison of the increasing ratio of the normalized free vibration of nanocomposite beams with wt.% for different $L/h$ ($e_0 = 0.5$).**

| Method | Graphene platelets weight fraction (wt.%) | $L/h = 20$ | $L/h = 30$ | $L/h = 40$ | $L/h = 50$ |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Kumar et al. [12] | 0 | 0 | 0 | 0 | 0 |
| Kumar et al. [12] | 0.2 | 9.58 9.68 | 9.65 9.75 | 9.68 9.77 | 9.69 9.79 |
| Kumar et al. [12] | 0.4 | 18.34 18.52 | 18.46 18.66 | 18.52 18.67 | 18.54 18.73 |
| Kumar et al. [12] | 0.6 | 26.45 26.67 | 26.63 26.89 | 26.97 26.96 | 26.99 34.39 |
| Kumar et al. [12] | 0.8 | 34.03 34.35 | 34.26 34.59 | 34.35 34.68 | 34.39 34.72 |
| Kumar et al. [12] | 1 | 41.17 41.55 | 41.45 41.84 | 41.55 41.94 | 41.60 41.99 |
