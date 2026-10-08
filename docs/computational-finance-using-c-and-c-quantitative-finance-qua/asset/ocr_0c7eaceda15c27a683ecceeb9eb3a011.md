# Single asset American options

This is not true of European vanilla options whose value depends on $S_t$, the underlying asset price at option maturity. The Monte Carlo approximation to the value of a European option is thus:

```
$f = \sum_{j=1}^{n_{sim}} p_j(n_j)$
```

$n_{sim}$ is the number of simulations, $n_j$ is the number of time steps associated with the $j$th price path, and $p_j(n_j)$ is the value of the $j$th price path. In the case of European vanilla options we can use $n_j = 1, 1, \dots, n_{sim}$: the accuracy obviously improves with increasing $n_{sim}$.

The valuation of American-style options, which include the possibility of early exercise, is more complicated. In Chapter 5 we described the use of binomial lattice to price options when the underlying asset process is GBM. Dynamic programming was used and the option prices were computed by backward in time through the lattice. The application of Monte Carlo for American options was described in Tilley (1993), Barraguand and Martineau (1995), and also Boyle, Broadie, and Glasserman (1997). Here we will outline the stochastic lattice approach discussed in Broadie and Glasserman (1997), where both a high estimator and a low estimator of the American option value are calculated. Since both of these biased estimators converge (with increasing number of simulations and lattice nodes) to the true option value, we will only consider how to compute the high estimator, $\theta_H$. We summarize the approach as follows

+   - Set the parameters
- Generate the lattice asset prices
- Compute the lattice option prices
- Compute the Monte Carlo estimate.

We will now consider each of these steps in detail.

# Set the parameters

First we set the simulation parameters; $n_{sim}$ is the number of lattice simulations, $b$ is the number of branches per lattice node, and $d$ is the number of time instants in the lattice. Note: this definition of $d$ is different from that used in the original paper by Broadie and Glasserman (1997) where $d$ is defined as the number of time steps in the lattice.

# Generate the lattice asset prices

Next we generate the asset prices for the $i$th stochastic lattice. The lattice is non recombining at the $b'$ nodes/asset prices. This contrasts with the binomial lattice of Chapter 5 where the asset prices at a given time step are arranged in ascending order, that is $S_j'$ increases with increasing $j$.