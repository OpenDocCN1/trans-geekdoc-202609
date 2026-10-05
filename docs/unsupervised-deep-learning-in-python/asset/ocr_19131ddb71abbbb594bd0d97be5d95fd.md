# # Chapter 6: Tricking a Neural Network

Now that you know how to take the derivative of a variable with respect to the inputs instead of the weights, we are ready to talk about how to trick a neural network.

The key is the cost function, J.

We want to increase the cost function as much as possible, while inducing minimal changes in X.

To do that, we simply ask, "in what direction should I change X, such that it results in the maximum change in J?"

This is again just a calculus problem - we want to find dJ/dX.

And again, we use Theano to automatically calculate the gradient.

Once you've done that, we simply change X by a small amount in that direction.

```
X = X + eps*dJ/dX
```

Where eps is a small number.

What you should find that is the image itself doesn't look any different (remember, matplotlib will scale your values to be from 0..255), but the neural network has a good chance of classifying the image wrong, even when it classifies the original image right.

What implications does this have in terms of training a neural network?

You surely don't want your neural network to be so easily fooled, and the key here is something we've already talked about before:

Data augmentation.