ADAGRAD paper$^{37}$ provides a theoretical foundation for this approach and suggests an algorithm for specifying $\partial_{ij}$. Most deep learning systems make use of ADAGRAD-inspired algorithms, such as ADAM$^{38}$, that combine the original algorithm with heuristics that have been shown empirically to improve performance.

Finally, there is another key trick to DNN training: *dropout*. This procedure, proposed by researchers$^{39}$ in Hinton's lab at the University of Toronto, involves introduction of random noise into each gradient calculation. For example, Bernoulli dropout replaces current estimates $\omega_{ij}$ with $\tilde{\omega}_{ij} = \omega_{ij}\zeta_{ij}$ where $\zeta_{ij}$ is a Bernoulli random variable with $\mathrm{p}(\zeta_{ij} = 1) = c$. Each SGD update from Equation 10.8 then uses these parameter values when evaluating the gradient:

```
$\mathbf{\Omega}_{t+1} = \mathbf{\Omega}_{t} - C_{t}\nabla f\left(\mathbf{\Omega}_{t}\{d_{ib}\}\{^{B}_{b=1}\}\right)\tilde{\mathbf{\Omega}}_{i}. \hspace{1em} (10.10)$
```

Here, $\tilde{\mathbf{\Omega}}_{t}$ is the noised-up version of $\mathbf{\Omega}_{t}$, with elements $\tilde{\omega}_{ij}$. 

Dropout is used because it has been observed to yield model fits that have lower out-of-sample error rates (so long as you tune $c$ appropriately). Why does this happen? Informally, dropout acts as a type of implicit regularization. An example of explicit regularization is parameter penalization: to avoid overfit, the minimization objective for DNNs almost always has a $\lambda\|\mathbf{\Omega}\|_{2}^{2}$ ridge penalty term added to the data-likelihood loss function. Dropout plays a similar role. By forcing SGD updates to ignore a random sample of the parameters, it prevents overfit on any individual parameter.$^{40}$ More rigorously, it has recently been established$^{41}$ that SGD with dropout corresponds to a type of “variational Bayesian inference.” That means that dropout SGD is solving to find the posterior *distribution* over $\mathbf{\Omega}$ rather than a point estimate.$^{42}$ As interest grows around uncertainty quantification for DNNs, this interpretation of dropout is one option for bringing Bayesian inference into deep learning.

# REINFORCEMENT LEARNING

As the final section on the elements of deep learning, let's consider how these AI systems generate their own training data through a mix of experimentation and optimization. Reinforcement learning (RL) is the common term for this aspect of AI. RL is sometimes used to denote specific