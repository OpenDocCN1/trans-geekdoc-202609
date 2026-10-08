# Single asset American options

```
jj = 2;
for (ml = 2; ml >= 1; --ml) {
  ind = M-ml;
  for (n = 0; n < N; ++n) {
    hold = P*v[5-jj-1] + p_u*v[5-jj];
    if (is_american) {
      if (put)
        v[5-jj] = MAX(hold,s[ind]);
      } else
        v[5-jj] = MAX(hold,s[ind]-X);
      }
    } else {
      v[5-jj] = hold;
      --jj;
      ind = ind + 2;
    }
  }
  *value = v[5];
```

**Code excerpt 5.9** Code fragment illustrating how the option values are stored for the first two time steps so the Greeks can be computed in the vicinity of the root node R.

| Node | Time step | Asset array element | Asset value | Option array element |
|---|---|---|---|--|
| R | 0 | s [M] | S | v[5] |
| S | 1 | s [M+1] | Su | v[4] |
| T | 1 | s [M-1] | Sd | v[3] |
| U | 2 | s [M+2] | Su² | v[2] |
| V | 2 | s [M] | S | v[1] |
| W | 2 | s [M-2] | Sd² | v[0] |

**Table 5.4** Lattice nodes in the vicinity of the root node R

# Computing the Greeks: $\Delta$, $\Gamma$ and $\Theta$

We will now describe how to calculate the option's hedge statistics (Greeks). Let the option value and asset value at lattice node $k$ be denoted by $f_k$ and $S_k$ respectively. So, for instance, $S_T$ represents the asset price at node $T$ and $f_T$ is the corresponding option value at node $T$. Table 5.4 supplies details of the lattice nodes in the vicinity of the root node R. The computation of each Greek is now considered.

# Delta

The definition of $\Delta$ is the rate of change of the option value with asset price all other parameters remaining fixed. Thus,

> $\Delta = \frac{\partial f}{\partial S} = \frac{\Delta f}{\Delta S}$

Where $\Delta f$ is the change value corresponding to the change in the asset price S. Ideally we would like to evaluate this partial derivative at the root node R (ml=0); however, we cannot because we need at least two lattice nodes to compute a value. The best we can do is to evaluate the derivative at the first time step (ml=1) as follows:

> $\Delta = \frac{f_S - f_T}{S_S - S_T} = \frac{v[4] - v[3]}{s[M+1] - s[M-1]}$