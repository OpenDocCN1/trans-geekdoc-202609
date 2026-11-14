programming language. How do we adapt AD to handle a language with loops, conditionals, and recursive calls? What about parallel programming constructs? We have partial answers to questions like these today, although they invite a deeper dive into language details such as type systems and implementation concerns [Yu+18; Inm20; Pas+21b].

One example language construct that we already know how to handle, due to Section 6.2.2.2, is a standard let expression. In languages with a means of name or variable binding, multiple appearances of the same variable are analogous to fan-out in a circuit. Figure 6.1a corresponds to a function f that we could write in a functional language as:

```
```
f(x) =
 let ax = a(x)
 in c(ax, b(ax))
```
```

in which ax indeed appears twice after it is bound.

Understanding the interaction between language capacity and automatic differentiability is an ongoing topic of computer science research [PS08a; AP19; Vyt+19; BMP19; MP21]. In the meantime, functional languages have proven quite effective in recent AD systems, both widely-used and experimental. Systems such as JAX, Dex, and others are designed around pure functional programming models, and internally rely on functional program representations for differentiation [Mac+15; BPS16; Sha+19; FJL18; Bra+18; Mac+19; Dex; Fro+21; Pas+21a].

# ## 6.3 Stochastic optimization

In this section, we consider optimization of stochastic objectives of the form

```
$$ \mathcal{L}(\theta) = \mathbb{E}_{q_\theta(z)} \left[ \tilde{\mathcal{L}}(\theta, z) \right] $$ (6.41)
```

where \(\theta\) are the parameters we are optimizing, and \(z\) is a random variable, such as an external noise.

# ## 6.3.1 Stochastic gradient descent

Suppose we have a way of computing an unbiased estimate \(g_t\) of the gradient of the objective function, i.e.,

```
$$ \mathbb{E} \left[ g_t \right] = \nabla_\theta \mathcal{L}(\theta) |_{\theta_t} $$ (6.42)
```

Then we can use this inside of a gradient descent procedure:

```
$$ \theta_{t+1} = \theta_t - \eta_t g_t $$ (6.43)
```

where \(\eta_t\) is the learning rate or step size. This is called stochastic gradient descent or SGD.

# ## 6.3.1.1 Choosing the step size

When using SGD, we need to be careful in how we choose the learning rate in order to achieve convergence. Rather than choosing a single constant learning rate, we can use a learning rate