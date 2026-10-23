
$$
f(\mathbf{x}) = \sum_{i=1}^{n} x_i f(\mathbf{e}_i)\tag{B.5}
$$

Based on Eq. (B.5), we see that we can represent a linear function as an inner product:

$$
f(\mathbf{x}) = \mathbf{a}^{\top} \mathbf{x}\tag{B.6}
$$

where \(a_i = f(\mathbf{e}_i)\) for \(i = 1,\ldots,n\). For example, consider the linear function that computes the average of its arguments, \(f(\mathbf{x}) = (x_1 + \cdots + x_n)/n\). This can be represented by \(f(\mathbf{x}) = \mathbf{a}^{\top} \mathbf{x}\), where \(\mathbf{a} = (1/n)\mathbf{1}_n = (1/n, \cdots, 1/n)\).

We can extend the definition of affine to handle functions that map vectors to vectors, \(f : \mathbb{R}^m \to \mathbb{R}^n\), by noting

$$
f(\mathbf{x}) = \mathbf{A}^{\top} \mathbf{x} + \mathbf{b}\tag{B.7}
$$

where \(\mathbf{A}\) is an \(m \times n\) matrix and \(\mathbf{b}\) is an \(n \times 1\) vector. See Chapter C for details.

### B.2.1.5 Nonlinear functions

Most functions are nonlinear. For example, consider the function that computes the maximum of its arguments, \(f(\mathbf{x}) = \max_i x_i\). This is not linear. The easiest way to show this is to construct a counter example. Let \(\mathbf{x} = (1, -1)\), \(\mathbf{y} = (-1, 1)\), \(c_1 = c_2 = 1\). Then

$$
f(c_1\mathbf{x} + c_2\mathbf{y}) = 0 \neq c_1 f(\mathbf{x}) + c_2 f(\mathbf{y}) = 2\tag{B.8}
$$

However, many functions are locally linear around a point (see Sec. B.4.5 for details).

### B.2.1.6 Quadratic functions

A scalar-argument quadratic function has the form

$$
f(x) = a x^2 + b x + c\tag{B.9}
$$

We can use a technique called **completing the square** to manipulate this equation as follows:

$$
a x^2 + b x + c = a(x - h)^2 + k\tag{B.10}
$$

$$
h = -\frac{b}{2a}\tag{B.11}
$$

$$
k = c - \frac{b^2}{4a}\tag{B.12}
$$

In the vector-argument case, a quadratic function is defined as follows:

$$
f(\mathbf{x}) = \mathbf{x}^{\top} \mathbf{A} \mathbf{x} + \mathbf{x}^{\top} \mathbf{b} + c\tag{B.13}
$$

For example, consider the family tree of the Simpsons, shown in Fig. B.4. Let \(\mathcal{V}_m\) be the set of males, \(\mathcal{V}_f\) be the set of females, and \(\mathcal{V} = \mathcal{V}_m \cup \mathcal{V}_f\) be all the members of the family. The diagram encodes several binary relations. For example, the symmetric relation “married-to” can be represented as the set of pairs

$$
R_{\text{married}} = \{(\text{Clancy}, \text{Jackie}), (\text{Jackie}, \text{Clancy}), (\text{Homer}, \text{Marge}), (\text{Marge}, \text{Homer})\}\tag{B.18}
$$

We see that \(R_{\text{married}} \subseteq \mathcal{V} \times \mathcal{V}\).

The binary one-to-many relation “father-of” can be represented as the set of pairs

$$
R_{\text{father-of}} = \{(\text{Clancy}, \text{Marge}), (\text{Clancy}, \text{Selma}), (\text{Homer}, \text{Bart}), (\text{Homer}, \text{Lisa}), (\text{Homer}, \text{Maggie})\}\tag{B.19}
$$

We see that \(R_{\text{father-of}} \subseteq \mathcal{V}_m \times \mathcal{V}\).

We can represent binary relations as **graphs**, where each node is an object in the domain, and there is an \(i \to j\) edge if \((i,j) \in R\). For example, Fig. B.5(a) represents the symmetric married-to relation as an undirected **bipartite graph**, with males on one side and females on the other. Fig. B.5(b) shows the asymmetric relation “father-of” using a directed graph. Each graph can be represented as an \(N \times N\) **adjacency matrix** \(\mathbf{M}\), where \(N = |\mathcal{V}|\) is the number of nodes, and \(M_{ij} = 1\) iff there is an \(i \to j\) edge. Sparse matrices (with many zeros) correspond to sparse graphs (with many missing edges) and vice versa. Also, block structure in the matrix corresponds to structure in the graph.

