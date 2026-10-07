# Inverter-based memristive neuromorphic circuit 27

Algorithm 1. Pseudo code for the proposed training algorithm

**Input:** Patterns

```
1: Trained weights
2: While (maximum number of iterations < than specified) or
3:   (Cost function j is > than specified) do
4:   For every pattern do
5:     Present the pattern to the network
6:     // Propagated the input forward through the network:
7:     For each layer in the network do
8:       Calculate the mapped weights using g1 and g2
9:       For every node in the layer do
10:        Calculate the weighted sum of the inputs to the node
11:        Calculate the activation for the node
12:        Calculate the Cost function j
13:  Propagate the error backward through the network:
14:  For every node in the output layer do
15:    Calculate the error signal (tk - Ok)
16:    Update θ’s in the output layer using (11.21) and (11.26)
17:  For all hidden layers do
18:    For every node j in the layer do
19:      Calculate the jth node signal error (Σk∈(l+1) δkWjk^(l+1)))
20:  Update θ’s in that layer using (11.21) and (11.26)
21: Return Thetas
```

rj is the expected output of the jth neuron of the last layer and L last layer of the network. In this case, the output of the jth neuron in the th layer is defined by

> $O_j^l = f_j^l(\sum_{jkp}^l O_{kp}^{l-1} + 	heta_{jkn}^l O_{kn}^{l-1} + eta_p^l b'_p + eta_n^l b'_n) \quad (11.19)$

where f_j^l is the activation function of the jth neuron in the th layer and θ_{jk}^l is the weight from the positive (negative) output of the kth neuron in the (i-1) last layer to the jth neuron in layer. Moreover, b'_p(b'_n) denote the positive (negative) bias in the th layer and β_p^l(β_n^l) are the corresponding positive (negative) weights. In this work, V_{DD}/2) is considered for all layers.

Now, in the following, we provide the details for extracting the update equations in the case of the positive weights. The updating rule for the negative weights are also similar. For extracting the update equations, we use a method called function mapped weights that has been proposed in [18] (see Figure 11.7). To employ