
## 1.5 Residual ANNs (continued)

**Definition 1.5.5 (Identity matrices).** Let $d \in \mathbb{N}$. Then we denote by $I_d \in \mathbb{R}^{d \times d}$ the identity matrix in $\mathbb{R}^{d \times d}$.

**Source code 1.20 (`code/res-ann.py`):** **PYTHON** code implementing a fully-connected **ResNet** in **PYTORCH**. The implemented model here corresponds to a fully-connected **ResNet** $(\Phi, V)$ where $l_0 = 3$, $l_1 = 10$, $l_2 = 20$, $l_3 = 10$, $l_4 = 1$, $\Phi = ((W_1, B_1), (W_2, B_2), (W_3, B_3), (W_4, B_4)) \in \big(\bigotimes_{k=1}^{4} (\mathbb{R}^{l_k \times l_{k-1}} \times \mathbb{R}^{l_k})\big)$, $S = \{(1,3)\}$, $V = (V_{r,k})_{(r,k) \in S} \in \big(\bigotimes_{(r,k) \in S} \mathbb{R}^{l_k \times r}\big)$, and $V_{1,3} = I_{10}$ (cf. Definition **1.5.5**).

```python
import torch
import torch.nn as nn

class ResidualANN(nn.Module):
    def __init__(self):
        super().__init__()
        self.affine1 = nn.Linear(3, 10)
        self.activation1 = nn.ReLU()
        self.affine2 = nn.Linear(10, 20)
        self.activation2 = nn.ReLU()
        self.affine3 = nn.Linear(20, 10)
        self.activation3 = nn.ReLU()
        self.affine4 = nn.Linear(10, 1)

    def forward(self, x0):
        x1 = self.activation1(self.affine1(x0))
        x2 = self.activation2(self.affine2(x1))
        x3 = self.activation3(x1 + self.affine3(x2))
        x4 = self.affine4(x3)
        return x4
```

**Example 1.5.6** (Example for Definition **1.5.2**). Let $l_0 = 1$, $l_1 = 1$, $l_2 = 2$, $l_3 = 2$, $l_4 = 1$, $S = \{(0,4)\}$, let

$$\Phi = ((W_1, B_1), (W_2, B_2), (W_3, B_3), (W_4, B_4)) \in \big(\bigotimes_{k=1}^{4} (\mathbb{R}^{l_k \times l_{k-1}} \times \mathbb{R}^{l_k})\big) \quad (1.146)$$

satisfy

$$W_1 = (1), \quad B_1 = (0), \quad W_2 = \begin{pmatrix} 1 \\ 2 \end{pmatrix}, \quad B_2 = \begin{pmatrix} 0 \\ 1 \end{pmatrix}, \quad (1.147)$$

$$W_3 = \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}, \quad B_3 = \begin{pmatrix} 0 \\ 0 \end{pmatrix}, \quad W_4 = \begin{pmatrix} 2 & 2 \end{pmatrix}, \quad \text{and} \quad B_4 = (1), \quad (1.148)$$

and let $V = (V_{r,k})_{(r,k) \in S} \in \bigotimes_{(r,k) \in S} \mathbb{R}^{l_k \times r}$, satisfy

$$V_{0,4} = (-1). \quad (1.149)$$

Then

$$(\mathcal{R}_{\dagger}^{\mathbf{R}}(\Phi, V))(5) = 28 \tag{1.150}$$

(cf. Definitions 1.2.4 and 1.5.4).

**Proof for Example 1.5.6.** Throughout this proof, let $x_0 \in \mathbb{R}^1$, $x_1 \in \mathbb{R}^1$, $x_2 \in \mathbb{R}^2$, $x_3 \in \mathbb{R}^2$, $x_4 \in \mathbb{R}^1$ satisfy for all $k \in \{1, 2, 3, 4\}$ that $x_0 = 5$ and

