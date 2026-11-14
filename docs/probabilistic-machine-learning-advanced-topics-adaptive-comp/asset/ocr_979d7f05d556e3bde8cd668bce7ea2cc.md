# 34 Decision making under uncertainty

# 34.1 Statistical decision theory

Bayesian inference provides the optimal way to update our beliefs about hidden quantities $H$ given observed data $\mathbf{X} = \mathbf{x}$ by computing the posterior $p(H|\mathbf{x})$. However, at the end of the day, we need to turn our beliefs into actions that we can perform in the world. How can we decide which action is best? This is where decision theory comes in. In this section, we give a brief introduction. For more details, see e.g., [DeG70; Ber85b; KWW22].

# 34.1.1 Basics

In statistical decision theory, we have an agent or decision maker, who wants to choose an action from has a set of possible actions, \(a \in \mathcal{A}\), given some observations or data \(\mathbf{x}\). We assume the data comes from some environment that is external to the agent; we characterize the state of this environment by a hidden or unknown variable \(h \in \mathcal{H}\), known as the state of nature. Finally, we assume we know a loss function \(\ell(h, a)\), that specifies the loss we incur if we take action \(a\) when the state of nature is \(h\). The goal is to define a policy, also called an estimator or decision procedure, which specifies which action to take in response to each possible observation, \(a = \delta(\mathbf{x})\), so as to minimize the expected loss, also called the risk:

```
\delta^*(\cdot) = \underset{\delta}{\text{argmin}} \ R(\delta) \tag{34.1}
```

where the risk is given by

```
R(\delta) = \mathbb{E}[\ell(h, \delta(\mathbf{X}))] \tag{34.2}
```

The key question is how to define the above expectation. We can use a frequentist or Bayesian approach, as we discuss below.

# 34.1.2 Frequentist decision theory

In frequentist decision theory, we treat the state of nature \(h\) as a fixed but unknown quantity, and treat the data \(\mathbf{X}\) as random. Hence we take expectations wrt the data, which gives us the frequentist risk:

```
r(\delta|h) = \mathbb{E}_{p(\mathbf{x}|h)}[\ell(h, \delta(\mathbf{x}))] = \int p(\mathbf{x}|h)\ell(h, \delta(\mathbf{x}))d\mathbf{x} \tag{34.3}
```