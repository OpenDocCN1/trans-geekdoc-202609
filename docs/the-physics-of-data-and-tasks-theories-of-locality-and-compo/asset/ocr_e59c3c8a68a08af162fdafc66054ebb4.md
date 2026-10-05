# 8.1 NOTATION AND PROBLEM STATEMENT

We demonstrate that the NTK is insufficient to explain weight arithmetic in nonlinear models and introduce weight disentanglement as the necessary underlying condition.

We put forward linearization as a method to augment weight disentanglement and improve weight arithmetic.

Using kernel theory, we connect weight disentanglement in linearized models to the spatial localization of the kernel's eigenfunctions and validate this theory numerically in pre-trained transformers.

Finally, we show that weight disentanglement is an emergent property that arises from the pre-training process.

# 8.1 NOTATION AND PROBLEM STATEMENT

$f:\mathcal{X} \times \mathcal{X} \to \mathcal{Y}$ is a neural network taking inputs $x \in \mathcal{X}$ and parameterized by a set of weights $\theta \in \mathcal{\Theta}$. We assume $\mathcal{X} \subseteq \mathbb{R}^d$, $\mathcal{\Theta} \subseteq \mathbb{R}^m$ and $\mathcal{Y} \subseteq \mathbb{R}^r$. Consider $T$, with each task $t$ starting from a triplet $(D_t, \mu_t, f_t)$ where $D_t \subseteq \mathcal{X}$ is a data support $\text{supp}(\mu_t)=D_t$, and $f_t:D_t \to \mathcal{Y}$ is a target function (e.g., labels). In practice, each task is identified with a training set $\{x_i, f_t(x_i)\}_{i\in[D_t]}$ with $x \sim \mu_t$, which are used to fine-tune the models starting from the pre-trained weights $\theta_0$ and obtain the fine-tuned weights $\theta_t$.

TASK ARITHMETIC Let the vector of task $t$ be the difference between the fine-tuned and the pre-trained weights, i.e., $\tau_t = \theta_t-\theta_0$. The following property formalizes the notation of weight arithmetic introduced in Luharco et al. [Lih+23], where the authors observed that the accuracies of pre-trained models on different datasets can be modified through the addition or removal of task vectors.

**Property 1** (Task arithmetic). Consider a set of task vectors $T=\{\tau_t\}_{t\in[T]}$ with associated non-intersecting task supports $D=\{D_t\subseteq\mathcal{X}\}_{t\in[T]}$, i.e., for all $t, t'$, if $t\neq t'$ then $D_t\cap D_{t'}=\emptyset$. A network $f$ satisfies the weight arithmetic around $\theta_0$ with respect to $T$ and $D$ if

```
$f(x;\theta_0+\sum_{t=1}^T\tau_t) = \begin{cases} f(x;\theta_0+\tau_t) & x\in D_t \ f(x;\theta_0) & x\notin\bigcup_{t=1}^T D_t \end{cases} \quad (91)$
```

In short, most tasks Property 1 if adding $\tau_t$ does not modify the output of the model outside $D_t$.

NEURAL TANGENT KERNEL Around the initialization weights $\theta_0$, a neural network can be approximated with a first-order Taylor expansion:

```
$f(x;\theta)\approx f(x;\theta_0)+(\theta-\theta_0)^\top\nabla_\theta f(x;\theta_0). \quad (92)$
```