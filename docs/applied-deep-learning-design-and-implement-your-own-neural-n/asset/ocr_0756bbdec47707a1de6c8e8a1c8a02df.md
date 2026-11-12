Example 3.1: Logic of AND gate can be implemented using a step function as described by McCulloch and Pitts network.

Table 3.2 shows the truth table of AND logic using a single neuron:

# AND function

| Input x1 | Input x2 | x1 AND x2 | Output (x1+x2) |
|---|---|---|---|
| 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 1 |
| 1 | 0 | 0 | 1 |
| 1 | 1 | 1 | 2 |

Table 3.2: Truth table for "AND" logic using single neuron.

Considering the value of the threshold, T = 2, the following condition holds.

Output = 1; if T ≥ 2

else,

Output = 0; if T < 2

AND gate implementation using neural network is as shown in figure 3.6:

![](bbox=[0.28, 0.54, 0.72, 0.78])

Figure 3.6: AND logic gate

# Feed-forward (FF) neural networks

The feed-forward neural network is a type of AI-based neural network in which connections among the neurons or nodes do not form any cycle. It is one of the simplest neural networks that was based upon the AI technique.