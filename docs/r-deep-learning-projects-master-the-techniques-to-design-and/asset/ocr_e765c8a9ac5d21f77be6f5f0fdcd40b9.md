If you run into trouble, chances are that there is some dependency missing. Re-read the error message and install any missing packages.

If it all goes smoothly, import the library and initialize the service to check that everything works:

```
install.packages ("h2o")
library(h2o)
h2o.init()
```

# Our first examples

Let's begin with a few simple examples to understand what is going on.

For some of us, it's very easy to get tempted to try the shiniest algorithms and do hyper-parameter optimization instead of the less glamorous step-by-step understanding.

# A simple 2D example

Let's develop our intuition of how the autoencoder works with a simple two-dimensional example.

We first generate 10,000 points coming from a normal distribution with mean 0 and variance 1:

```
library (MASS)
library (keras)
Sigma <- matrix(c(1,0,0,1),2,2)
n_points <- 10000
df <- mvrnorm(n=n_points, rep(0,2), Sigma)
df <- as.data.frame(df)
```