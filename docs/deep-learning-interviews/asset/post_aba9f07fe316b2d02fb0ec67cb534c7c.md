
probability of the observed data. Find the Likelihood function symbolically using sympy. Convert the SymPy representation to a purely Numpy based callable function with a Lambda expression. Evaluate the Likelihood function at $\theta=0.5$ with 50 successful trials out of 100 .

2. Prior: The Beta Distribution. Define the Beta distribution which will act as our **prior** distribution symbolically using sympy. Convert the SymPy representation to a purely Numpy based callable function. Evaluate the Beta Distribution at $\theta=0.5, a: 2, b: 7$.

3. Plot the Beta distribution, using the Numpy based function.

4. Posterior: Find the **posterior** distribution by multiplying our Beta prior by the Binomial Likelihood symbolically using sympy. Convert the SymPy representation to a purely Numpy based callable function. Evaluate the Posterior Distribution at $\theta:0.5$, $a:2, b:7$.

5. Plot the posterior distribution, using the Numpy based function.

6. Show that the posterior distribution has the same functional dependence on $\theta$ as the prior, and it is just **another Beta distribution**.

7. Given:
   - **Prior**: Beta($\theta \ |a=2, b=7)=56\theta\left(-\theta+1\right)^{6}$ and:
   - **Likelihood**: Bin($r=3|n=6, \theta ~$)$=19600 \theta^{3}\left(-\theta+1\right)^{47}$

   find the resulting posterior distribution and plot it.

## 5.3 Solutions

### 5.3.1 Algorithmic differentiation, Gradient descent
### 5.3.2 Numerical differentiation

**SOL-100 CH.SOL- 5.1.**

1. The formulae is:

$$f^{\prime}(x)\approx\frac{f(x+h)-f(x)}{h} . \tag { 5 . 2 7 }$$

2. *The main problem with this formulae is that it suffers from numerical instability for small values of $h$.*

3. *In some numerical software systems, the number $\sqrt{2}$ may be represented as the a floating point number $\approx 1.414213562$. Therefore, the result of:*

$float(\sqrt{(\sqrt{2})}) * float(\sqrt{(\sqrt{2})})$ may equal $\sim 2.000000446$.

# **SOL-101** ✏ **CH.SOL- 5.2.**

1. *The instantaneous rate of change equals:*

$\underset{h \to 0}{\lim} \frac{f(a + h) - f(a)}{a + h - a}$. (5.28)

2. *The instantaneous rate of change of $f(x)$ at $a$ is also commonly known as the tangent line of $f(x)$ at $a$.*

3. *Given a function $f(x)$ and a point $a$, the tangent (Fig. 5.12) line of $f(x)$ at $a$ is: a line that touches $f(a)$ but does not cross $f(x)$ (sufficiently close to $a$).*

![](img/574135cb1d7125b50cf484d943cdd676_165_0.png)

![](img/574135cb1d7125b50cf484d943cdd676_166_0.png)

## **5.3.3 Directed Acyclic Graphs**

**SOL-102 ✍️ CH.SOL- 5.3.**

1. The definition is:

$$ f'(c) = \lim_{h \to 0} \frac{f(c + h) - f(c)}{h}. $$

2. If we traverse the graph 5.3 from left to right we derive the following function:

$$ g(x) = \frac{1}{\sqrt{x}}. \tag{5.29} $$

$$\begin{aligned} f'(9) &= \lim_{h \to 0} \frac{1 / \sqrt{9 + h} - 1 / \sqrt{9}}{h} \\ &= \lim_{h \to 0} \frac{\sqrt{9} - \sqrt{9 + h}}{\sqrt{9} \cdot \sqrt{9 + h} \cdot h} \\ &= \lim_{h \to 0} \frac{(3 - \sqrt{9 + h})(3 + \sqrt{9 + h})}{3 \sqrt{9 + h} \cdot (3 + \sqrt{9 + h}) \cdot h} \\ &= \lim_{h \to 0} \frac{9 - (9 + h)}{9 \sqrt{9 + h} \cdot h + 3 \cdot (9 + h) \cdot h} \\ &= \frac{1}{-9 \cdot 3 + 3 \cdot 9} \\ &= -\frac{1}{54} \end{aligned}$$

