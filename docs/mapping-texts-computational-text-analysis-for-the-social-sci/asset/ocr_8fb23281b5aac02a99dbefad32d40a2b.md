# Figure 11.6: Gender Bias in Star Trek: TNG, Season 5.

![](bbox=[0.145, 0.145, 0.655, 0.535])

# # WORD EMBEDDINGS: THE NEXT GENERATION

Applying SVD to a (PPMI weighted) TCM is one way of creating word vectors. But it’s not the most popular.29 Broadly, there are three popular embedding methods: the global approach, the neural network approach, and newer “contextualized” approaches. We’ll discuss each in the following.

29 For one, SVD may not perform well on large corpora (Pennington et al. 2014:1539).

# ## The Global Approach: GloVe

One of the most popular algorithms for training word vectors is the GloVe model (Pennington et al. 2014)—a.k.a., the “Global Vectors” model. GloVe is a combination of two training methods: “global” matrix factorization (thus, the global part of the name) and “local” window-sliding methods (Pennington et al. 2014:1532). The matrix of right singular vectors that we get from a latent semantic analysis (LSA) on a DTM30 are word vectors—only the context is the entire document. This is “global”

30 See Core Inductive.