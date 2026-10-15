procedure over all the layers, and that this approach could be used to successfully train even fully connected architectures.

— Page 528, Deep Learning, 2016.

Pretraining involves successively adding a new hidden layer to a model and refitting, allowing the newly added model to learn the inputs from the existing hidden layer, often while keeping the weights for the existing hidden layers fixed. This gives the technique the name layer-wise as the model is trained one layer at a time. The technique is referred to as greedy because of the piecewise or layer-wise approach to solving the harder problem of training a deep network. As an optimization process, dividing the training process into a succession of layer-wise training processes is seen as a greedy shortcut that likely leads to an aggregate of locally optimal solutions, a shortcut to a good enough global solution.

Greedy algorithms break a problem into many components, then solve for the optimal version of each component in isolation. Unfortunately, combining the individually optimal components is not guaranteed to yield an optimal complete solution.

— Page 323, Deep Learning, 2016.

Pretraining is based on the assumption that it is easier to train a shallow network instead of a deep network and contrives a layer-wise training process that we are always only ever fitting a shallow model.

... builds on the premise that training a shallow network is easier than training a deep one, which seems to have been validated in several contexts.

— Page 529, Deep Learning, 2016.

The key benefits of pretraining are:

+   - Simplified training process.
+   - Facilitates the development of deeper networks.
+   - Useful as a weight initialization scheme.
+   - Perhaps lower generalization error.

In general, pretraining may help both in terms of optimization and in terms of generalization.

— Page 325, Deep Learning, 2016.

There are two main approaches to pretraining; they are:

+   - Supervised greedy layer-wise pretraining.
+   - Unsupervised greedy layer-wise pretraining.