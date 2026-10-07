How weights got updated (Gradient descent occurs): Now let's focus on one value, let's consider just single $\epsilon_t$. Here we've calculated
the cost function epsilon:\$\epsilon_t$. Now we want to propagate that cost function back through the network.

+   - To do this, every single neuron that *participated* in the calculation of the output associated with this cost function $\epsilon_t$;
should update their weights, in order to minimize that error.

![](bbox=[0.118, 0.335, 0.882, 0.545])

But we have to note that, it's not just the neurons directly below (directly below that red circle): $\epsilon_t$.

+   - It's all the neurons that contributed (i.e. all previous time-point), all of these *neurons* as far back as we go. Depending on
how many *time-steps* you take.
- For example, you might take 50 time-steps before, then you have to update weights for all previous 50 time-steps. You
have to *propagate all the way back through time* to those neurons.

Following is the math behind RNNs, we use $W_{rec}$ and $W_{rec}$ (stands for *weight recurring*), and that is the *weight* that is used to
connect the *hidden layers* to themselves in the *unrolled temporal loop*.

![](bbox=[0.118, 0.73, 0.882, 0.958])