

```r
# Define a most basic RNN
network = tf$contrib$rnn$GRUCell(n.hidden)
# Then, assign stacked RNN cells
network =
tf$contrib$rnn$MultiRNNCell(lapply (1:num_layers,function(k,network)
{network},network))
# create a Recurrent Neural Network
cell_output = tf$contrib$rnn$static_rnn (network, x,
dtype=tf$float32)
# Linear activation, using rnn inner loop
last_vec=tail(cell_output [[1]], n=1)[[1]]
return(tf$matmul(last_vec, weights) + bias)
}
```

## Setting up a Long short-term memory based sequence model

In sequence learning the objective is to capture short-term and long-term memory. The short-term memory is captured very well by standard RNN, however, they are not very effective in capturing long-term dependencies as the gradient vanishes (or explodes rarely) within an RNN chain over time.

> The gradient vanishes when the weights have small values that on multiplication vanish over time, whereas in contrast, scenarios where weights have large values keep increasing over time and lead to divergence in the learning process. To deal with the issue Long Short Term Memory (LSTM) is proposed.

## How to do it...

The RNN models in TensorFlow can easily be extended to LSTM models by using BasicLSTMCell. The previous rnn function can be replaced with the lstm function to achieve an LSTM architecture:

```r
# LSTM implementation
lstm<-function(x, weight, bias){
# Unstack input into step_size
x = tf$unstack(x, step_size, 1)
# Define a lstm cell
lstm_cell = tf$contrib$rnn$BasicLSTMCell(n.hidden, forget_bias=1.0,
state_is_tuple=TRUE)
# Get lstm cell output
cell_output = tf$contrib$rnn$static_rnn(lstm_cell, x, dtype=tf$float32)
# Linear activation, using rnn inner loop last output
last_vec=tail(cell_output[[1]], n=1)[[1]]
return(tf$matmul(last_vec, weights) + bias)
}
```

For brevity the other parts of the code are not replicated.

## How it works...

The LSTM has a similar structure to RNN, however, the basic cell is very different as traditional RNN uses single multi-layer perceptron (MLP), whereas a single cell of LSTM includes four input layers interacting with each other. These three layers are:

- forget gate
- input gate
- output gate

The forget gate in LSTM decides which information to throw away and it depends on the last hidden state output \(h_{t-1}\), \(X_t\) which represents input at time \(t\).

![](img/88a9c35e3059565190fbb6413f1ca217_215_0.png)

Illustration of forget gate

In the earlier figure, \(C_t\) represents cell state at time \(t\). The input data is represented by \(X_t\) and the hidden state is represented as \(h_{t-1}\). The earlier layer can be formulated as:

\[
f_t = \sigma(S_f X_t + W_f h_{t-1} + b_f)
\]

The input gate decides update values and decides the candidate values of the memory cell and updates the cell state, as shown in the following figure:

![](img/88a9c35e3059565190fbb6413f1ca217_216_0.png)

Illustration of input gate

- The input $i_t$ at time $t$ is updated as:

\[
i_t = \sigma(S_i x_t + W_i h_{t-1} + b_i) \qquad \hat{C}_t = \tanh(S_c x_t + W_c h_{t-1} + b_c)
\]

- The expected value of current state $\hat{C}_t$ and the output from input gate $i_t$ is used to update the current state $C_t$ at time $t$ as:

\[
C_t = i_t * \hat{C}_t + f_t * C_{t-1}
\]

The output gates, as shown in the following figure, compute the output from the LSTM cell based on input $X_t$, previous layer output $h_{t-1}$ and current state $C_t$:

![](img/88a9c35e3059565190fbb6413f1ca217_217_0.png)

Illustration of output gate

The output based on output gate can be computed as follows:

\[
O_t = \sigma(S_o x_t + W_o h_{t-1} + b_o) \qquad h_t = O_t * \tanh(C_t)
\]

## Reinforcement Learning

The current chapter will introduce Reinforcement Learning. We will cover the following topics:

- Setting up a Markov Decision Process
- Performing model-based learning
- Performing model-free learning

### Introduction

**Reinforcement Learning** (RL) is an area in machine learning that is inspired by psychology, such as how agents (software programs) can take actions in order to maximize cumulative rewards.