$$x_k = \mathfrak{M}_{\mathbf{1}_{(0,k)}(k) + \operatorname{id}_{\mathbb{R}^1 \mathbf{1}_{\{4\}}(k),k}(W_k x_{k-1} + B_k + \sum_{r \in \mathbb{N}_0, (r,k) \in S} V_{r,k} x_r) \tag{1.151}$$

Observe that (1.151) assures that

$$(\mathcal{R}_{\dagger}^{\mathbf{R}}(\Phi, V))(5) = x_4 \tag{1.152}$$

Next note that (1.151) ensures that

$$x_1 = \mathfrak{M}_{\mathbf{r},1}(W_1 x_0 + B_1) = \mathfrak{M}_{\mathbf{r},1}(5) \tag{1.153}$$

$$x_2 = \mathfrak{M}_{\mathbf{r},2}(W_2 x_1 + B_2) = \mathfrak{M}_{\mathbf{r},1}\left(\begin{pmatrix} 1 & 0 \\ 2 & 1 \end{pmatrix}\begin{pmatrix} 5 \\ 0 \end{pmatrix} + \begin{pmatrix} 0 \\ 1 \end{pmatrix}\right) = \mathfrak{M}_{\mathbf{r},1}\left(\begin{pmatrix} 5 \\ 11 \end{pmatrix}\right) = \begin{pmatrix} 5 \\ 11 \end{pmatrix} \tag{1.154}$$

$$x_3 = \mathfrak{M}_{\mathbf{r},2}(W_3 x_2 + B_3) = \mathfrak{M}_{\mathbf{r},1}\left(\begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}\begin{pmatrix} 5 \\ 11 \end{pmatrix} + \begin{pmatrix} 0 \\ 0 \end{pmatrix}\right) = \mathfrak{M}_{\mathbf{r},1}\left(\begin{pmatrix} 5 \\ 11 \end{pmatrix}\right) = \begin{pmatrix} 5 \\ 11 \end{pmatrix} \tag{1.155}$$

and

$$x_4 = \mathfrak{M}_{\mathbf{r},1}(W_4 x_3 + B_4 + V_{0,4} x_0) = \mathfrak{M}_{\mathbf{r},1}\left(\begin{pmatrix} 2 & 2 \end{pmatrix}\begin{pmatrix} 5 \\ 11 \end{pmatrix} + \begin{pmatrix} 1 \end{pmatrix} + (-1)\begin{pmatrix} 5 \end{pmatrix}\right) = \mathfrak{M}_{\mathbf{r},1}(28) = 28 \tag{1.156}$$

This and (1.152) establish (1.150). The proof for Example 1.5.6 is thus complete.

**Exercise 1.5.1.** Let $l_0 = 1$, $l_1 = 2$, $l_2 = 3$, $l_3 = 1$, $S = \{(0, 3), (1, 3)\}$, let

$$\Phi = ((W_1, B_1), (W_2, B_2), (W_3, B_3)) \in \left(\bigotimes_{k=1}^{3}(\mathbb{R}^{l_k \times l_{k-1}} \times \mathbb{R}^{l_k})\right) \tag{1.157}$$

satisfy

$$W_1 = \begin{pmatrix} 1 \\ 2 \end{pmatrix}, \quad B_1 = \begin{pmatrix} 3 \\ 4 \end{pmatrix}, \quad W_2 = \begin{pmatrix} -1 & 2 \\ 3 & -4 \\ -5 & 6 \end{pmatrix}, \quad B_2 = \begin{pmatrix} 0 \\ 0 \\ 0 \end{pmatrix} \tag{1.158}$$

$$W_3 = \begin{pmatrix} -1 & 1 & -1 \end{pmatrix}, \quad \text{and} \quad B_3 = \begin{pmatrix} -4 \end{pmatrix} \tag{1.159}$$

and let $V = (V_{r,k})_{(r,k) \in S} \in \bigotimes_{(r,k) \in S} \mathbb{R}^{l_k \times l_r}$ satisfy

