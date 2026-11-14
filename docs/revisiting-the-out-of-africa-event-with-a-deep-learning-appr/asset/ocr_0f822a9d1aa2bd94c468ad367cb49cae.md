![](bbox=[0.14, 0.04, 0.86, 0.42])

Figure 1. The simplistic schema of the models (A–C) Simple out of Africa (model S) (A), back to Africa (model B) (B), and out of Africa mixed (model M) (C). Please consult Table 1 for more details of time parameters (in y axis) and Table S10 for the interdependencies of those parameters. AFR is African, EUR is European, and ASN is East Asian. X is African archaic, N is Neanderthal, and D is Denisova.

Simulations from every step were stored and re-used in subsequent cycles if their parameter values fell inside the new prior range. A flow chart of this strategy can be found in Figure S2C.

We used 10,000 simulations as a training dataset and 10,000 simulations for testing. The NN model is exactly as before (as used in DL, Figure S1). To make it more efficient, we started with simulating a total length of 100 Mb (each simulated region being 1 Mb long), and then we increased the total length stepwise (i.e., 0.5, 1.5, and 3 Gb). The priors for 100 Mb regions are the same as presented in Table 1. The final posterior (after convergence reached) of the run with 100 Mb is used as a prior for 0.5 Gb simulation and so on. We multiplied the observed SFS by frac accordingly to scale it to the simulated region length.

After the convergence was reached with 3 Gb in total, we finalized by running 50,000 training and 10,000 testing simulations with the DL method by using loclinear (from abc package) with the tolerance of 0.01. The flowchart of the method is represented in Figure S3.

# Model selection with DLS

Here, we describe model selection by using NN, ABC, and SMC together. In principle, we can directly use the final output of the parameter estimation procedure by DLS for every model and then use it for the ABC classification approach. However, this approach would be inefficient given that only one model is true for our real dataset, and thus spending considerable resources to optimize parameters for unlikely scenarios does not make sense. Instead, we used the output of 100 Mb parameter optimizations from the DLS approach as a prior to every model, and then we used the model selection strategy of DL, as mentioned before. In

other words, we first optimized the parameters for each model class by using 100 Mb of simulated sequence and then compare the different models between each other. We found out that we already have enough power to distinguish between models by using 100 Mb of total simulated sequence for most of the cases, except Table S7 where we used 500 Mb regions for optimization.

# ABC-RF

We tested the real SFS against the three simulated models by using a similar ABC approach but with random forest^61 (here onward, we call this implementation RF) as an inferential tool implemented in the abcrf R package.^43,62 First, we trained our model by using the bagging method applying the function abcrf, with no linear discriminant analysis, and 2,000 decision trees by using 1,000 simulations for each tested model. We then evaluated the performance of ABC-RF through a cross-validation dataset composed of 1,000 simulations for each tested model by using the function predict.abcrf. The same function and settings were used for inferring the best-supported model with the SFS obtained from real data described above. We performed parameter estimation for the most supported scenario applying regression as implemented in the regAbcrf model by using 1,000 decision trees. Each parameter was inferred separately. Similar to DL and DLS approaches, the whole procedure has been repeated ten times for model selection.

# Demographic models

# Simple out of Africa (model S)

In this simulation model, we have modeled a simple OOA event (Figure 1A) closely following Gravel et al.,^19 except the migration