We can make our predictions from that w and look at the three losses—square-error, absolute, and hinge losses. I won’t use the absolute loss any further—it’s just there for comparison sake.

```
In [17]:
# prediction, error, loss
predictions = rdot(weights, xs.reshape(-1, 1))
errors = ys - predictions

loss_sse   = np.sum(errors ** 2)
loss_sae   = np.sum(np.abs(errors))
loss_hinge = np.sum(np.max(np.abs(errors) - epsilon, 0))
```

We can also compute the two complexity penalties we need for L₁ and L₂ regularization. Note the close similarity to the calculations for the losses, except we calculate the complexity from the weights instead of the errors.

```
In [18]:
# complexity penalty for regularization
complexity_saw = np.sum(np.abs(weights))
complexity_ssw = np.sum(weights**2)
```

Finally, we have our total costs:

```
In [19]:
# cost
cost_gof_regression   = loss_sse   + 0.0
cost_L1pen_regression = loss_sse   + C * complexity_saw
cost_L2pen_regression = loss_sse   + C * complexity_ssw
cost_sv_regression    = loss_hinge + C * complexity_ssw
```

Now, as that code is written, it only calculates a cost for each type of regression for one set of weights. We would have to run that code over and over—with different sets of weights—to find a good, better, or best set of weights.

Table 9.1 shows the mathematical forms that are buried in that code. If we let L₁ = Σ |vᵢ| and L₂ = Σ vᵢ² be the sum of absolute values and the sum of squared values, respectively, then we can summarize these in the smaller, more readable form of Table 9.2. Remember, the loss applies to the raw errors. The penalty applies to the parameters or weights.

I want to congratulate. By reading Table 9.2, you can see the fundamental differences between these four regression methods. In reality, we don’t know the right assumptions to choose between learning methods—for example, the discriminant methods or these varied regression methods—so we don’t know whether the noise and underlying complexity of data is going to be best suited to one or another of these techniques. But we skirt around this problem by cross-validating to pick a preferred method for a given