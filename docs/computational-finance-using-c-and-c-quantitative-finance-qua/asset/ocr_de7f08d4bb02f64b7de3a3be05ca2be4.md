# Single asset American options

easy reference we will now list the input parameters used by this computer program:

+   S0 the current price of the underlying asset, S
X the strike price
sigma the volatility of the asset
T the maturity of the option in years
r the risk-free interest rate
q the continuous dividend yield
put if put equals 1 then the option is a put
option, if put equals 0 then it is a call option
is_american if is_american equals 1 then it is an
American option, if is_american equals 0 then it is a
European option
M the number of time steps in the lattice

We will now discuss in more the computational issues involved in each stage of the calculation.

# Compute the values of the constants used by the lattice

First calculate the values of various constants that will be used, Code excerpt 5.5.
For convenience, we have used the variables p_u and p_d to store, respectively, the up and down jump probabilities discounted by the interest rate r over one time step; these values will be later on when we backwards through the lattice to calculate the current option value.

# Assess the asset values to the lattice nodes

We will show that the number of different asset prices, LSn, for an n step recombining lattice is 2n+1.
The nodes in a recombining lattice can be considered as composed of two kinds: those corresponding to an even time step, and those corresponding to an odd time step.
This is because of set of node asset values, ET, for an even time step is distinct from the set of node asset values, OT, for an odd time step. Although

```
dt = T/(double)M;
t1 = sigma*sqrt(dt);
u = exp(t1);
d = exp((r-q)*dt);
a = (a - d)/u - d;
pif ((p <= zero) || (p > 1.0)) printf("Error p out of range\n");
discount = exp(-r*dt);
p_u = discount*p;
p_d = discount*(1.0-p);
```

Code excerpt 5.5 A code fragment which computes the values of various lattice constants.