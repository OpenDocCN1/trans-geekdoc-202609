
## 5.1. NEURAL NETWORKS

```
$\frac{\partial}{\partial a_i} = \sum_{k=1}^n -2(y_k - h(x_k))c_k \frac{\partial}{\partial a_i} \max(0, a_i + b_ix) = \sum_{k=1}^n -2(y_k - h(x_k))c_k \begin{cases} 0 & \text{if } a_i + b_ix < 0 \\ 1 & \text{if } a_i + b_ix > 0 \end{cases}$
```

```
$\frac{\partial}{\partial b_i} = \sum_{k=1}^n -2(y_k - h(x_k))c_k \frac{\partial}{\partial b_i} \max(0, a_i + b_ix) = \sum_{k=1}^n -2(y_k - h(x_k))c_k \begin{cases} 0 & \text{if } a_i + b_ix < 0 \\ \text{otherwise} \end{cases}$
```

Crucially, we see that the gradient with respect to **a** and **b** is not uniformly zero, unlike the step function.

If the ReLU is active, both weights are adjustable. Depending on the gradient of the objective function, our ReLUs can move to the left or right, increase or decrease their slope, and flip direction.

![](img/99defe26aebed215976e83d281581f33_74_0.png)

If the initialization runs off the ReLU for every training point, then the gradient descent updates will not change the parameters of the neuron, and we say it is dead. Random initialization should result in a reasonable number of active neurons. There are more sophisticated initialization methods, such as “Glorot initialization”, which take into account the number of connections and are more effective in practice. Leaky ReLUs, which have a small slope in the section where the ReLU is flat ($u(x) = .01x$ when $x < 0$) are sometimes used to provide some small gradient to avoid dead neurons.

## Neural networks are universal function approximators

The celebrated neural network approximation theorem, by Kurt Hornik³, tells us that neural networks are universal function approximators in the following sense.

**Theorem.** Suppose $u : \mathbb{R} \to \mathbb{R}$ is nonconstant, bounded, nondecreasing, and continuous⁴, and let $S \subset \mathbb{R}^n$ be closed and bounded. Then for any continuous function $f : S \to \mathbb{R}$ and any $\epsilon > 0$, there exists a neural network with one hidden layer and finite number of neurons, which we can write

```
$h(x) = \sum_{i=1}^d c_iu(a_i + b_ix)$
```

² Understanding the difficulty of training deep feedforward neural networks.
³ See Approximation Capabilities of Multilayer Feedforward Networks.
⁴ Both ReLU and sigmoid satisfy these requirements.

such that
$|h(x) - f(x)| < \epsilon$

for all $x \in S$.

There's some subtlety in the theorem that's worth noting. It says that for any continuous function, there exists a neural network of finite size that uniformly approximates the given function. However, it says nothing about well any particular architecture you're considering will approximate the function.

It's also worth pointing out that in the theorem, the network consists of just one hidden layer. In practice, people find that using more layers works better.

## 5.2 Training Neural Networks

### ReLUs as Universal Function Approximators

Last time we saw that the second-most simple function approximator was the piecewise linear function. Specifically, we talked about a specific component of piecewise linear functions called the ReLU, which is $f(x) = \max(0, x)$.

In discussion of neural nets, we saw that we would have the ReUs act on linear combinations of neural units to introduce nonlinearity to the function encoded by the neural net. For example, when acting on one input (and a bias term) our ReLUs will take in arguments of the form $a + b$. Let's see an example of how expressive they can be. Suppose we wanted to build this function from ReUs:

![](img/99defe26aebed215976e83d281581f33_75_0.png)

All we would need to do is center a ReLU at each hinge of the function and give it the appropriate parameters. For example, to match $f$ from 0 to 3, we would only need the ReLU defined by $\max(0, x-2)$. The full function can be matched with this linear combination of ReUs (and a constant bias term):

$f(x) = -1 + \max(0, x-2) - \max(0, x-2) + \max(0, 6-x) - \max(0, 5-x) + \max(0, 2x-12)$

Here's the plot on Wolfram Alpha.

![](img/99defe26aebed215976e83d281581f33_76_0.png)

## 5.2. TRAINING NEURAL NETWORKS

![](img/99defe26aebed215976e83d281581f33_76_0.png)

In higher dimensions, i.e. a ReLU takes as input: $f(x) = \max(0, x)$, the gradient can be viewed as:

### Derivatives in Neural Nets

We have a very powerful tool at our disposal, but it does us no good if we can't train them. Let's look at:

![](img/99defe26aebed215976e83d281581f33_76_0.png)

The output of the neural net is represented by:

### The Chain Rule

Since neural net outputs are functions of their inputs, we must calculate the derivative of the loss with respect to the parameters. This is because of the chain rule.