The RL is reward-based learning where the reward comes at the end or is distributed during the learning. For example, in chess, the reward will be assigned to winning or losing the game whereas in games such as tennis, every point won is a reward. Some of the commercial examples of RL are DeepMind from Google uses RL to master parkour. Similarly, Tesla is developing AI-driven technology using RL. An example of reinforcement architecture is shown in the following figure:

![](img/88a9c35e3059565190fbb6413f1ca217_219_0.png)

Interaction of an agent with environment in Reinforcement Learning

The basic notations for RL are as follows:

- T(s, a, s'): Represents the transition model for reaching state s' when action a is taken at state s
- P: Represents a policy which defines what action to take at every possible state s ∈ S
- R(s): Denotes the reward received by agent at state s

The current chapter will look at how to set up reinforcement models using R. The next sub-section will introduce MDPtoolbox from R.

## Setting up a Markov Decision Process

The **Markov Decision Process** (MDP) forms the basis of setting up RL, where the outcome of a decision is semi-controlled; that is, it is partly random and partly controlled (by the decision-maker). An MDP is defined using a set of possible states (S), a set of possible actions (A), a real-values reward function (R), and a set of transition probabilities from one state to another state for a given action (T). In addition, the effects of an action performed on one state depends only on that state and not on its previous states.

### Getting ready

In this section, let us define an agent travelling across a 4 x 4 grid, as shown in following figure:

![](img/88a9c35e3059565190fbb6413f1ca217_220_0.png)

*A sample 4 x 4 grid of 16 states*

This grid has 16 states (S1, S2, ..., S16). In each state, the agent can perform four actions (up, right, down, left). However, the agent will be restricted to some actions based on the following constraints:

- The states across the edges shall be restricted to actions which point only toward states in the grid. For example, an agent in S1 is restricted to the right or down action.
- Some state transitions have barriers, marked in red. For example, the agent cannot go *down* from S2 to S3.

Each state is also assigned to a reward. The objective of the agent is to reach the destination with minimum moves, thereby achieving the maximum reward. Except state *S15* with a reward value of 100, all the remaining states have a reward value of -1.

Here, we will use the *MDptoolbox* package in R.

## How to do it...

This section will show you how to set up RL models using *MDptoolbox* in R:

- 1. Install and load the required package:

```r
Install.packages("MDptoolbox")
library(MDptoolbox)
```

- 2. Define the transition probabilities for action. Here, each row denotes *from state* and each column denotes *to state*. As we have 16 states, the transition probability matrix of each action shall be a 16 x 16 matrix, with each row adding up to 1:

```r
up<- matrix(c(1
0 , . , . , 0 , . , . , 0 , . , . , 0 , . , . , 0
, 0 , . , . , 0 , . , . , 0 , . , . , 0 , . , . , 0
, . , 0.1 , . , 0.7 , . , 0.2 , . , 0 , . , 0 , . , 0
, . , 0 , . , 0 , . , 0 , . , 0 , . , 0 , . , 0
, 0 , . , 0.15 , . , 0 , . , 0.8 , . , 0.05 , . , 0
, 0 , . , 0 , . , 0 , . , 0 , . , 0 , . , 0 , . , 0
, 0 , . , 0 , . , 0 , . , 0.7 , . , 0.3 , . , 0
, 0 , . , 0 , . , 0 , . , 0 , . , 0 , . , 0 , . , 0
, . , 0.1 , . , 0 , . , 0 , . , 0 , . , 0 , . , 0.7
, 0.1 , . , 0 , . , 0 , . , 0.1 , . , 0 , . , 0
, 0 , . , 0 , . , 0.05 , . , 0 , . , 0 , . , 0.7
, 0.15 , . , 0.1 , . , 0 , . , 0 , . , 0 , . , 0
0 , . , 0 , . , 0 , . , 0 , . , 0 , . , 0 , . , 0
, . , 0.7 , . , 0.15 , . , 0.05 , . , 0 , . , 0 , . , 0
0.05 , . , 0 , . , 0 , . , 0 , . , 0 , . , 0 , . , 0
, 0 , . , 0 , . , 0 , . , 0 , . , 0 , . , 0
```
