Once again, you find a solution close to the one returned by the Normal Equation:

```
>>> sg_reg_intercept_, sg_reg_coef_
(array([4.24365286]), array([2.2850878]))
```

# Mini-batch Gradient Descent

The last Gradient Descent algorithm we will look at is called Mini-batch Gradient Descent. It is quite simple to understand once know Batch and Stochastic Gradient: at each step, instead of computing the gradients based on the full training set (as Batch GD) or on just one instance (as Stochastic GD), Mini-batch computes the gradients on small random sets of instances called mini-batches. The main advantage of Mini-batch GD over Stochastic GD is that you can get a performance boost from hardware optimization of matrix operations, especially when using GPUs.

The algorithm's progress in parameter space is less erratic than SGD, with fairly large mini-batches. As a result, Mini-batch GD will end up reaching a bit closer to the minimum than SGD. But, on the other hand, it may be harder for it to escape local minima (in the case of problems that suffer from local minima, unlike Linear Regression as we saw earlier). Figure 4-11 shows the paths taken by the three Gradient Descent algorithms in parameter space during training. They all end near the minimum, but Batch GD's path actually stops at the minimum, while both Stochastic GD and Mini-batch GD continue to walk around. However, don't forget that Batch GD takes a lot of time to take each step, and Stochastic GD and Mini-batch GD would also reach the minimum if you used a good learning schedule.

![](bbox=[0.14, 0.595, 0.857, 0.819])

Figure 4-11. Gradient Descent paths in parameter space