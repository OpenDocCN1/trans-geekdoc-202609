![](bbox=[0.25, 0.12, 0.78, 0.42])

Figure 15.9: Illustration of a GRU. Adapted from Figure 8.8.3 of [Zha+19a].

# 15.2.6.2 Long short term memory (LSTM)

In this section, we discuss the long short term memory (LSTM) model of [HS97], which is a more sophisticated version of the GRU (and pre-dates it by almost 20 years).

The basic idea is to partition the hidden state into a long-term part, called a memory cell c_t, and a short-term part, denoted h_t. We first compute the new cell state using

```
C_t = F_t ⊙ C_{t-1} + I_t ⊙ \tilde{C}_t  (15.14)
\tilde{C}_t = tanh(X_t W_{xc} + H_{t-1} W_{hc} + b_c)  (15.15)
I_t = σ(X_t W_{xi} + H_{t-1} W_{hi} + b_i)  (15.16)
F_t = σ(X_t W_{xf} + H_{t-1} W_{hf} + b_f)  (15.17)
```

where I_t is the input gate, F_t is the forget gate, and \tilde{C}_t is a candidate cell state. This additive update to the cell state allows long-term information to pass through, without the gradient from vanishing.

Next we compute the new short term state as follows:

```
O_t = σ(X_t W_{xo} + H_{t-1} W_{ho} + b_o)  (15.18)
H_t = O_t ⊙ tanh(C_t)  (15.19)
```

2. One important detail pointed out in [JZS15] is that we need to initialize the bias term for the forget gate b_f to be large (e.g., close to 1), so that information can easily pass through the c chain over time. Without this trick, performance is often much worse.