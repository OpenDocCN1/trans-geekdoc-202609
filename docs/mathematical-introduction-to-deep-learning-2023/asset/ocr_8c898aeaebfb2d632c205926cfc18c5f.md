**Lemma 1.2.3 (Fully-connected feedforward ANN with one hidden layer).** *Let* $\mathcal{I}, \mathcal{H} \in \mathbb{N}$, $\theta = (\theta_1, \theta_2, \dots, \theta_{\mathcal{H}\mathcal{I}+2\mathcal{H}+1}) \in \mathbb{R}^{\mathcal{H}\mathcal{I}+2\mathcal{H}+1}$, $x = (x_1, x_2, \dots, x_\mathcal{I}) \in \mathbb{R}^{\mathcal{I}}$ *and let* $\psi : \mathbb{R} \to \mathbb{R}$ *be a function. Then*

```
\mathcal{N}^{\theta, \mathcal{I}}_{\mathfrak{M}_{\psi, \mathcal{H}, \mathrm{id}_{\mathcal{I}}}}(x) = \left[ \sum_{k=1}^{\mathcal{H}} \theta_{\mathcal{H}\mathcal{I}+k+k} \psi \left( \sum_{i=1}^{\mathcal{I}} x_i \theta_{(k-1)\mathcal{I}+i} + \theta_{\mathcal{H}\mathcal{I}+k} \right) \right] + \theta_{\mathcal{H}\mathcal{I}+2\mathcal{H}+1}. (1.24)
```

*(*cf. *Definitions 1.1.1, 1.1.3, and 1.2.1*).*

*Proof of Lemma 1.2.3.* *Observe that* (1.5) *and* (1.18) *show that*

```
\begin{align} &\mathcal{N}^{\theta, \mathcal{I}}_{\mathfrak{M}_{\psi, \mathcal{H}, \mathrm{id}_{\mathcal{I}}}}(x) \\ &= \left( \mathrm{id}_{\mathbb{R}} \circ \mathcal{A}^{0, \mathcal{H}\mathcal{I}+\mathcal{H}}_{1, \mathcal{H}} \circ \mathfrak{M}_{\psi, \mathcal{H}} \circ \mathcal{A}^{\theta, 0}_{\mathcal{H}, \mathcal{I}} \right)(x) \\ &= \mathcal{A}^{0, \mathcal{H}\mathcal{I}+\mathcal{H}}_{1, \mathcal{H}} \left( \mathfrak{M}_{\psi, \mathcal{H}} \left( \mathcal{A}^{\theta, 0}_{\mathcal{H}, \mathcal{I}}(x) \right) \right) \\ &= \left[ \sum_{k=1}^{\mathcal{H}} \theta_{\mathcal{H}\mathcal{I}+k+k} \psi \left( \sum_{i=1}^{\mathcal{I}} x_i \theta_{(k-1)\mathcal{I}+i} + \theta_{\mathcal{H}\mathcal{I}+k} \right) \right] + \theta_{\mathcal{H}\mathcal{I}+2\mathcal{H}+1}. \end{align} (1.25)
```

*The proof of Lemma 1.2.3 is thus complete.* \quad $\Box$

# **1.2.3 Rectified linear unit (ReLU) activation**

In this subsection we formulate the ReLU function which is one of the most frequently used activation functions in deep learning applications (cf., for example, LeCun et al. [263]).

**Definition 1.2.4 (ReLU activation function).** *We denote by* $\mathfrak{r} : \mathbb{R} \to \mathbb{R}$ *the function which satisfies for all* $x \in \mathbb{R}$ *that*

```
\mathfrak{r}(x) = \max \{x, 0\} (1.26)
```

*and we call* $\mathfrak{r}$ *the ReLU activation function (*we call* $\mathfrak{r}$ *the rectifier function)*.*

```
```python
import matplotlib.pyplot as plt

def setup_axis(xlim, ylim):
    _, ax = plt.subplots()
    
    ax.set_aspect("equal")
    ax.set_xlim(xlim)
    ax.set_ylim(ylim)
    ax.spines["left"].set_position("zero")
    ax.spines["bottom"].set_position("zero")
    ax.spines["right"].set_color("none")
    ax.spines["top"].set_color("none")
    for s in ax.spines.values():
```
```