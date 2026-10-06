calculated as the ratio of the number of elements in log2fc with an absolute value greater than 2 to the length of log2fc This gives us an estimate of a proportion of genes that are differentially expressed. Inspecting it gives us the following output:

```
prop_de
## [1] 0.2001754
```

This shows that 20% of the features has counts changed by log2 2-fold or more.

In step 2, the is.finite() function is used to select only the finite elements of log2fc and assign the result to finite_log2fc. This is done to ensure that any potential infinite ratios caused by a zero count in the mock sample are removed safely. The plot() function is then used to create a density plot of finite_log2fc, and the qnorm() function from the extMem library is used to create a quantile-quantile plot of finite_log2fc.

In step 3, the estimateParam() function from the powsim library is used to estimate the parameters needed to run a simulation based on the data in arab_infection. The distribution of the data is specified as a negative binomial distribution, the type of RNA sequencing is specified as bulk (as ours is - which just means all the sampled RNA), and the normalization method is specified as TMM. The method is assigned to parameters.

Then, the Setup() function from powsimR is used to set up the options for the simulation run. The number of genes is set to 1000, the proportion of differentially expressed genes is set to prop_de, the log fold change ratios are set to finite_log2fc, and the estimated parameter values are set to params. The result is assigned to de_opts.

num_replicates is then defined as a vector with values of 3, 6, 12, and 18.

In step 4, the simulateDE() function from powsimR is used to run the simulation with the options specified in de_opts. The method for identifying differentially expressed genes is edgeR-LRT, the normalization method is specified as TMM, and verbosity is turned off. The result is assigned to simDE.

In step 5, the evaluate() function from powsimR is used to evaluate the results of the simulation stored in simDE. The type of adjustment is specified as adjusted, the multiple test method is specified as the Benjamini-Hochberg procedure, the normal alpha level is set to 0.1, the data is stratified by mean expression level, no filtering is applied, the first stratum is used for filtering, the target for evaluation is log fold change, and the delta value is set to 0. The result is assigned to evalDE.

In step 6, the plotEvaluateDE() function from powsimR is used to plot the evaluation stored in evalDE. The rate is specified as marginal, quick plotting is turned off, and annotation is turned on.