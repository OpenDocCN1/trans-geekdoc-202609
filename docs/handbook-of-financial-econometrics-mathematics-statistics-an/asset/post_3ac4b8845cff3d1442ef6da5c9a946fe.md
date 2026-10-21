
popular models, are shown in Section 44.4. Conclusions are finally drawn in Section 44.5, with recommendations for future research.

## 44.2 Adaptive L_q SVM

### 44.2.1 Support vector machine

The general form of support vector machine is used to solve binary classification problem. Given a set of credit data points G = {(\vec{x}_i, y_i)}^n_{i=1}, where \vec{x}_i \in R^m is the ith input record and y_i \in {1,-1} is the corresponding observed result, the main goal of SVM is to find an optimal separating hyper-plane, which can be represented as \langle \vec{\omega}, \vec{x} \rangle + b = 0, and to maximize the separation margin (the distance between it and the nearest data point of each class), and to minimize the empirical classification error. Thus, the problem of seeking the optimal separating hyper-plane can be transformed into the following optimization problem:

min ½||\vec{\omega}||² + C \sum_{i=1}^n \xi_i, s.t. y_i(\vec{\omega}^T \phi(x_i) + b) \ge 1 - \xi_i, \xi_i \ge 0, \; i = 1, ..., n (44.1)

where variables \xi_i are the non-negative slack variables, representing the classification error; regularization parameter C is a constant denoting a trade-off between the maximum margin and the minimum empirical risk.

The above quadratic optimization problem can be solved by transforming it into Lagrangian function

L(\vec{\omega}, b, \xi, \alpha) = ½||\vec{\omega}||² + C \sum_{i=1}^n \xi_i - \sum_{i=1}^n \alpha_i (y_i(\vec{\omega}^T \phi(\vec{x}_i) + b) - 1 + \xi_i) - \sum_{i=1}^n \theta_i \xi_i (44.2)

where \alpha_i, \theta_i denote Lagrange multipliers; \alpha_i \ge 0 and \theta_i \ge 0.

At the optimal point, we have the following saddle point equations: \frac{\partial L}{\partial \vec{\omega}} = 0, \; \frac{\partial L}{\partial b} = 0 \; and \; \frac{\partial L}{\partial \xi_i} = 0,

which translate into \vec{\omega} = \sum_{i=1}^n \alpha_i y_i \phi(\vec{x}_i), \; \sum_{i=1}^n \alpha_i y_i = 0 \; and \; \alpha_i = C - \theta_i \; i = 1, ..., n. (44.3)

By substituting (44.3) into (44.2), and by replacing $(\phi(\vec{x}_i) \cdot \phi(\vec{x}_j))$ with kernel functions $k(\vec{x}_i, \vec{x}_j)$, we get the dual optimization problem

$$\max \sum_{i=1}^{n} \alpha_i - \frac{1}{2} \sum_{i=1}^{n} \sum_{j=1}^{n} \alpha_i \alpha_j y_i y_j k(\vec{x}_i, \vec{x}_j),$$
s.t. $\sum_{i=1}^{n} \alpha_i y_i = 0,$
$0 \le \alpha_i \le C, \quad i = 1, \dots, n.$
(44.4)

Commonly used kernel functions include polynomial, radial basis function (RBF) and sigmoid kernel, which are shown in (44.5), (44.6) and (44.7), respectively.

$k(\vec{x}, \vec{y}) = (\vec{x} \cdot \vec{y} + c)^d, \quad \text{for } d \in N, c \ge 0, \quad (44.5)$
$k(\vec{x}, \vec{y}) = \exp(-\gamma \|\vec{x} - \vec{y}\|^2), \quad \text{for } \gamma > 0, \quad (44.6)$
$k(\vec{x}, \vec{y}) = \tanh(\gamma (\vec{x} \cdot \vec{y}) + c), \quad \text{for } \gamma > 0, c \ge 0. \quad (44.7)$

On solving the dual optimization problem, solution $\alpha_i$ determines the parameters of the optimal hyper-plane. This leads to the decision function, expressed as

$$f(\vec{x}) = \operatorname{sgn}\left( \sum_{i=1}^{n} y_i \alpha_i k(\vec{x}_i, \vec{x}) + b \right), \quad (44.8)$$

where $b = y_j - \sum_{i=1}^{n} y_i \alpha_i k(x_i, x_j)$, for some $j$, $\alpha_i \le C$.

Usually, there is only a small subset of Lagrange multipliers $\alpha_i$ that is greater than zero in a classification problem. Training vectors having non-zero $\alpha_i^*$ are called support vectors; the optimal decision hyper-plane depends on them exclusively:

$$f(\vec{x}) = \operatorname{sgn}\left( \sum_{i \in SV} y_i \alpha_i^* k(\vec{x}_i, \vec{x}) + b^* \right). \quad (44.9)$$

### 44.2.2 Adaptive $L_q$ penalty SVM

The SVM model (44.1) or (44.4) and many other improved SVM are with fixed penalty forms, but different data structures are suitable for different types of penalty forms. Thus, Liu proposed an adaptive $L_q$ penalty SVM to find the best penalty q for different data structures (e.g., see Liu et al., 2007).

Under the general regularization framework, the standard SVM for binary classification problem can be changed as follows:

$$\min_{f} \frac{1}{n}\sum_{i=1}^{n} l(f(x_i),y_i)+\lambda\|f\|_{2}^{2}, \tag{44.10}$$

