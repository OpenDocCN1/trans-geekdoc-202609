# 7.5 CONCLUSIONS

![](bbox=[0.297, 0.083, 0.702, 0.269])

**Figure 27: Phase diagram of generalization dynamics vs. memorization in different training regimes as a function of training time τ and sample complexity P: partial generalization, (full) generalization and memorization. Note that in the simplest version of the RHM, learning proceeds by well-distinct steps, while it is smoother for natural data (or more realistic versions of the RHM [KW23]).**

unstructured noise. In the diffusion context, instead, the empirical score at low noise levels significantly differs from the population noise i.e., the corresponding “noise”, i.e., the difference between the two functions, is inherent to the training set, structured, and defined over the entire domain of the inputs xᵢ. An overparameterized model converging to the empirical target, therefore, memorizes the training set and cannot generalize. This contrasts with noisy regression, where overparameterization can surprisingly be beneficial, leading to double descent [Spi19; Bel+19] and benign overfitting [Bar+20].

# 7.5 CONCLUSIONS

We have argued that the learning dynamics in diffusion models is best understood as a competition between time scales, as summarized in Figure 27. A larger training time implies a larger memorization time, opening a larger time window to generate more coherent data. These results open new avenues for fine control of copyright issues, using early stopping to avoid memorization and building backward flows that are nearly independent of the training set, as demonstrated.