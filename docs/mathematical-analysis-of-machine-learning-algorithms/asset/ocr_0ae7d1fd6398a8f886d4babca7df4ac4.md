# Rademacher Complexity and Concentration Inequalities

In Chapter 3 and Chapter 4, we obtained uniform convergence results using covering numbers and exponential probability inequalities. This chapter considers a different, though closely related, method. In this approach, we first bound the expectation of the supremum of an underlying empirical process using the so-called *Rademacher complexity*, and then use *concentration inequalities* to obtain high probability bounds. This approach simplifies various derivations in generalization analysis.

# 6.1 Rademacher Complexity

Using the notations from Section 3.3, we are given a function class $\mathcal{G} = \{\phi(w,z): w \in \Omega\}$, and are interested in the uniform convergence of training error

$\phi(w, \mathcal{S}_n) = \frac{1}{n} \sum_{i=1}^n \phi(w, Z_i)$

on a training data $\mathcal{S}_n = \{Z_1, \dots, Z_n\} \sim \mathcal{D}^n$, to the test error

$\phi(w, \mathcal{D}) = \mathbb{E}_{Z \sim \mathcal{D}} \phi(w, Z)$

on the test data $\mathcal{D}$. In particular, in the general analysis of learning algorithms, we want to estimate the supremum of the associated empirical process

$\sup_{w \in \Omega} [\phi(w, \mathcal{D}) - \phi(w, \mathcal{S}_n)]$.

We introduce the following definition, which will be useful in the analysis of this chapter.

**Definition 6.1** Given an empirical process $\{\phi(w, \mathcal{S}_n): w \in \Omega\}$, with $\mathcal{S}_n \sim \mathcal{D}^n$, define the expected supremum of this empirical process as

$\epsilon_n(\mathcal{G}, \mathcal{D}) = \mathbb{E}_{\mathcal{S}_n} \sup_{w \in \Omega} [\phi(w, \mathcal{D}) - \phi(w, \mathcal{S}_n)]$, 

which will be referred to as the *uniform convergence complexity* of the function class $\mathcal{G}$.

The smaller this quantity is, the closer the gap between the training error and the test error, which implies that we have less overfitting. In Chapter 3, we