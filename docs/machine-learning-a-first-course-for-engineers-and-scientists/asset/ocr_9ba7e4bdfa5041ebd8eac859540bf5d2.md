# 6.4 Dropout

![](bbox=[0.368, 0.073, 0.631, 0.255])

**Figure 6.19:** The network used for prediction after trained with dropout. All units and links are present (no dropout) but the weights going out from a certain unit are multiplied by the probability that unit being included during training. This compensates for the fact that they were dropped during training. Here all units have been kept with probability $r$ during training (and consequently dropped with probability $1-r$).

# Training with dropout

To train we use stochastic gradient descent described in Algorithm 5.3. Each gradient mini-batch of data is used to compute an approximation of the gradient, as normally in stochastic gradient descent. However, instead of computing the gradient for the full network, we generate a random sub-network by randomly dropping units as described above. We compute the gradient for that sub-network and then do a gradient step. This step only updates the parameters in the sub-network. The parameters that are associated with the dropped units do not affect the output of that sub-network and are left untouched. In the next step we use another mini-batch of data, remove another randomly selected collection of units and update the parameters in that sub-network. We proceed in this method until some terminal condition is fulfilled.

# Prediction at test time

After we have trained the sub-networks, we want to make a prediction on an unseen input data $\mathbf{x}$. If this was an ensemble method we would evaluate all sub-networks and their averages. Since each unit can be in or out, there are $2^U$ sub-networks where $U$ is the total number of units in the network. Hence, due to this large number, evaluating all of them would be infeasible. However, there is a simple trick to achieve the same result. Instead of evaluating all sub-networks we simply evaluate the full network all the parameters. Compensate for the fact that the model was trained with dropout, we multiply each estimated parameter going out from a unit with the probability that unit being kept during training. This ensures that the expected value of the input to the next unit is the same during training and testing. If we are keeping a unit with probability $r$, then we multiply the following weight $\mathbf{W}^{(l)}$ with $r$, with that

```
$$\begin{aligned} \mathbf{W}^{(l)} &= r\mathbf{W}^{(l)} \ \mathbf{q}^{(l)} &= h(\mathbf{q}^{(l-1)} + b^{(l)}). \end{aligned}$
```

This is also illustrated in Figure 6.19 where we keep a unit with probability $r$ in all layers during training. This adjustment of the weights can be done just once after we are done training and then use these adjusted weights as usual during all predictions.

This procedure of averaging the average over all ensemble members has been shown to work well in practice even though there is not yet some theoretical argument for the accuracy of this approximation.