**SOL-103 ✍️ CH.SOL- 5.4.**

1. The function $g(x) = 2x^2 - x + 1$ represents the expression graph depicted in 5.4.

2. By the definition:

$$f'(x) = \lim _ { h \to 0 } \frac { f ( x + h ) - f ( x ) } { x + h - x }$$

$$ = \lim _ { h \to 0 } \frac { 2 ( x + h ) ^ { 2 } - ( x + h ) + 1 - 2 x ^ { 2 } + x - 1 } { h }$$

$$ = \lim _ { h \to 0 } \frac { 2 ( x ^ { 2 } + 2 x h + h ^ { 2 } ) - x - h + 1 - 2 x ^ { 2 } + x - 1 } { h }$$

$$ = \lim _ { h \to 0 } \frac { 2 x ^ { 2 } + 4 x h + 2 h ^ { 2 } - x - h + 1 - 2 x ^ { 2 } + x - 1 } { h }$$

$$ = \lim _ { h \to 0 } \frac { 4 x h + 2 h ^ { 2 } - h } { h }$$

$$ = \lim _ { h \to 0 } 4 x + 2 h - 1$$

$$ = 4 x - 1 .$$

![](img/574135cb1d7125b50cf484d943cdd676_167_0.png)

![](img/574135cb1d7125b50cf484d943cdd676_167_1.png)

## 5.3.4 The chain rule

**SOL-104 CH.SOL- 5.5.**

1. The chain rule states that the partial derivative of $E = E ( x , y )$ with respect to $x$ can be calculated via another variable $y = y ( x )$, as follows:

$$\frac { \partial E } { \partial x } = \frac { \partial E } { \partial y } \cdot \frac { \partial y } { \partial x }$$

2. For instance, the chain rule $[ 8 ]$ is applied in neural networks to calculate the change in its weights resulting from tuning the cost function. This derivative is calculated via a chain of partial derivatives (e.g. of the activation functions).

## **5.3.5**      Taylor series expansion

**SOL-105 CH.SOL- 5.6.**

1.

$$\frac {1}{1-x} = \sum _ {n = 0} ^ {\infty} x ^ {n} = 1 + x + x ^ {2} + x ^ {3} \quad (5.32) \, (when - 1 < x < 1)$$

2.

$$e ^ {x} = \sum _ {n = 0} ^ {\infty} \frac {x ^ {n}}{n !} = 1 + x + \frac {x ^ {2}}{2 !} + \frac {x ^ {3}}{3 !} + \cdots$$   (5.33)

3.

$$\sin x = \sum _ {n = 0} ^ {\infty} \frac {(- 1) ^ {n}}{(2n + 1) !} x ^ {2n + 1} = x - \frac {x ^ {3}}{3 !} + \frac {x ^ {5}}{5 !} - \cdots$$  (5.34)

4.

$$\cos x = \sum _ {n = 0} ^ {\infty} \frac {(- 1) ^ {n}}{(2n) !} x ^ {2n} = 1 - \frac {x ^ {2}}{2 !} + \frac {x ^ {4}}{4 !} - \cdots$$  (5.35)

**SOL-106 CH.SOL- 5.7.**

$$\log x = \sum _ {n = 1} ^ {\infty} \frac {(- 1) ^ {n + 1} (x - 1) ^ {n}}{n} = (x - 1) - \frac {(x - 1) ^ {2}}{2} + \frac {(x - 1) ^ {3}}{3} - \frac {(x - 1) ^ {4}}{4} + \cdots$$  (5.36)

**SOL-107 CH.SOL- 5.8.**

*In this case, all derivatives can be computed:*

