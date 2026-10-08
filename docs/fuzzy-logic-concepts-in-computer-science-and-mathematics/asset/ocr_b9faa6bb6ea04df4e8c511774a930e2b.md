been entirely removed. To illustrate this, consider one rule, Rule$_{i}$, where we have $\mu\mathrm{i}$ representing the temperature and $\mu\mathrm{j}$ representing the engine. In this context, the equation for the rate of change of variable $x$ can be expressed as

```
$$x = A_{i}\tilde{x} + B_{i}\tilde{u}.$$ (2.6)
```

![](bbox=[0.12, 0.24, 0.88, 0.44])

**FIGURE 2.6** Fuzzy controllers in comparison to the linear planned controller.

The requirement for stability in this context is satisfied when there is a shared positive definite matrix $P$ that fulfills the following inequalities:

```
$$P > 0$$ (2.7)
$$A_{i}^{T} P + P A_{i} < 0$$ (2.8)
$$\forall i i \in \{1, ..., N_{\text{rules}}\}$$ (2.9)
```

The determination of the $P$ matrix can be achieved through the resolution of the feasibility linear matrix inequality (LMI) problem. A viable solution has been identified for this problem, ensuring stability. Figure 2.6 provides the model for fuzzy controller linear planned controller [23–27].

This study examines the enhancements achieved through the implementation of a fuzzy controller [28–30] in comparison to a linear planned controller. It is crucial to note that there exists not only an enhancement in performance, but also a facilitation in the implementation of design modifications, owing to the further information offered by the rule base explanation.

# ## 2.6 CONCLUSION

This section elucidates the process of designing a control system for a continuous variable transmission. The control system employs a fuzzy inference method to