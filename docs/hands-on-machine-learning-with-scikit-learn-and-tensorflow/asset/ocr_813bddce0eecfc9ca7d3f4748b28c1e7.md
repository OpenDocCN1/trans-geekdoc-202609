often don't even fit in memory, and even when they do, computing the Hessians is just too slow.

# # Training Sparse Models

All the optimization algorithms just presented produce dense models, meaning that most parameters will be nonzero. If you need a blazingly fast model at runtime, or if you need it to take less memory, you may prefer to use with a sparse model instead.

One rival to achieve this is to train the model as usual, then get rid of the tiny weights (set them to 0). However, this will typically not lead to a very sparse model, and it may degrade the model's performance.

A better option is to apply strong $\ell_1$ regularization during training, then zero out to as many weights as it can (as discussed in Chapter 4 about Lasso Regression).

However, in some cases these techniques remain insufficient. One last option is to apply Dual Averaging, often called Follow The Regularized Leader (FTRL), a technique proposed by Yurii Nesterov.²⁰ When used with $\ell_1$ regularization, this technique leads to very sparse models. Keras implements a variant of FTRL called FTRL-Proximal²¹ in the FTRL optimizer.

# # Learning Rate Scheduling

Finding a good learning rate can be tricky. If you set it too high, training actually diverge (as discussed in Chapter 4). If you set it too low, training will eventually converge to the optimum, but it will take a very long time. If you set it slightly too high, it will make progress quickly at first, but it will end up dancing around the optimum, never settling down. If you have a limited computing budget, you may have to interrupt training before it has converged properly, yielding a suboptimal solution (see Figure 11-8).

²⁰ "Primal-Dual Subgradient Methods for Convex Problems," Yurii Nesterov (2005).
²¹ "Ad Click Prediction: a View from the Trenches," H. McMahan et al. (2013).