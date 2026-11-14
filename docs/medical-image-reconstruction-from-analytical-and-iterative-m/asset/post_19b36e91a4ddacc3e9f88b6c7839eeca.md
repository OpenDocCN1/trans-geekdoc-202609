

### Property 1

Left = \(AA^+ A = AA^T (AA^T)^{-1} A = (AA^T) (AA^T)^{-1} A = A =\) Right

### Property 2

Left = \(A^+ A A = A^T (AA^T)^{-1} AA^T (AA^T) = A^T (AA^T)^{-1} (AA^T) (AA^T)^{-1}\)

\(= A^T (AA^T)^{-1} = A^+ =\) Right

### Property 3

Left = \((A^+ A)^T = \left( A^T (AA^T)^{-1} A \right)^T = A^T \left( (AA^T)^{-1} \right)^T A\)

\(= A^T \left( (AA^T)^T \right)^{-1} A = A^T (AA^T)^{-1} A = A^+ A =\) Right

### Property 4

Left = \((AA^+)^T = \left( AA^T (AA^T)^{-1} \right)^T = \left( (AA^T) (AA^T)^{-1} \right)^T = I\)

Right = \(AA^+ = AA^T (AA^T)^{-1} = (AA^T) (AA^T)^{-1} = I\)

## Example 2

In Section 6.1, we used SVD to decompose matrix \(A_{m \times n}\) into \(A_{m \times n} = U_{m \times m} \Sigma V^T_{n \times n}\) and defined \(A^+ = V \Sigma^+ U^T\) (assuming \(\sigma_r > 0\)) with \(\Sigma^+_{n \times m} = \begin{bmatrix} D_r & 0 \\ 0 & 0 \end{bmatrix}\) and \(D_r = \text{diag} \{ 1/\sigma_1, 1/\sigma_2, ..., 1/\sigma_r, 0, ..., 0 \}\). Is \(A^+ = V \Sigma^+ U^T\) a generalized inverse of matrix \(A\) according to the four properties stated in Example 1? Find the condition under which \(A^+ = V \Sigma^+ U^T\) is a generalized inverse of matrix \(A\).

### Solution

Let us apply the first property to \(A^+ = V \Sigma^+ U^T\) and \(A_{m \times n} = U_{m \times m} \Sigma V^T_{n \times n}\):

\(AA^+ = U \Sigma V^T V \Sigma^+ U^T U \Sigma V^T = U \Sigma (V^T V) \Sigma^+ (U^T U) \Sigma V^T = U \Sigma \Sigma^+ \Sigma V^T\)

In order to have \(AA^+ A = A\), we must have

\(\Sigma^+ \Sigma = \Sigma,\)

which is equivalent to

\(\text{diag}\{ \sigma_1, \sigma_2, ..., \sigma_r, ..., \sigma_m \} \text{diag}\left\{ \frac{1}{\sigma_1}, \frac{1}{\sigma_2}, ..., \frac{1}{\sigma_r}, 0, ..., 0 \right\} \text{diag}\{ \sigma_1, \sigma_2, ..., \sigma_r, ..., \sigma_m \}\)

\(= \text{diag}\{ \sigma_1, \sigma_2, ..., \sigma_r, ..., \sigma_m \},\)

or

\(\sigma_{r+1} = \cdots = \sigma_m = 0.\) (6.121)

Since

\(\sigma_1 \ge \sigma_2 \ge \cdots \ge \sigma_r \ge \cdots \ge 0,\) (6.122)

Property 1 is equivalent to

\(\sigma_{r+1} = 0 \text{ and } \sigma_r > 0.\) (6.123)

Now let us look at Property 2:

\(A^+AA^+ = A^+,\) (6.124)

which is equivalent to

