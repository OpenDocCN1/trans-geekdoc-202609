# 6. The Score | predict action can be used to score another hex data frame in H2O:

![](bbox=[0.21, 0.148, 0.791, 0.379])

Scoring in H2O

# There's more...

For more complicated scenarios that involve a lot of preprocessing, H2O can be called from R directly. This book will focus more on building models using H2O from R directly. If H2O is set up at a different location instead of localhost, then it can be connected within R by defining the correct ip and port at which the cluster is running:

```
localH2O = h2o.init(ip = "localhost", port = 54321, nthreads = -1)
```

Another critical parameter is the number of threads to be used to build the model; by default, n threads are set to -2, which means that two cores will be used. The value of -1 for n threads will make use of all available cores.

> http://docs.h2o.ai/h2o/latest-stable/index.html#gettingstarted is very good using H2O in interactive mode.