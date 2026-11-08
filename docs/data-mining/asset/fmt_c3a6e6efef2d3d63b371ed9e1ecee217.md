
# LSTM Recurrent Neural Network Architecture

The so-called `LSTM` recurrent neural network architecture was specifically created to address the vanishing gradient problem. It uses a special combination of hidden units, elementwise products and sums between units to implement gates that control “memory cells.” These cells are designed to retain information without modification for long periods of time. They have their own input and output gates, which are controlled by learnable weights that are a function of the current observation and the hidden units at the previous time step. As a result, backpropagated error terms from gradient computations can be stored and propagated backward without degradation. The original `LSTM` formulation consisted of *input gates* and *output gates* but *forget gates* and “peephole weights” were added later. The architecture is complex but has produced state-of-the-art results on a wide variety of problems. Next we present the most popular variant of `LSTM` `RNNs`, which does not include peephole weights but does use forget gates.

## How `LSTM` `RNNs` Work

`LSTM` `RNNs` work as follows. At each time step there are three types of gate: input `i[t]`, forget `f[t]`, and output `o[t]`, each being a function of the underlying input `x[t]` at time `t` and the hidden units at time `t` - 1, `h[t-1]`. Gates multiply `x[t]` by their own gate-specific `W` matrix `h[t-1]`, by their own `U` matrix, and add their own bias vector `b`, followed by the application of a sigmoidal elementwise nonlinearity.
