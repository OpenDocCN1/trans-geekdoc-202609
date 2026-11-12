It is the combination of one-to-many and many-to-one models. Here, the model uses the recent sequence of observations to predict the multiple output values.

**In the case of many-to-many sequence prediction models, the number of inputs does not have to match with the total number of outputs.**

# RNN architecture

Now, to understand the working of RNN, let us discuss the basic architecture of RNN, as shown in figure 6.53:

![](bbox=[0.132, 0.304, 0.867, 0.586])

**Figure 6.53: RNN architecture**

We can represent the RNN by using the following function:

```
h_{(t)} = f_c(h_{(t-1)} \times x_{(t)}) (6.3)
```

Where

+   - h(t) is the new state; [history vector],
+   - f_c is the function with parameter c,
+   - h(t – 1) is the old state; [previous history vector],
+   - x(t) is the input vector at time step t.