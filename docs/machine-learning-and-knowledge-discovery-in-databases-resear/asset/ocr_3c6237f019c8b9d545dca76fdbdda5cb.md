the memory bank:

```
$$\mathcal{L}_{reg} = \sum_{t,n}^{T,N} \max \{ \| \mathbf{H}_t^t[n] - \mathbf{\Phi}[a] \|^2 - \| \mathbf{H}_t^t[n] - \mathbf{\Phi}[b] \|^2 + \kappa, 0 \} + \sum_{t,n}^{T,N} \| \mathbf{H}_I^t[n] - \mathbf{\Phi}[a] \|^2,$$
```

where \(\kappa\) is a distance margin, \(a,b\) are the indices of the most and second similar virtual nodes w.r.t. node \(n\) based on the affinity score \(\mathbf{S}_I^t\) computed in Eq.(6). As such, \(\mathcal{L}_{reg}\) encourages diversity within the information encoded by different virtual node prototype vectors in the memory bank. Finally, the optimization objective aims to minimize the following overall loss:

```
$$\mathcal{L} = \mathcal{L}_{task} + \mathcal{L}_{inv} + \lambda_2 \mathcal{L}_{reg},$$
```

with a balancing hyperparameter \(\lambda_2\). As MIP is being trained towards convergence, the intervention on variant patterns, i.e., \(\hat{\mathbf{H}}_V = \text{Intervene}(\mathbf{H}_V, r)\) is re-executed in every training epoch, so as to inject more variations in the supervision signals. It is worth noting that, once MIP is trained, only the spatial-temporal backbone model described in Sect. 4.3 is activated for making predictions in the inference stage.

# ## 5 Experiments

# ### 5.1 Experimental Settings

We evaluate our model on two well-established benchmarks, namely METR-LA [17] and NYC Bike [37]. METR-LA [17] is a traffic speed prediction dataset collected with 207 sensors across Los Angeles, from 1st March 2012 to 30th June 2012, the data points are sampled with 5 5-minute time interval. NYC Bike 1 [37] is a dataset of bike rental records from 1st April 2014 to 30th September in New York City, where the city is divided into \(8 \times 16\) equally-sized grids, and the data points are sampled with a 1-hour time interval. As NYC Bike 1 records both in and out flows of bikes, we treat them as two prediction tasks and respectively denote them as NYC Bike 1 (In) and NYC Bike 1 (Out).

We split both datasets chronologically: the first 60% is for training, the following 10% for validation, and three test sets are constructed by evenly slicing the remaining data (10% for each). This is to fully mimic real-world application scenarios where a trained model is expected to provide predictions for multiple consecutive time periods with varying distributions. For convenience, we number the tree test sets with 0, 1, and 2. Generally, as test sets 0-2 become farther apart from the training set in time, their distribution shifts tend to become stronger. Based on the number of time steps available, we predict the next 12 time steps based on the past 12 on METR-LA and predict the next 6 time steps based on the past 6 on NYC Bike. We compare MIP with the following state-of-the-art baselines: STGCN [36], DCRNN [17], STNorm [8], GMSDR [19], MegaCRN [14], CauSTG [40], TESTAM [16]. Similar to previous studies [19, 28, 33], we evaluate all methods in terms of Mean Absolute Error (MAE), Root Mean Square Error