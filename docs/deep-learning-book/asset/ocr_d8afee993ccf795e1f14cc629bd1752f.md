In comparison to the RBM energy function (equation **20.5**), the DBM energy function includes connections between the hidden units (latent variables) in the form of the weight matrices $\mathbf{W}^{(2)}$ and $\mathbf{W}^{(3)}$. As we will see, these connections have significant consequences for the model behavior as well as how we go about performing inference in the model.

In comparison to fully connected Boltzmann machines (with every unit connected to every other unit), the DBM offers some advantages that are similar to those offered by the RBM. Specifically, as illustrated in figure **20.3**, the DBM layers can be organized into a bipartite graph, with odd layers on one side and even layers on the other. This immediately implies that when we condition on the variables in the even layer, the variables in the odd layers become conditionally independent. Of course, when we condition on the variables in the odd layers, the variables in the even layers also become conditionally independent.

The bipartite structure of the DBM means that we can apply the same equations we have previously used for the conditional distributions of an RBM to determine the conditional distributions in a DBM. The units within a layer are conditionally independent from each other given the values of the neighboring layers, so the distributions over binary variables can be fully described by the Bernoulli parameters, giving the probability of each unit being active. In our example with two hidden layers, the activation probabilities are given by

$$P(v_i = 1 \mid \mathbf{h}^{(1)}) = \sigma\left(\mathbf{W}^{(1)}_{i,:}\mathbf{h}^{(1)}\right), \tag{20.26}$$

![](bbox=[0.197, 0.537, 0.811, 0.804])

Figure 20.3: A deep Boltzmann machine, rearranged to reveal its bipartite graph structure.