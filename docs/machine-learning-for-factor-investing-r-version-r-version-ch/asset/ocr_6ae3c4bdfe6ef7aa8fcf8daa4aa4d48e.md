![](bbox=[0.12, 0.06, 0.88, 0.28])

# FIGURE 7.6: Diagram of back-propagation.

This operation can be performed any number of times with different sample sizes. We discuss this issue in Section 7.3.

The learning rate \(\eta\) can be refined. One option to reduce overfitting is to impose that after each epoch, the intensity of the update decreases. One possible parametric form is \(\eta = \alpha e^{-\beta t}\), where \(t\) is the epoch and \(\alpha, \beta > 0\). One further sophistication is to resort to so-called *momentum* (which originates from Polyak (1964)):

```
\(\mathbf{W}_{t+1} \leftarrow \mathbf{W}_t - \mathbf{m}_t\) with

\(\mathbf{m}_t \leftarrow \eta \frac{\partial D(\tilde{y}_i)}{\partial \mathbf{W}_t} + \gamma \mathbf{m}_{t-1},\) (7.9)
```

where \(t\) is the index of the weight update. The idea of momentum is to speed up the convergence by including a memory term of the last adjustment (\(\mathbf{m}_{t-1}\)) and going in the same direction in the current update. The parameter \(\gamma\) is often taken to be 0.9.

More complex and enhanced methods have progressively been developed:

+   - Nesterov (1983) improves the momentum term by forecasting the future shift in parameters;
+   - Adagrad (Duchi et al. (2011)) uses a different learning rate for each parameter;
+   - Adadelta (Zeiler (2012)) and Adam (Kingma and Ba (2014)) combine the ideas of Adagrad and momentum.

Lastly, in some degenerate case, some gradients may explode and push weights far from their optimal values. In order to avoid this phenomenon, learning libraries implement gradient clipping. The user specifies a maximum magnitude for gradients, usually expressed as a norm. Whenever the gradient surpasses this magnitude, it is rescaled to reach the authorized threshold. Thus, the direction remains the same, but the adjustment is smaller.

# 7.2.4 Further details on classification

In decision trees, the ultimate goal is to create homogeneous clusters, and the process to reach this goal was outlined in the previous chapter. For neural networks, things work differently because the objective is explicitly to minimize the error between the prediction \(\tilde{\mathbf{y}}_i\) and a target label \(\mathbf{y}_i\). Again, here \(\mathbf{y}_i\) is a vector full of zeros with only one *one* denoting the class of the instance.