We can also have higher-order relations. Formally, a \(k\)-ary relation is a set of \(k\)-tuples, \(R \subseteq \mathcal{V} \times \mathcal{V} \cdots \mathcal{V}\). These can be represented graphically using **hypergraphs**.

## B.3 Matrix calculus

The topic of **calculus** concerns computing “rates of change” of functions as we vary their inputs. It is of vital importance to machine learning, as well as almost every other numerical discipline. In this section, we review some standard results. In some cases, we use some concepts and notation from matrix algebra, which we cover in Chapter C. For more details on these results from a deep learning perspective, see [PHI18].

### B.3.1 Derivatives

Consider a scalar-argument function \(f : \mathbb{R} \to \mathbb{R}\). We define its **derivative** at a point \(x\) to be the quantity

$$
f'(x) \triangleq \lim_{h \to 0} \frac{f(x+h)-f(x)}{h}\tag{B.20}
$$

We can compute a **finite difference** approximation to the derivative by using a finite step size \(h\), as follows:

$$
f'(x) \equiv \lim_{h\to0}\underbrace{\frac{f(x+h)-f(x)}{h}}_{\text{forward difference}} = \lim_{h\to0}\underbrace{\frac{f(x+h/2)-f(x-h/2)}{h}}_{\text{central difference}} = \lim_{h\to0}\underbrace{\frac{f(x)-f(x-h)}{h}}_{\text{backward difference}}\tag{B.22}
$$

The smaller the step size \(h\), the better the estimate, although if \(h\) is too small, there can be errors due to numerical cancellation.

