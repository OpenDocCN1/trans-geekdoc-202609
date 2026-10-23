![](bbox=[0.25, 0.1, 0.8, 0.48])

# FIGURE 2.11

The multilayer construction of a neural network. Each colored circle represents a neuron (which passes the aggregated signal through an activation function) and the lines are the inputs and output connecting them. In this example, only a single hidden layer is shown. In practice, multiple hidden layers are used.

> From SciForce: white paper on Top Algorithms for Health", by permission of M. Ved, "Top Algorithms for Healthcare" SciForce-Medium.

for the following reason: since we know the inputs and receive output data, both these layers are known to us. In contrast, the layers in between are not readily accessible to the observer. Since the computer has no cognition, each run of the algorithm is, in essence, a double-blind experiment. This has raised philosophical issues about the explainability of deep learning models.

The basic features of an ANN are as follows:

+   - Each input neuron gets only one input, directly from outside; those of the hidden layers get many.
+   - Neurons in a layer do not connect to each other.
+   - Each neuron in one layer connects to all the neurons in the next layer.
+   - The ANN is a synchronous model; all nodes in a given layer receive their inputs and calculate their activities at the same time. This means that all the calculations in the n layer must be calculated before we can start the calculations for the (n+1) layer.