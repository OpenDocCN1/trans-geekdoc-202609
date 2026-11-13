version of the vanilla recurrent network defined above. It has the following representation:

```
\tilde{y}_i = z_i \tilde{y}_{i-1} + (1 - z_i) \tanh \mathbf{w}'_y \mathbf{x}_i + b_y + u_y r_i \tilde{y}_{i-1} \quad \text{output (prediction)}
z_i = \text{sig}(\mathbf{w}'_z \mathbf{x}_i + b_z + u_z \tilde{y}_{i-1}) \quad \text{'update gate'} \in (0,1)
r_i = \text{sig}(\mathbf{w}'_r \mathbf{x}_i + b_r + u_r \tilde{y}_{i-1}) \quad \text{'reset gate'} \in (0,1).
```

In compact form, this gives

```
\tilde{y}_i = \underbrace{z_i}_{\text{weight past value}} \underbrace{\tilde{y}_{i-1}}_. + \underbrace{(1-z_i)}_{\text{weight}} \underbrace{\tanh \mathbf{w}'_y \mathbf{x}_i + b_y}_{\text{candidate value (classical RNN)}} + \underbrace{u_y r_i \tilde{y}_{i-1}}_- ,
```

where the \(z_i\) decides the optimal mix between the current and past values. For the candidate value, \(r_i\) decides which amount of past/memory to retain. \(r_i\) is commonly referred to as the ‘reset gate’ and \(z_i\) to the ‘update gate’.

There are some subtleties in the training of a recurrent network. Indeed, because of the chaining between the instances, each batch must correspond to a coherent time series. A logical choice is thus one batch per asset with instances (logically) chronologically ordered. Lastly, one option in some frameworks is to keep some memory between the batches by passing the final value of \(\tilde{y}_i\) to the next batch (for which it will be \(\tilde{y}_0\)). This is often referred to as the stateful mode and should be considered meticulously. It does not seem desirable in a portfolio prediction setting if the batch size corresponds to all observations for each asset: there is no particular link between assets. If the dataset is divided into several parts for each given asset, then the training must be handled very cautiously.

Recurrent networks and LSTM especially have been found to be good forecasting tools in financial contexts (see, e.g., Fischer and Krauss (2018) and Wang et al. (2020)).

# 7.5.2 Code and results

Recurrent networks are theoretically more complicated compared to multilayered perceptrons. In practice, they are also more challenging in their implementation. Indeed, the serial linkages require more attention compared to feed-forward architectures. In an asset pricing framework, we must separate the assets because the stock-specific time series cannot be bundled together. The learning will be sequential, one stock at a time.

The dimensions of variables are crucial. In Keras, they are defined for RNNs as:

+   1. The size of the batch: in our case, it will be the number of assets. Indeed, the recurrence relationship holds at the asset level, hence each asset will represent a new batch on which the model will learn.

+   2. The time steps: in our case, it will simply be the number of dates.

+   3. The number of features: in our case, there is only one possible figure which is the number of predictors.

For simplicity and in order to reduce computation times, we will use the same subset of stocks as that from Section 5.2.2. This yields a perfectly rectangular dataset in which all dates have the same number of observations.