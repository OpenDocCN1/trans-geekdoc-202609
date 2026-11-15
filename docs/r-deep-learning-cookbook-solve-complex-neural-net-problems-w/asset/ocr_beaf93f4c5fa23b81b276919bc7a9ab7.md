# Setting up a Deep Restricted Boltzmann Machine

Unlike DBNs, **Deep Restricted Boltzmann Machines (DRBM)** are undirected networks of interconnected hidden layers with the capability to learn joint probabilities over these connections. In the current setup, centering is performed where visible and hidden variables are subtracted from offset bias vectors after every iteration. Research has shown that centering optimizes the performance of DRBMs and can reach higher log-likelihood values in comparison with traditional RBMs.

# Getting ready

This section provides the requirements for setting up a DRBM:

+   - The MNIST dataset is loaded and set up
+   - The tensorflow package is set up and loaded

# How to do it...

This section covers detailed the steps for setting up the DRBM model using TensorFlow in R:

+   1. Define the parameters for the DRBM:
+   
+   ```
+   learning_rate = 0.005
+   momentum = 0.005
+   minbatch_size = 25
+   hidden_layers = c(400,100)
+   biases = list(-1,-1)
+   ```

+   2. Define a sigmoid function using a hyperbolic arc tangent [(log(1+x)-log(1-x))/2]:
+   
+   ```
+   arcsigm <- function(x) {
+   return (atanh ( (2*x)-1 )*2)
+   }
+   ```

+   3. Define a sigmoid function using only a hyperbolic tangent [(e^x-e^-x)/(e^x+e^x)]:

```
sigm <- function(x) {
return (tanh ( (x/2) +1 )/ 2)
}
```