$$\begin{aligned} & f^{0}(x)=5 x^{2}-11 x+1, \\ & f^{0}(-3)=79, \\ & f^{1}(x)=10 x-11, \\ & f^{1}(-3)=-41, \\ & f^{2}(x)=10, \\ & f^{2}(-3)=10, \\ & f^{n}(x)=0, \forall n \geq 3 .\end{aligned}\tag{5.37}$$

**SOL-108**  CH.SOL- 5.9.

*The immediate answer is 1. Refer to eq. 5.35 to verify this logical consequence .*

**SOL-109**  CH.SOL- 5.10.

*By employing eq. 5.36 , one can substitute x by $3 - x$ and generate the first 7 terms of the x-dependable outcome before assigning the point x = 1.*

## 5.3.6 Limits and continuity

**SOL-110**  CH.SOL- 5.11.

1. With an indeterminate form 0/0, L'Hopital's rule holds. We look at

$$\operatorname*{lim}_{x \rightarrow 3} \frac{3 x^{2} e^{x^{3}}}{3} = 9 e^{27},$$

which equals to the original limit.

2. Again, we yield 0/0 at interim, so we look at the first order derivative

$$\operatorname*{lim}_{x \rightarrow 0} \frac{2 x e^{x}-1}{-3 \sin x-1}=1 .$$

The original limit is also equal to 1.

3. This time, the intermediate form is of \(\infty/\infty\) and L'Hopital applies as well. The quotient of the derivatives is

$$\frac{1 - \frac{1}{x}}{0.01x^{-99/100}} = 100(x - 1)x^{1/99}$$

As \(x \to \infty\), this goes to \(\infty\), so the original limit is equal to \(\infty\) also.

## 5.3.7     Partial derivatives

**SOL-111 \pencilicon CH.SOL- 5.12.**

1. True.

2. By treating y as constant, one can derive that

$$\frac{\partial g}{\partial x} = 2xy + y . \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad (5.38)$$

**SOL-112 \pencilicon CH.SOL- 5.13.**

1.

$$\begin{aligned} \nabla f(x,y) &= \frac{\partial f}{\partial x}\mathbf{i} + \frac{\partial f}{\partial y}\mathbf{j} & \quad (5.39) \\ &= \left(y^{2}+3 x^{2}\right) \mathbf{i}+\left(2 x y-2 y\right) \mathbf{j} \end{aligned}$$

2. It can be shown that \(\nabla g(x, y) = (2xy + y^{2}) \mathbf{i} + (x^{2} + 2xy - 1) \mathbf{j}\) at \((-1, 0)\) equals \((0, 0)\). According to the definition of directional derivative:

$$\frac{(0,0) \cdot (1,1)}{|(1,1)|} = 0 \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad (5.40)$$

**SOL-113 CH.SOL- 5.14.**

$$\begin{gathered} \frac{\partial f}{\partial x}=6 \sin (x-y) \cos (x-y) \\ \frac{\partial f}{\partial y}=-6 \sin (x-y) \cos (x-y) \end{gathered}$$

(5.41)

**SOL-114 CH.SOL- 5.15.**

$$\begin{gathered} \frac{\partial z}{\partial x}=2 \cos x \sin y \\ \frac{\partial z}{\partial y}=2 \sin x \cos y \end{gathered}$$

(5.42)

## 5.3.8 Optimization

**SOL-115 CH.SOL- 5.16.**

1. The function is only defined where $x \neq - 2$, in the domain of: $(-\infty, -2) \cup (-2, +1)$.

2. By a simple quotient-based derivation:

$$f^{\prime}(x)=\frac{2(x+2)(2x-1)}{(x+2)^{4}}.$$

(5.43)

Namely, expect for the ill-defined $x = - 2$, the critical point of $x = 0.5$ should be considered. For $x > 0.5$, the derivative is positive and the function increases, in contrast to $x < 0.5$.

3. The requested coordinate is $(0.5, 0.2)$.

**SOL-116 CH.SOL- 5.17.**
