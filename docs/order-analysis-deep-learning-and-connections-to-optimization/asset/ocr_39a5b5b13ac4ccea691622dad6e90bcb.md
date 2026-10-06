# 24

# 2 -C Representing Functionals

**Fig. 2.1** Bishop-Phelps cone
$C(\ell)$ (see [68, Fig. 1])

![](bbox=[0.385, 0.073, 0.875, 0.278])

**Example 2.1** Choose $Y := \mathbb{R}^m$ with $m \in \mathbb{N}\setminus\{1\}$, and let $\|\cdot\|_2$ denote the Euclidean norm. Recall that the cone

$C_\ell := \{(y_1, \dots, y_m) \in \mathbb{R}^m \mid \|(y_1, \dots, y_{m-1})\|_2 \leq 2y_m^2\}$

is called Lorentz cone or second-order cone or ice cream cone. For every $y = (y_1, \dots, y_m) \in \mathbb{R}^m$, we have the equivalences

$\Longiff \|(y_1, \dots, y_{m-1})\|_2 \leq y_m \Longiff |y_1|^2 + \dots + |y_{m-1}|^2 \leq 2y_m^2, \ y_m \geq 0$
$\Longiff |y_1|^2 + \dots + |y_{m-1}|^2 \leq 2y_m^2, \ y_m \geq 0$
$\Longiff \|(y_1, \dots, y_m)\|_2^2 \leq 2y_m^2, \ y_m \geq 0$
$\Longiff \|(y_1, \dots, y_m)\|_2 \leq \sqrt{2} \ e^m^T y$
$\Longiff \|y\|_2 \leq \sqrt{2} \ e^m^T y$

with $e^m := (0, \dots, 0, 1) \in \mathbb{R}^m$ (see the proof in [68, Lemma 2.2, (a)). Consequently, the Lorentz cone is a Bishop-Phelps cone with $\ell := \sqrt{2}e^m$.

**Remark 2.1** [[74, Remark 2.1] It is obvious under the assumptions of Definition-2.1 that

$-C(\ell) = \{y \in Y \mid -\ell(y)\} = \{y \in Y \mid \ell(y) + \|y\|y \leq 0\}$.

In this book, the functional $\varphi_\ell : Y \to \mathbb{R}$

$\varphi_\ell(y) := \ell(y) + \|y\|y$ for all $y \in Y$

is called a Bishop-Phelps functional. Hence, we conclude

```
$-C(\ell) = \{y \in Y \mid \varphi_\ell(y) \leq 0\},$
```