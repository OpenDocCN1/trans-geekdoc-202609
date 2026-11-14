![](bbox=[0.206, 0.123, 0.792, 0.287])

Figure 4.52: An example of a ground Markov logic network represented as a pairwise MRF for 2 people. Adapted from Figure 2.1 from [DL09]. Used with kind permission of Pedro Domingos.

constraint. For example, we can encode the rule \(\neg Sm(x) \lor Ca(x)\) by creating a potential function \(\Psi(Sm(x), Ca(x))\), where we define

```
\Psi(Sm(x), Ca(x)) = \left\{ \begin{array}{ll} 1 & \text{if } \neg Sm(x) \lor Ca(x) = T \\ 0 & \text{if } \neg Sm(x) \lor Ca(x) = F \end{array} \right. (4.180)
```

The result is the UGM in Figure 4.52.

The above approach will assign non-zero probability to all logically valid worlds. However, logical rules may not always be true. For example, smoking does not always cause cancer. We can relax the hard constraints by using non-zero potential functions. In particular, we can associate a weight with each rule, and thus get potentials such as

```
\Psi(Sm(x), Ca(x)) = \left\{ \begin{array}{ll} e^w & \text{if } \neg Sm(x) \lor Ca(x) = T \\ e^0 & \text{if } \neg Sm(x) \lor Ca(x) = F \end{array} \right. (4.181)
```

where the value of \(w > 0\) controls strongly we want to enforce the corresponding rule.

The overall joint distribution has the form

```
\(p(\boldsymbol{x}) = \frac{1}{Z(\boldsymbol{w})} \exp(\sum_i w_i n_i(\boldsymbol{x}))\) (4.182)
```

where \(n_i(\boldsymbol{x})\) is the number of instances of clause \(i\) which evaluate to true in assignment \(\boldsymbol{x}\).

Given a grounded MLN model, we can then perform inference using standard methods. Of course, the ground models are often extremely large, so more efficient inference methods, which avoid creating the full ground model (known as **lifted inference**), must be used. See [DL09; KNP11] for details.

One way to gain tractability is to relax the discrete problem to a continuous one. This is the basic idea behind **hinge-loss MRFs** [Bac+15b], which support exact inference using scalable convex optimization. There is a template language for this model family known as **probabilistic soft logic**, which has a similar "flavor" to MLN, although it is not quite as expressive.