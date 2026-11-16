# # An Active Learning Approach to Iterative Combinatorial Auctions

# ## A.1 Hyperparameters

We present the values of the parameters for the different auction models and bidders. The Table A.1.1 contains the general hyperparameters for DL-ICA, Table A.1.2 and Table A.1.3 contain the parameters used for the neural networks, Table A.1.4 the non neural networks related parameters. For all hyperparameters we closely followed the work by [285]. We shortly summarize the meaning of the hyperparameters in Table A.1.1:

+   - $k$ : Denotes the number of starting samples. Only necessary with the sampling techniques GALO and GALI + UF. In these two sampling techniques the first $k$ bundles get determined with GALI, the rest of the initial bundles with GALO or UF.
+   - $c_0$ : Number of initial bundles sampled before the iterative phase.