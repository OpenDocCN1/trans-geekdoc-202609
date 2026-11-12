So, what is the total loss made by the network here. And how we can do the backpropagation to minimize this loss and update the weight parameters (U, V, and W) here?

So for the questions mentioned preceding, we should understand the basic phenomenon of backpropagation with time as described as follows.

So, here the total loss is the sum of all the losses over every timestamp. The loss representation is shown in figure 6.76.

![](bbox=[0.23, 0.275, 0.77, 0.72])

Figure 6.76: Next letter prediction example

So, observing the preceding figure properly, the total cross-entropy loss of the network is given as follows:

```
\( L(\theta) = \sum_{t=1}^{T} L_t(\theta) \)
```

And loss at timestamp t is given as follows:

```
\( L_t(\theta) = -log(y_{tc}) \)
```