We can think of differentiation as an operator that maps functions to functions, \(D(f)=f'\), where \(f'(x)\) computes the derivative at \(x\) (assuming the derivative exists at that point). The use of the prime symbol \(f'\) to denote the derivative is called **Lagrange notation**. The second derivative function, which measures how quickly the gradient is changing, is denoted by \(f''\). The \(n\)'th derivative function is denoted \(f^{(n)}\).

Alternatively, we can use **Leibniz notation**, in which we denote the function by \(y = f(x)\), and its derivative by \(\frac{dy}{dx}\) or \(\frac{d}{dx}f(x)\). To denote the evaluation of the derivative at a point \(a\), we write \(\left.\frac{df}{dx}\right|_{x=a}\).

### B.3.2 Gradients

We can extend the notion of derivatives to handle vector-argument functions, \(f : \mathbb{R}^n \to \mathbb{R}\), by defining the **partial derivative** of \(f\) with respect to \(x_i\) to be

$$
\frac{\partial f}{\partial x_i} = \lim_{h\to0}\frac{f(\mathbf{x}+h\mathbf{e}_i)-f(\mathbf{x})}{h}\tag{B.23}
$$

where \(\mathbf{e}_i\) is the \(i\)'th unit vector.

The **gradient** of a function at a point \(\mathbf{x}\) is the vector of its partial derivatives:

$$
\mathbf{g} = \frac{\partial f}{\partial \mathbf{x}} = \nabla f = \begin{pmatrix}\frac{\partial f}{\partial x_1}\\ \vdots \\\frac{\partial f}{\partial x_n}\end{pmatrix}\tag{B.24}
$$

To emphasize the point at which the gradient is evaluated, we can write

$$
\mathbf{g}(\mathbf{x}^*) \triangleq \left.\frac{\partial f}{\partial \mathbf{x}}\right|_{\mathbf{x}^*}\tag{B.25}
$$

We see that the operator \(\nabla\) (pronounced “nabla”) maps a function \(f : \mathbb{R}^n \to \mathbb{R}\) to another function \(\mathbf{g} : \mathbb{R}^n \to \mathbb{R}^n\). Since \(\mathbf{g}(\cdot)\) is a vector-valued function, it is known as a **vector field**. By contrast, the derivative function \(f'\) is a **scalar field**.

### B.3.3 Directional derivative

The **directional derivative** measures how much the function \(f : \mathbb{R}^n \to \mathbb{R}\) changes along a direction \(\mathbf{v}\) in space. It is defined as follows

$$
D_{\mathbf{v}}f(\mathbf{x}) = \lim_{h\to0}\frac{f(\mathbf{x}+h\mathbf{v})-f(\mathbf{x})}{h}\tag{B.26}
$$

So we can see that we can approximate this numerically using just 2 calls to **f**.

The **vector Jacobian product** or **VJP** is defined to be the operation that corresponds to left-multiplying the Jacobian matrix \(\mathbf{J}\in\mathbb{R}^{m\times n}\) by a vector \(\mathbf{u}\in\mathbb{R}^{m}\):

$$
\mathbf{u}^{\mathsf{T}}\mathbf{J}_f(\mathbf{x})=\mathbf{u}^{\mathsf{T}}\left(\frac{\partial f}{\partial x_1},\ldots,\frac{\partial f}{\partial x_n}\right)=\left(\mathbf{u}\cdot\frac{\partial f}{\partial x_1},\ldots,\mathbf{u}\cdot\frac{\partial f}{\partial x_n}\right)\tag{B.32}
$$

The JVP is more efficient if \(m\ge n\), and the VJP is more efficient if \(m\le n\). See Sec. **13.3** for details on how this can be used to perform automatic differentiation in a computation graph such as a DNN.

### B.3.5.2 Jacobian of a composition

Sometimes it is useful to take the Jacobian of the composition of two functions. Let \(h(\mathbf{x})=g(f(\mathbf{x}))\). By the chain rule of calculus, we have

$$
\mathbf{J}_h(\mathbf{x})=\mathbf{J}_g(f(\mathbf{x}))\mathbf{J}_f(\mathbf{x})\tag{B.33}
$$

For example, suppose \(f:\mathbb{R}\to\mathbb{R}^2\) and \(g:\mathbb{R}^2\to\mathbb{R}^2\). We have

$$
\frac{\partial g}{\partial x}=\begin{pmatrix}\frac{\partial}{\partial x}g_1(f_1(x),f_2(x))\\[2pt]\frac{\partial}{\partial x}g_2(f_1(x),f_2(x))\end{pmatrix}=\begin{pmatrix}\frac{\partial g_1}{\partial f_1}\frac{\partial f_1}{\partial x}+\frac{\partial g_1}{\partial f_2}\frac{\partial f_2}{\partial x}\\[2pt]\frac{\partial g_2}{\partial f_1}\frac{\partial f_1}{\partial x}+\frac{\partial g_2}{\partial f_2}\frac{\partial f_2}{\partial x}\end{pmatrix}\tag{B.34}
$$

$$
=\frac{\partial g}{\partial f}\frac{\partial f}{\partial x}=\begin{pmatrix}\frac{\partial g_1}{\partial f_1}&\frac{\partial g_1}{\partial f_2}\\\frac{\partial g_2}{\partial f_1}&\frac{\partial g_2}{\partial f_2}\end{pmatrix}\begin{pmatrix}\frac{\partial f_1}{\partial x}\\\frac{\partial f_2}{\partial x}\end{pmatrix}\tag{B.35}
$$

### B.3.6 Hessian

For a function \(f:\mathbb{R}^n\to\mathbb{R}\) that is twice differentiable, we define the **Hessian matrix** as the (symmetric) \(n\times n\) matrix of second partial derivatives:

$$
\mathbf{H}=\frac{\partial^2 f}{\partial \mathbf{x}^2}=\nabla^2 f=\begin{pmatrix}\frac{\partial^2 f}{\partial x_1^2}&\cdots&\frac{\partial^2 f}{\partial x_1\partial x_n}\\\vdots&\ddots&\vdots\\\frac{\partial^2 f}{\partial x_n\partial x_1}&\cdots&\frac{\partial^2 f}{\partial x_n^2}\end{pmatrix}\tag{B.36}
$$

We see that the Hessian is the Jacobian of the gradient.

### B.3.7 Gradients of commonly used functions

In this section, we list without proof the gradients of certain widely used functions.

### B.3.7.1 Functions that map scalars to scalars

Consider a differentiable function \(f:\mathbb{R}\to\mathbb{R}\). Here are some useful identities from scalar calculus, which you should already be familiar with.
