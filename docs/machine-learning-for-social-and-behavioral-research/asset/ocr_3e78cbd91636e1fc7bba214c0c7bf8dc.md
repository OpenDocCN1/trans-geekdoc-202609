In contrast, the predictors represent something like blood-oxygen-level-dependent (BOLD) signals from magnetic resonance imaging (MRI), using rules of this like for PCA may work much better.

# 7.6.2 Variable Network Models

Developed on a separate track than that of factor analysis, graphical models, or Bayesian networks (in the directed case) have obvious similarities because of their graphical nature. Their development originated in computer science (Pearl, 1988), and have been more focused on explicating the “causal” relationship between variables without having to resort to longitudinal designs (Pearl, 2000); for causality in SEM, see Bollen & Pearl, 2013). The similarities between methodologies have spawned hybrid models (Duarte, Clementis, Harris, Cardel, & Fernandez, 2011) that capitalize on each framework's strengths, as well as models that build upon their equivalence with Gaussian variables (Buhlmann, Peters, & Ernst, 2014; Shimizu, Hoyer, Hyvärinen, & Kivkinen, 2006).

Here

In graphical models, the models are not specified a priori, it is common to use some form of “search” to find the optimal model given the dataset. Although greedy, stochastic search algorithms were at the outset (Chickering, 2003), most recently regularization has seen a wide variety of applications with graphical models (Friedman, Hastie, & Tibshirani, 2007; Meinshausen & Buhlmann, 2006; Yuan, & Lin, 2007). Although these proposed methods are similar in many senses, the method that has potentially seen the most application of the graphical lasso