where $l(f(x_i),y_i)=[1-y_i f(x_i)]_{+}$ is the convex hinge loss; $\|f\|_{2}^{2}$, the $L_{2}$ penalty of f, is a regularization term serving as the roughness penalty of f, and $\lambda>0$ is the tuning parameter which controls the trade-off between the fitness of the data measured by l and the complexity of f in terms of $\|f\|_{2}^{2}$.

Based on the extended SVM model (44.10), the adaptive $L_{q}$ penalty SVM can be briefly described as:

$$\min \frac{1}{n}\sum_{i=1}^{n}c(-y_i)[1-y_i f(x_i)]_{+}+\lambda\|f\|_{q}^{q}, \tag{44.11}$$

where $f(x)=\sum_{d=1}^{m}\varpi_{d}B_{d}(x)$ is the decision function, and $c(+1)$ and $c(-1)$ are the costs for false positives and false negatives, respectively. Different from the standard binary SVM, there are two parameters $\lambda$ and $q$ to be tuned. Parameter $\lambda$, playing the same role as in the non-adaptive SVM, controls the trade-off between minimizing the hinge loss and the penalty on $f$. Parameter $q$ determines the penalty function on $f$. Here, $q\in(0,2]$ is considered as a tuning parameter, and it can be adaptively chosen by data, together with $\lambda$. The best $q$ is dependent on the nature of the data structure. If there are many noisy attributes of inputs, the $L_{q}$ penalty with $q\le1$ is chosen since it automatically chooses important attributes and removes the noisy ones. Otherwise, if all the attributes are important, $q>1$ is used to avoid any attributes deletion.

Like the standard SVM, $f(x)$ is the linear decision function. For binary classification, the decision function is denoted as $f_{k}(x)=\vec{\omega}_{k}^{T}x+b_{k}$, where $\vec{\omega}_{k}=(\varpi_{k1},\dots,\varpi_{km})^{T}$, and $k=1,2$. In order to obtain the unique solution, the coefficients are subject to $b_{1}+b_{2}=0$ and $\vec{\omega}_{1}+\vec{\omega}_{2}=0$. Then the optimization problem becomes

$$\min_{\{(\varpi_{k},b_{k})_{k=1,2}\}}\frac{1}{n}\sum_{i=1}^{n}\sum_{k=1}^{2}[\vec{\varpi}_{k}^{T}x+b_{k}+1]_{+}c(k\ne y_{i})+\lambda\sum_{k=1}^{2}\sum_{d=1}^{m}|\varpi_{kd}|^{q}\tag{44.12}$$ s.t. $b_{1}+b_{2}=0,\quad\varpi_{1d}+\varpi_{2d}=0\quad d=1,2,\dots,m.$

The final decision rule for classifying $x$ is $\operatorname{argmax}[f_{1}(x),f_{2}(x)]$.

## 44.3 ES-Based ALqG-SVM

### 44.3.1 Adaptive Lq SVM with Gauss kernel

When q = 2, the optimization problems (44.12) can be solved by quadratic programming (QP). When q = 1, (44.12) can be reduced to linear programming (LP). Many standard software packages are available to solve them. Except for these two special cases, the problem (44.12) is essentially a nonlinear programming (NLP) problem, which is hard to solve. Another problem is that when q < 1, function ||f||_q^q is not convex in \vec{w}. Therefore, standard optimization routines may fail to solve this problem. The LQA algorithm is proposed to solve this problem and minimize (44.12) via iterative quadratic optimization (e.g., see Liu et al., 2007). For fixed parameters (λ, q), the LQA algorithm to solve (44.12) can be summarized in the following three steps:

- **step 1:** Set l = 1 and the initial value η^(l);
- **step 2:** Let η^0 = η^(l). Minimize F(η) = η^T Q η + η^T L to obtain η^(l+1);
- **step 3:** Set l = l+1 and go to Step 2, until convergence.

Where η denotes the parameter vectors; F(η) is the Taylor first-order approximation of the objective function of model (44.12), where Q = Q_A1 + Q_B1 + Q_C1 + Q_C2 and L = L_A1 + L_A2 + L_B1 + L_B2. More details of the LQA algorithm are given in Liu et al. (2007).

Generally, training vector x_i is mapped into a higher (maybe infinite) dimensional space by function Φ(−). Then, the SVM finds a linear separating hyper-plane with the maximal margin in this higher dimensional space. There are several kernels proposed by researchers, and the Gauss kernel, shown in (44.13), is used more often in general cases and performs better than others (e.g., see Burges, 1998). Thus, the Gauss kernel is introduced in the adaptive L_q penalty SVM model to improve the performance of classification (e.g., see Sun et al., 2008).

$$k(\vec{x}, \vec{y}) = \exp(-||\vec{x} - \vec{y}||^2 / \sigma^2). \tag{44.13}$$

In the LQA algorithm, Gauss kernel is introduced in Q_A1 and Q_B1 in Step 2, which are defined as:

$$Q_{A1} = \frac{1}{4n} \sum_{i=1}^{n} \frac{c_{i1}}{|\eta^{0T} \tilde{x}_i + 1|} \tilde{x}_i \tilde{x}_i^T = \frac{1}{4n} \sum_{i=1}^{n} \hat{x}_i \hat{x}_i^T = Ker_{Q_{A1}}^{m \times m}, \tag{44.14}$$
