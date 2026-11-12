And if we pass the car image as an input, then we get the prediction as a car, as shown in figure 6 4:

![](bbox=[0.13, 0.15, 0.86, 0.27])

# Figure 6.4: Input to CNN and prediction as Car

Therefore, here the computations, decisions, and outputs are completely independent of all the input images. But in many other applications, the input cannot be of a fixed size. Moreover, successive inputs may depend on each other or, say, may not be independent of each other.

So to understand that, let us take an example of auto-completion, which is used while we type text messages on the phone. Suppose we have given the first character d; we want to predict the next character e and the further ones till we get the full word as follows:

![](bbox=[0.29, 0.5, 0.71, 0.91])

# Figure 6.5: Word prediction