$$V_{0,3} = \begin{pmatrix} 1 \end{pmatrix} \quad \text{and} \quad V_{1,3} = \begin{pmatrix} 3 & -2 \end{pmatrix} \tag{1.160}$$

Prove or disprove the following statement: It holds that

$$(\mathcal{R}_{\dagger}^{\mathbf{R}}(\Phi, V))(-1) = 0 \tag{1.161}$$

(cf. Definitions 1.2.4 and 1.5.4).

## 1.6 Recurrent ANNs (RNNs)

In this section we review RNNs, a type of ANNs designed to take sequences of data points as inputs. Roughly speaking, unlike in feedforward ANNs where an input is processed by a successive application of series of *different* parametric functions (cf. Definitions 1.1.3, 1.3.4, 1.4.5, and 1.5.4 above), in RNNs an input sequence is processed by a repeated application of the *same* parametric function whereby after the first application, each subsequent application of the parametric function takes as input a new element of the input sequence and a partial output from the previous application of the parametric function. The output of an RNN is then given by a sequence of partial outputs coming from the repeated applications of the parametric function (see Definition 1.6.2 below for a precise description of RNNs and cf., for instance, [4, Section 12.7], [60, Chapter 17] [63, Chapter 5], and [164, Chapter 10] for other introductions to RNNs).

The repeatedly applied parametric function in an RNN is typically called an *RNN node* and any *RNN architecture* is determined by specifying the architecture of the corresponding RNN node. We review a simple variant of such RNN nodes and the corresponding RNNs in Section 1.6.2 in detail and we briefly address one of the most commonly used RNN nodes, the so-called *long short-term memory (LSTM)* node, in Section 1.6.3.

There is a wide range of application areas where sequential data are considered and RNN based deep learning methods are being employed and developed. Examples of such application areas are NLP including language translation (cf., for example, [11, 76, 77, 388] and the references therein), language generation (cf., for instance, [51, 169, 238, 340] and the references therein), and speech recognition (cf., for example, [6, 81, 170, 172, 360] and the references therein), time series prediction analysis including stock market prediction (cf., for instance, [130, 133, 372, 376] and the references therein) and weather prediction (cf., for example, [352, 375, 407] and the references therein) and video analysis (cf., for instance, [108, 235, 307, 401] and the references therein).

### 1.6.1 Description of RNNs

**Definition 1.6.1** (Function unrolling). *Let $X,Y,I$ be sets, let $f: X \times I \to Y \times I$ be a function, and let $T \in \mathbb{N}$, $\mathbb{I} \in I$. Then we denote by $\mathfrak{R}_{f,T,I}: X^T \to Y^T$ the function which satisfies for all $x_1, x_2, \ldots, x_T \in X$, $y_1, y_2, \ldots, y_T \in Y$, $i_0, i_1, \ldots, i_T \in I$ with $i_0 = \mathbb{I}$ and $\forall t \in \{1, 2, \ldots, T\}: (y_t, i_t) = f(x_t, i_{t-1})$ that*

$$\mathfrak{R}_{f,T,I}(x_1, x_2, \ldots, x_T) = (y_1, y_2, \ldots, y_T) \tag{1.62}$$

*and we call $\mathfrak{R}_{f,T,I}$ the $T$-times unrolled function $f$ with initial information $\mathbb{I}.$*

**Definition 1.6.2** (Description of RNNs). *Let $X, Y, I$ be sets, let $\mathfrak{D}, T \in \mathbb{N}$, $\theta \in \mathbb{R}^\mathfrak{D}$, $\mathbb{I} \in I$, and let $\mathfrak{N} = (\mathfrak{N}_\vartheta)_{\vartheta \in \mathbb{R}^\mathfrak{D}}: \mathbb{R}^\mathfrak{D} \times X \times I \to Y \times I$ be a function. Then we call $R$ the realization function of the $T$-step unrolled RNN with RNN node $\mathfrak{N}$, parameter vector $\theta$, and initial*
