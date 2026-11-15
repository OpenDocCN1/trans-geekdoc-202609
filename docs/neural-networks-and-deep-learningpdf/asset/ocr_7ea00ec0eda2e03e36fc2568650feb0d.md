In particular, by making the weights in the first hidden layer a good approximation to a step function, the output from our network will be a good approximation to any continuous function, f.

![](bbox=[0.38, 0.08, 0.6, 0.21])

What about functions of more than

Let's try three variables x₁, x₂, x₃. The following network can be used to compute a tower function in four dimensions:

![](bbox=[0.14, 0.28, 0.39, 0.53])

Here, the x₁, x₂, x₃ denote inputs to the network. The s₁, t₁ and so on are step points for neurons - that is, all the weights in the first layer are large, and the biases are set to give the step points s₁, t₁, s₂, .... The weights in the second layer alternate +h, -h, where h is some very large number. And the output bias is -5h/2.

This network computes a function which is 1 provided three conditions are met: x₁ is between s₁ and t₁; x₂ is between s₂ and t₂; and x₃ is between s₃ and t₃. The network is 0 everywhere else. That is, it's a kind of tower which is 1 in a little region of input space, and 0 everywhere else.

By gluing together many such networks we can get as many towers as we want, and so approximate an arbitrary function of three variables. Exactly the same idea works in m dimensions. The only change needed is to make the output bias (-m + 1/2)h, in order to get the right kind of sandwiching behavior to level the plateau.