\(\text{diag} \left\{ \frac{1}{\sigma_1}, \frac{1}{\sigma_2}, \dots, \frac{1}{\sigma_r}, 0, \dots, 0 \right\} = \text{diag} \left\{ \frac{1}{\sigma_1}, \frac{1}{\sigma_2}, \dots, \frac{1}{\sigma_r}, 0, \dots, 0 \right\}.\) (6.125)

This property is always satisfied.

Property 3 \(A^+A^*A = A^*A\) and Property 4 \((AA^+)^* = AA^+\) both imply that

\(\text{diag} \{ 1, 1, \dots, 1, 0, \dots, 0 \} = \text{diag} \{ 1, 1, \dots, 1, 0, \dots, 0 \},\) (6.126)

which is always satisfied.

To summarize the above discussion, the condition under which \(A^+ = V\Sigma^*U^T\) is a generalized inverse of matrix \(A\) is

\(\sigma_{r+1} = 0 \text{ and } \sigma_r > 0.\) (6.127)

However, in practice, a cutoff index much smaller than this \(r\) is used to obtain a stable solution.

## Example 3

None of the following images match the measured projections. Which one is the best solution among the three solutions in Figure 6.23? (Compare \(\chi^2\))

### Solution

- i) \(\chi^2 = 0^2 + 0^2 + 1^2 + 1^2 = 2, (\leftarrow \text{ Best})\)

- ii) \(\chi^2 = 0^2 + 0^2 + 2^2 + 0^2 = 4,\)

- iii) \(\chi^2 = 1^2 + 0^2 + 1^2 + 2^2 = 6.\)

## Example 4

Find a least-squares reconstruction to the imaging problem shown in Figure 6.24.

### Solution

The imaging matrix \(A\) for this problem \(AX = P\) is given as

| 1 | 0 | 1 | 0 |
|---|---|---|---|
| 0 | 1 | 0 | 1 |
| 1 | 1 | 0 | 0 |
| 0 | 0 | 1 | 1 |

(6.128)

The rank of \( A \) is 3. The system \( AX = P \) is also not consistent. Therefore, there is no solution for this problem. We can use SVD-based method to find a pseudo-solution. Using Matlab with \( X = \text{pinv}(A) * P \), we get \( x_1 = 2.25 \), \( x_2 = 1.75 \), \( x_3 = 1.75 \), and \( x_4 = 1.25 \).

## Example 5

Let \( A = \begin{bmatrix} 2 & 0 \\ 0 & 1 \end{bmatrix} \). Find the conjugate direction \(\bar{u}_1\) of \(\bar{u}_0 = \begin{bmatrix} 1 \\ 1 \end{bmatrix}\).

### Solution

The conjugate direction is defined by this relationship: \(\bar{u}_0(A^T A)\bar{u}_1 = 0\), where

\(A^T A = \begin{bmatrix} 2 & 0 \\ 0 & 1 \end{bmatrix} \begin{bmatrix} 2 & 0 \\ 0 & 1 \end{bmatrix} = \begin{bmatrix} 4 & 0 \\ 0 & 1 \end{bmatrix} .\) (6.129)

![](img/dd555effd38151c67af30d84800c554a_183_0.png)

Fig. 6.23: Three images try to match the projections.

![](img/dd555effd38151c67af30d84800c554a_183_1.png)

Fig. 6.24: A 2 x 2 image reconstruction problem.

We also know

\(\begin{bmatrix} 1 \\ 1 \end{bmatrix} \cdot \begin{bmatrix} 1 \\ -1 \end{bmatrix} = 0 .\) (6.130)

Thus \(\begin{bmatrix} 4 & 0 \\ 0 & 1 \end{bmatrix} \bar{u}_1 = \begin{bmatrix} 1 \\ -1 \end{bmatrix}\), which leads to

\(\bar{u}_1 = \begin{bmatrix} 1/4 & 0 \\ 0 & 1 \end{bmatrix} \begin{bmatrix} 1 \\ -1 \end{bmatrix} = \begin{bmatrix} 1/4 \\ -1 \end{bmatrix} .\) (6.131)

