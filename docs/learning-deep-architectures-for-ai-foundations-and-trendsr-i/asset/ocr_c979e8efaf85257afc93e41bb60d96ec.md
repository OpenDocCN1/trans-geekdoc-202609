# Energy-Based Models and Boltzmann Machines

partition the space according to all possible configurations (where each expert can have its constraint violated or not). [69] proposed an algorithm for estimating the gradient of log P(x) in Equation (5.4) with respect to parameters associated with each expert, using the first instantiation [70] of the Contrastive Divergence algorithm (Section 5.4).

# 5.1.1 Introducing Hidden Variables

In many cases of interest, x has many component variables xᵢ, and we do not observe of these components simultaneously, or we want to introduce some non-observed variables to increase the expressive power of the model. So we consider an observed part (since denoted x here) and a hidden part

```
$P(x
```

and because only x is observed, we care about the marginal

```
$P(x) = \frac{e^{-FreeEnergy(x)}}{Z} (5.6)$
```

In such cases, to map this formulation to one similar to Equation (5.1), we introduce the notation (inspired from physics) of free energy, defined as:

```
$P(x) = \frac{e^{-FreeEnergy(x)}}{Z}, (5.7)$
```

with $Z = \sum_{x} e^{-FreeEnergy(x)}$, i.e.,

```
$FreeEnergy(x) = -log \sum_{h} e^{-FreeEnergy(x,h)} (5.8)$
```

So the free energy is a marginalization of energies in the logdomain. The data-likelihood gradient then has a particularly interesting form. Let us introduce $	heta$ to represent parameters of the model. Starting from Equation (5,7), we obtain

```
$$\frac{\partial \log P(x)}{\partial \theta} = \frac{\partial FreeEnergy(x)}{\partial \theta} + \frac{1}{Z} \sum_{\hat{x}} e^{-FreeEnergy(\hat{x})} \frac{\partial FreeEnergy(\hat{x})}{\partial \theta}\n = \frac{\partial FreeEnergy(x)}{\partial \theta} + \sum_{\hat{x}} P(\hat{x}) \frac{\partial FreeEnergy(\hat{x})}{\partial \theta}. (5.9)$
```