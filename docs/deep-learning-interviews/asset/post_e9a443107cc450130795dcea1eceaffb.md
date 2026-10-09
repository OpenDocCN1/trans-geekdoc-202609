
![](img/574135cb1d7125b50cf484d943cdd676_157_0.png)

FIGURE 5.8: A typical binary classification problem.

1. Given the sigmoid function: $g(x) = \frac{1}{1 + e^{-x}}$, what is the expression for the hypothesis in logistic regression?
2. What is the decision boundary?
3. What does $h_\Theta(x) = 0.8$ mean?
4. Using an Autograd based Python program, implement both the forward and backward pass for the sigmoid activation function and evaluate its derivative at $x = 1$.
5. Using an Autograd based Python program, implement both the forward and backward pass for the ReLU activation function and evaluate its derivative at $x = 1$.

**PRB-124 CH.PRB-5.25.** Your friend, a veteran of the DL community, wants to implement a custom activation function using Autograd and asks for your help. Consider a function accepting two tensors as input and an output obeying the following mapping:

```python
(u, v) ↦ |uv|²
```

### 5.2.13 Dual numbers in AD

Dual numbers (DN) are analogous to complex numbers and augment real numbers with a dual element by adjoining an infinitesimal element $d$, for which $d^2=0$.

**PRB-125 CH.PRB-5.26.**

1. Explain how AD uses floating point numerical rather than symbolic expression.
2. Explain the notion of DN as introduced by ((2)).
3. What arithmetic operations are possible on DN?
4. Explain the relationship between a Taylor series and DN.

**PRB-126 CH.PRB-5.27.**

1. Expand the following function using DN:

$$
\sin(x + dx) \quad (5.23)
$$

2. With respect to the expression graph depicted in 5.9:

![](img/574135cb1d7125b50cf484d943cdd676_158_0.png)

   (a) Traverse the graph 5.9 and find the function $g(x)$ it represents.
   (b) Expand the function $g(x)$ using DN.

3. Show that the general identity:

$$
g(x + x\mathbf{d}) = g(x) + g'(x) x\mathbf{d} \quad (5.24)
$$

holds in this particular case too.

4. Using the derived DN, evaluate the function $g(x)$ at $x = 2$.
5. Using an Autograd based Python program implement the function and evaluate its derivative at $x = 2$.

**PRB-127❓ CH.PRB-5.28.**