![](img/dd555effd38151c67af30d84800c554a_184_0.png)

Fig. 6.25: Conjugate directions.

(If you want, you could normalize $\vec{u}_1$ and make it a unit vector.)

The matrix $A^T A$ defines a quadratic form, which is an ellipse in our case. The point of this example is as follows: For any initial direction $\vec{u}_0$, draw an ellipse specified by the quadratic form $A^T A$ such that $\vec{u}_0$ is a tangential direction. If you travel along the conjugate direction $\vec{u}_1$, you will reach the center of the ellipse (see Figure 6.25).

## Example 6

Compute one iteration of the ML-EM algorithm with the initial image and projections given in Figure 6.26.

![](img/dd555effd38151c67af30d84800c554a_184_1.png)

Fig. 6.26: Initial image and projection data for Example 6.

### Solution

Step 1: Find the forward projections:

![](img/dd555effd38151c67af30d84800c554a_184_2.png)

Step 2: Find the ratios of given (i.e., measured) projections and the forward projections of the current image:

![](img/dd555effd38151c67af30d84800c554a_185_0.png)

Step 3: Backproject the ratios:

![](img/dd555effd38151c67af30d84800c554a_185_1.png)

Step 4: Backproject a constant 1 from all rays:

![](img/dd555effd38151c67af30d84800c554a_185_2.png)

Step 5: Find the pixel-by-pixel ratio of the backprojected image obtained from Step 3 and the backprojected image from Step 4:

![](img/dd555effd38151c67af30d84800c554a_185_3.png)

Step 6: Update the current image pixel by pixel (using point-by-point multiplication, not matrix multiplication):

![](img/dd555effd38151c67af30d84800c554a_186_0.png)

## Example 7

Use a Bayesian method to find a stable solution of the system

$$
\begin{cases} x_1 + 0.01x_2 = 1.2 \\ x_1 + 0.001x_2 = 1. \end{cases}\tag{6.132}
$$

### Solution

If we consider the potential measurement errors, the system of equations can be written as

$$
\begin{cases} x_1 + 0.01x_2 = 1.2 + \delta_1 \\ x_1 + 0.001x_2 = 1 + \delta_2. \end{cases}\tag{6.133}
$$

The solution of this modified system is given as

$$
\begin{cases} x_1 = 0.978 - 0.111\delta_1 + 1.11\delta_2 \\ x_2 = 22.22 + 111.1\delta_1 - 111.1\delta_2. \end{cases}\tag{6.134}
$$

It is seen that \(x_2\) is sensitive to measurement noise. Let us assume a priori that “\(x_1\) and \(x_2\) are close” and solve this problem using the Bayesian method. Here, a prior is a probability distribution representing knowledge or belief about an unknown quantity a priori, that is, before any data have been observed. First, we set up an objective function and use the prior knowledge as a penalty term:

$$
F(x_1, x_2) = (x_1 + 0.01x_2 - 1.2 - \delta_1)^2 + (x_1 + 0.001x_2 - 1 - \delta_2)^2 + \beta(x_1 + x_2)^2.\tag{6.135}
$$

Note that \(\beta\) in this expression is not a Lagrange multiplier, but a preassigned constant. To minimize \(F(x_1, x_2)\), we set \(\partial F/\partial x_1 = 0\) and \(\partial F/\partial x_2 = 0\). This results in a *different* problem:

$$
\begin{bmatrix} 2+\beta & 0.011-\beta \\ 0.011-\beta & 0.01^2 + 0.001^2 + \beta \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} = \begin{bmatrix} (1.2+\delta_1) + (1+\delta_2) \\ (0.01)(1.2+\delta_1) + (0.001)(1+\delta_2) \end{bmatrix}.\tag{6.136}
$$

The solution of this system depends on the value of \(\beta\), as well as the values of \(\delta_1\) and \(\delta_2\). Some MAP solutions are listed in the following two tables:

