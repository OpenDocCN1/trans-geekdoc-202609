![](bbox=[0.15, 0.14, 0.81, 0.49])

Figure 5.3: Line Plots of Train and Test Accuracy for a Suite of Momentums on the Blobs Classification Problem.

# 5.3.3 Effect of Learning Rate Schedules

We will look at two learning rate schedules in this section. The first is the decay built into the SGD class and the second is the ReduceLROnPlateau callback.

# Learning Rate Decay

The SGD class provides the decay argument that specifies the learning rate decay. It may not be clear from the equation or the code as to the effect that this decay has on the learning rate over updates. We can make this clearer with a worked example. The function below implements the learning rate decay as implemented in the SGD class.

```
# learning rate decay
def decay_lrate(initial_lrate, decay, iteration):
    return initial_lrate * (1.0 / (1.0 + decay * iteration))
```

Listing 5.22: Example of a function for calculating a decaying learning rate.

We can use this function to calculate the learning rate over multiple updates with different decay values. We will compare a range of decay values [1E-1, 1E-2, 1E-3, 1E-4] with an initial learning rate of 0.01 and 200 weight updates.