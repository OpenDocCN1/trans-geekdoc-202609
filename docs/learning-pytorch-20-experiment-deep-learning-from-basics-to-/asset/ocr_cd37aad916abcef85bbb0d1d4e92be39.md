# optimizer.step()

In the training loop, optimizer.zero_grad() is called to zero out the gradients, because PyTorch accumulates gradients by default. loss.backward() computes the gradients, and optimizer.step() updates the model parameters based on these gradients.

# Stochastic Gradient Descent

Stochastic Gradient Descent (SGD) is a variation of the Gradient Descent algorithm, where instead of performing computations on the whole dataset—which is the basis of standard (or "Batch") Gradient Descent—you calculate the gradient and update weights based on small subsets of the data, or "mini-batches".

This has a couple of key advantages:

Computational efficiency: It can make large-scale, computationally intensive models feasible to train, as only a fraction of the data needs to be loaded into memory for each step of training.

Frequent updates: The frequent updates can lead to faster convergence towards the minimum of the loss