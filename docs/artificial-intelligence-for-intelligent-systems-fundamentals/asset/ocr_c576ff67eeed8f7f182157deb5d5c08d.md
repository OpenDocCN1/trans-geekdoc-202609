# Advantage:

It may be utilized in the output layer of neural networks to do multiclass classification.

# Disadvantage:

It takes a long time to compute since there are so many exponent terms to calculate.

# 2.2.2.5 Hyperbolic tangent (tanh)

Hyperbolic tangent or in short "tanh" is represented as follows:

```
$$\tanh(x) = \frac{e^x - e^{-x}}{e^x + e^{-x}}$
```

It's a lot like the sigmoid function. It has a range of -1 to +1 and is centered at zero as shown in Figure 2.9.

# Advantages:

+   - Everywhere, where it is continuous and distinct.
- It revolves around zero.
- It will set a restriction on output between -1 and +1.

# Disadvantages:

+   - It may result in a vanishing gradient issue.
- It is computationally costly.

![](bbox=[0.136, 0.673, 0.863, 0.863])

Figure 2.9 Hyperbolic tangent activation function.