+   11.1 Introduction 477
+   11.2 Monte Carlo integration 477
+   11.2.1 Example: estimating π by Monte Carlo integration 478
+   11.2.2 Accuracy of Monte Carlo integration 478
+   11.3 Generating random samples from simple distributions 480
+   11.3.1 Sampling using the inverse cdf 480
+   11.3.2 Sampling from a Gaussian (Box-Muller method) 481
+   11.4 Rejection sampling 481
+   11.4.1 Basic idea 482
+   11.4.2 Example 483
+   11.4.3 Adaptive rejection sampling 483
+   11.4.4 Rejection sampling in high dimensions 484
+   11.5 Importance sampling 484
+   11.5.1 Direct importance sampling 485
+   11.5.2 Self-normalized importance sampling 485
+   11.5.3 Choosing the proposal 486
+   11.5.4 Annealed importance sampling (AIS) 486
+   11.6 Controlling Monte Carlo variance 488
+   11.6.1 Common random numbers 488
+   11.6.2 Rao-Blackwellization 488
+   11.6.3 Control variates 489
+   11.6.4 Antithetic sampling 490
+   11.6.5 Quasi-Monte Carlo (QMC) 491

# 12 Markov chain Monte Carlo 493

+   12.1 Introduction 493
+   12.2 Metropolis-Hastings algorithm 494
+   12.2.1 Basic idea 494
+   12.2.2 Why MH works 495
+   12.2.3 Proposal distributions 496
+   12.2.4 Initialization 498
+   12.3 Gibbs sampling 499
+   12.3.1 Basic idea 499
+   12.3.2 Gibbs sampling is a special case of MH 499
+   12.3.3 Example: Gibbs sampling for Ising models 500
+   12.3.4 Example: Gibbs sampling for Potts models 502
+   12.3.5 Example: Gibbs sampling for GMMs 502
+   12.3.6 Metropolis within Gibbs 504
+   12.3.7 Blocked Gibbs sampling 504
+   12.3.8 Collapsed Gibbs sampling 505
+   12.4 Auxiliary variable MCMC 507
+   12.4.1 Slice sampling 507
+   12.4.2 Swendsen-Wang 509
+   12.5 Hamiltonian Monte Carlo (HMC) 510
+   12.5.1 Hamiltonian mechanics 511
+   12.5.2 Integrating Hamilton's equations 511
+   12.5.3 The HMC algorithm 513
+   12.5.4 Tuning HMC 514
+   12.5.5 Riemann manifold HMC 515
+   12.5.6 Langevin Monte Carlo (MALA) 515
+   12.5.7 Connection between SGD and Langevin sampling 516
+   12.5.8 Applying HMC to constrained parameters 517
+   12.5.9 Speeding up HMC 518
+   12.6 MCMC convergence 518
+   12.6.1 Mixing rates of Markov chains 519
+   12.6.2 Practical convergence diagnostics 520