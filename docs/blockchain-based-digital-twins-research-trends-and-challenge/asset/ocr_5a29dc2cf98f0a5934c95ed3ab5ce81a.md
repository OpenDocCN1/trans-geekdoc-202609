the machineat time 't' and $s_{t-1}$ be the state of the machineat time 't-1.' While analyzing the $s_t$ for predicting the maintenance requirement or probability of failure, the knowledge of the machine state at a time 't-1', i.e., $S_{t-1}$ is also to be considered. The Preciseness of the prediction task can be improved by also considering previous 'n' state information like $S_{t-1,t-2}, S_{t-3\dots t-n}$. Hence, the Long Short-Term Memory (LSTM) neural network is considered to be a suitable learning model for the proposed predictive maintenance.

The LSTM can do analysis and classification of current input using the knowledge acquired from the past data. The LSTM can decide which information is worth mentioning or not. The architecture of LSTM has four gates to support learning based on long-term dependencies. The gates decide what to learn, forget, remember, and use. The Learning gate takes the current state $C_t$ and previous short-term memory $SM_{t-1}$ as input. It decides which information is relevant and keeps only as learning for prediction. The operation of the learning gate $(lg)$ using the weight matrix $(M_n)$ is given below:

```
$Learning Matrix (L_t) = \tanh(M_n [SM_{t-1}, S_t]) + bias \_n$
```

```
$Ignoring factor (ig_t) = (M_n [SM_{t-1}, S_t]) + bias \_n$
```

```
$lg_{output} = L_t ig_t$
```

The Forgetting gate takes the long-term memory $(SM_t)$ as input and decides what to be forgotten and what to be remembered as follows:

```
$Ignoring factor (ig_t) = (M_n [SM_{t-1}, S_t]) + bias \_n$
```