With respect to the expression graph depicted in [5.10](https://link.springer.com/chapter/10.1007/978-3-031-19950-8#chapter-5.10):

![](img/574135cb1d7125b50cf484d943cdd676_159_0.png)

[FIGURE 5.10: An expression graph for $g(x)$. Constants are shown in gray, crossed-out since derivatives should not be propagated to constant operands.](https://link.springer.com/chapter/10.1007/978-3-031-19950-8#figure-5.10)

1. Traverse the graph [5.10](https://link.springer.com/chapter/10.1007/978-3-031-19950-8#chapter-5.10) and find the function $g(x)$ it represents.
2. Expand the function $g(x)$ using DN.
3. Using the derived DN, evaluate the function $g(x)$ at $x = 5$.
4. Using an AutoGrad based Python program implement the function and evaluate its derivative at $x = 5$.

### 5.2.14 Forward mode AD

**PRB-128❓ CH.PRB-5.29.**

When differentiating a function using forward-mode AD, the computation of such an expression can be computed from its corresponding directed a-cyclical graph by propagating the numerical values.

1. Find the function, $g(A,B,C)$ represented by the expression graph in 5.11.

![](img/574135cb1d7125b50cf484d943cdd676_160_0.png)

2. Find the partial derivatives for the function $g(x)$.

**PRB-129 CH.PRB-5.30.**

Answer the following given that a computational graph of a function has $N$ inputs and $M$ outputs.

1. True or False?
   - (a) Forward and reverse mode AD always yield the same result.
   - (b) In reverse mode AD there are fewer operations (time) and less space intermediates (memory).
   - (c) The cost for forward mode grows with $N$.
   - (d) The cost for reverse mode grows with $M$.

**PRB-130 CH.PRB-5.31.**

1. Transform the source code in code snippet 5.1 into a function $g(x_1, x_2)$.

CODE 5.1: A function, $g(x_1, x_2)$ in the C programming language.

```c
float g(float x1, float x2) {
    float v1, v2, v3, v4, v5;
    v1 = x1;
    v2 = x2;
    v3 = v1 * v2;
    v4 = ln(v1);
    v5 = v3 + v4;
    return v5;
}
```

2. Transform the function $g(x_1, x_2)$ into an expression graph.
3. Find the partial derivatives for the function $g(x_1, x_2)$.

### 5.2.15 Forward mode AD table construction

**PRB-131 CH.PRB-5.32.**

1. Given the function:

$$
f(x_1, x_2) = x_1 x_2 + \ln(x_1) \quad (5.25)
$$

and the graph 5.1, annotate each vertex (edge) of the graph with the partial derivatives that would be propagated in forward mode AD.

2. Transform the graph into a table that computes the function $g(x_1, x_2)$ evaluated at $(x_1, x_2) = (e^2, \pi)$ using forward-mode AD.
3. Write and run a Python code snippet to prove your results are correct.
4. Describe the role of seed values in forward-mode AD.
5. Transform the graph into a table that computes the derivative of $g(x_1, x_2)$ evaluated at $(x_1, x_2) = (e^2, \pi)$ using forward-mode AD for $x_1$ as the chosen independent variable.
6. Write and run a Python code snippet to prove your results are correct.

### 5.2.16 Symbolic differentiation

In this section, we introduce the basic functionality of the SymPy (SYMbolic Python) library commonly used for symbolic mathematics as a means to deepen your understanding in both Python and calculus. If you are using Sympy in a Jupyter notebook in Google Colab (e.g. https://colab.research.google.com/), then rendering sympy equations requires MathJax to be available within each cell output. The following is a hook function that will make this possible:

CODE 5.2: Sympy in Google Colab

```python
from IPython.display import Math, HTML

def enable_sympy_in_cell():
    display(Math('<script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.3/latest.js?config=default"></script>'))

get_ipython().events.register('pre_run_cell', enable_sympy_in_cell)
```

After successfully registering this hook, SymPy rendering (5.3) will work correctly:

CODE 5.3: Rendering Sympy in Google Colab

```python
import sympy
from sympy import *
init_printing()
x, y, z = symbols('x y z')
Integral(sqrt(1/x), (x, 0, oo))
```

It is also recommended to use the latest version of Sympy:

CODE 5.4: Updating Sympy

```bash
> pip install --upgrade sympy
```

### 5.2.17 Simple differentiation

**PRB-132 CH.PRB-5.33.**
Answer the following questions:

1. Which differentiation method is inherently prone to rounding errors?
2. Define the term symbolic differentiation.

**PRB-133 CH.PRB-5.34.**
Answer the following questions:

1. Implement the sigmoid function $\sigma(x) = \frac{1}{1 + e^{-x}}$ symbolically using a Python based SymPy program.
2. Differentiate the sigmoid function using SymPy and compare it with the analytical derivation $\sigma'(x) = \sigma(x)(1 - \sigma(x))$.
3. Using SymPy, evaluate the gradient of the sigmoid function at $x = 0$.
4. Using SymPy, plot the resulting gradient of the sigmoid function.

### 5.2.18 The Beta-Binomial model

**PRB-134 CH.PRB-5.35.**

You will most likely not be given such a long programming task during a face-to-face interview. Nevertheless, an extensive home programming assignment is typically given at many of the start-ups I am familiar with. You should allocate around approximately four to six hours to completely answer all questions in this problem.

We discussed the Beta-Binomial model extensively in chapter 3. Recall that the Beta-Binomial distribution is frequently used in Bayesian statistics to model the number of successes in $n$ trials. We now employ SymPy to do the same; demonstrate computationally how a prior distribution is updated to develop into a posterior distribution after observing the data via the relationship of the Beta-Binomial distribution.

Provided the probability of success, the number of successes after $n$ trials follows a binomial distribution. Note that the beta distribution is a conjugate prior for the parameter of the binomial distribution. In this case, the likelihood function is binomial, and a beta prior distribution yields a beta posterior distribution.

Recall that for the Beta-Binomial distribution the following relationships exist:

| Prior of $\theta$ | Beta($a,b$) |
|---|---|
| Likelihood | binomial $(n,\theta)$ |
| Posterior of $\theta$ | Beta $(a + x, b + n - x)$ |
| Posterior Mean | $(a + x)/(a + b + n - x)$ |

1. Likelihood: The starting point for our inference problem is the Likelihood, the
