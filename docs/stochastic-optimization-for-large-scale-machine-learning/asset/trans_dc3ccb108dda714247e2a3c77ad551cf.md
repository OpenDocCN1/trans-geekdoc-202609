

where `s[k]` is the step direction and `d[k]` is the step size along that direction. The process of finding `d[k]` is also called as line search because of finding the value of step size along the step direction. The descent method is a method in which the value of a function decreases with every iteration, i.e., suppose function `f` is to be minimized then for `(k + 1)^(th)` iteration

$$
\begin{array}{l} {f(w_{k + 1}) < f(w_{k})} \\\\ \end{array}
$$  

except when `w[k]` is optimal. `s[k]` in a descent method must satisfy the following equation:

$$
\begin{array}{l} {\nabla f{(w_{k})}^{T}s_{k} < 0} \\\\ \end{array}
$$  

(2.38)

This means that the search direction should make an acute angle with the negative of gradient of function. Such a direction is known as a descent direction. A general algorithm for a descent optimization method is given by [Algorithm 1](#03chap_02.xhtml#algorithm_1). The step size and step direction can be found by separate methods or by a single method, and other exit criteria can be tried.

![](Images/algo1.jpg)

Some methods for finding the step size are given below:

### 2.4.1 Exact Line Search Method

In this method \[102\] of finding the step size (`d`), an exact optimization problem is solved to minimize `f` along the ray {`w`+`d**s`|`d`>0}:

$$
\begin{array}{l} {d = \\underset{v \\geq 0}{argmin}\\quad f(w + vs)} \\\\ \end{array}
$$  

(2.39)

The limitation of exact line search method is that it takes a lot of overhead for large problems. So, generally this method is not used for large problems.

### 2.4.2 Backtracking Line Search

Backtracking Line Search\[[22](#bib.xhtml#refbib_22)\] is an inexact line search method where instead of solving the exact optimization problem, a set of values for step size, are tried along the ray {`w`+`d**s`|`d`>0}. The backtracking line search algorithm is given in [Algorithm 2](#03chap_02.xhtml#algorithm_2).

![](Images/algo2.jpg)

This method is called as backtracking line search method because it starts with unit size for step size and then decreases its value by a factor of `β`. Small value of `β` (0.1) corresponds to very crude search and large value (0.9) to less crude. The typical values of `α` are between 0.01 and 0.3, i.e., 1% to 30% decrease of prediction in `f` is accepted based on linear exploration.

### 2.4.3 Constant Step Size

This is the simplest method of finding the step length. In order to get the value of step size no optimization problem is solved rather a constant value (generally `d` = 1) is used as a step size. For larger value, the convergence is uncertain. For smaller value, the convergence is slower but certain in convex functions.

### 2.4.4 Lipschitz and Strong Convexity Constants

Lipschitz (`L`) and strong convexity (`μ`) constants can also be used for calculating step sizes. These constants helps in easy calculation of step sizes but depends on correct estimation of `L` and `μ`. The main disadvantage of this method is that sometimes, these constants are not available. Using these constants, step size can be calculated as \[115\]:

$$
\begin{array}{l} {d = \\frac{1}{L}\\quad\\text{and}\\quad d = \\frac{2}{L + \\mu},} \\\\ \end{array}
$$  

(2.40)

These expressions for `d`, can change depending upon the implementation.

### 2.4.5 Trust Region Method

In Trust Region (TR) method \[[24](#bib.xhtml#refbib_24)\], a step direction and a step size is selected, then if the step is successful in some sense then the step is accepted else rejected and another step direction and step size is found. Here an approximate model (`m[k]`) of a function (`f`) to be minimized is taken and solved to get the solution. The region around the current iterate in which the model has good approximation of function is called as trust-region. A basic Trust Region algorithm is given by [Algorithm 3](#03chap_02.xhtml#algorithm_3). Typically used values are `η[v]` = 0.75, `η[s]` = 0.25, `σ[i]` = 2 and `σ[d]` = 0.5.

![](Images/algo3.jpg)

Some optimization methods for finding the step direction are given below:

### 2.4.6 Gradient Descent Method

Gradient Descent method\[[20](#bib.xhtml#refbib_20)\] is also known as Steepest Descent (SD) method, is a first order optimization method. SD method is based on the observation that a function decreases fastest on moving along the direction of negative gradient of the function. In this method, the step direction is taken as negative of gradient, i.e.,

$$
\begin{array}{l} {s_{k}^{GD} = - \\nabla f(w_{k})} \\\\ \end{array}
$$  

(2.43)

and step size can be determined by either exact or backtracking line search. So, substituting the values of step size and step direction into the Algorithm 1., it gives Gradient Descent Algorithm. SD method generally exhibits approximately linear convergence. On using backtracking line search, the parameters `α` and `β` have noticeable effect over the convergence rate but it does not have dramatic effect. Advantage of this method is its simplicity, it does not require second order derivative and every iteration is inexpensive. Disadvantages are: it is often slow, depends upon scaling and can't handle non-differentiable problems.

### 2.4.7 Newton Method

For Newton's method\[29\], the step direction is given by

$$
\begin{array}{l} {s_{k}^{N} = - \\left( {\\nabla^{2}f(w_{k})} \\right)^{- 1}\\nabla f(w_{k})} \\\\ \end{array}
$$  

(2.44)

is called as Newton step which is a descent direction. When step size is taken as `d` = 1, then it is called as pure Newton method, else called as damped Newton or guarded Newton method. On replacing the step direction and method to find step size, in Algorithm 1, it gives algorithm for the Newton method. In general, Newton method has quadratic rate of convergence when `d` = 1. Advantages of Newton method are (1) it is affine invariant to the choice of coordinates or condition number, (2) scales with problem size, (3) has fast convergence and (4) it is independent of algorithm parameters. Disadvantages of Newton method are (1) it need second order derivative, (2) high cost of computing and (3) storing the Hessian and calculating step direction.

### 2.4.8 Gauss-Newton Method

Gauss-Newton method\[[47](#bib.xhtml#refbib_47)\] is an iterative optimization method for least squares problems which are of the form:

$$
\begin{array}{l} {\\underset{w}{\\min}\\quad f(w) = \\frac{1}{2}{\\sum\\limits\_{j = 1}^{m}r_{j}^{2}}(w)} \\\\ \end{array}
$$  

(2.45)

where `w` ∈ ℝ^(`n`) and `r[j]`:ℝ^(`n`)→ℝ are residual functions.

Suppose `r`:ℝ^(`n`)→ℝ^(`m`) is a residual vector defined by

$$
\begin{array}{l} {r(w) = (r_{1}(w),r_{2}(w),...,r_{m}(w))} \\\\ \end{array}
$$  

So eq. (2.45) becomes:

$$
\begin{array}{l} {\\underset{w}{\\min}\\quad f(w) = \\frac{1}{2} \\parallel r(w) \\parallel^{2}} \\\\ \end{array}
$$  

(2.46)

From eq. (2.46), the gradient and Hessian can be expressed as:

$$
\begin{array}{l} \\begin{array}{ll} {\\nabla f(w)} & {= {\\sum\\limits\_{j = 1}^{m}r_{j}}(w)\\nabla r_{j}(w)} \\\\ & {= J{(w)}^{T}r(w)} \\\\ \\end{array} \\\\ \end{array}
$$  

(2.47)

$$
\begin{array}{l} \\begin{array}{l} {\\nabla^{2}f(w) = J{(w)}^{T}J(w) + {\\sum\\limits\_{j = 1}^{m}r_{j}}(w)\\nabla^{2}r_{j}(w)} \\\\ \\end{array} \\\\ \end{array}
$$  

(2.48)

For small value of ∇²`r[j]`(`w`) or residuals (`r[j]`(`w`)), eq. (2.48) simplifies to,

$$
\begin{array}{l} \\begin{array}{l} {\\nabla^{2}f(w) = J{(w)}^{T}J(w)} \\\\ \\end{array} \\\\ \end{array}
$$  

(2.49)

Now using gradient and Hessian, for least squares problem, eq. (2.44) gives Gauss-Newton step direction for the `(k + 1)^(th)` iteration as:

$$
\begin{array}{l} \\begin{array}{l} {s_{k}^{G} = - \\left( {J{(w_{k})}^{T}J(w_{k})} \\right)^{- 1}J{(w_{k})}^{T}r(w_{k})} \\\\ \\end{array} \\\\ \end{array}
$$  

(2.50)

For small residual problem, the convergence rate is close to quadratic, otherwise not even linear is guaranteed.

### 2.4.9 Levenberg-Marquardt Method

