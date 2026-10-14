# Listing 6.2 Hierarchical Bayesian regression

```
```python
import numpy as np
import pandas as pd

import seaborn as sns
import matplotlib.pyplot as plt

import pymc3 as pm

def main():
    data = pd.read_csv('./data/radon.txt')  ← Load data

    county_names = data.county.unique()
    county_idx = data['county_code'].values

    with pm.Model() as hierarchical_model:
        mu_a = pm.Normal('mu_alpha', mu=0., sd=100**2)
        sigma_a = pm.Uniform('sigma_alpha', lower=0,
            upper=100)
        mu_b = pm.Normal('mu_beta', mu=0., sd=100**2)
        sigma_b = pm.Uniform('sigma_beta', lower=0,
            upper=100)
        
        a = pm.Normal('alpha', mu=mu_a, sd=sigma_a,
            shape=len(data.county.unique()))  ← Intercept for each county
        b = pm.Normal('beta', mu=mu_b, sd=sigma_b,
            shape=len(data.county.unique()))  ← Slope for each county

        eps = pm.Uniform('eps', lower=0, upper=100)  ← Model error

        radon_est = a[county_idx] + b[county_idx] *
            data.floor.values  ← Expected value

        y_like = pm.Normal('y_like', mu=radon_est, sd=eps,
            observed=data.log_radon)  ← Data likelihood

    with hierarchical_model:
        # Use ADVI for initialization
        mu, sds, elbo = pm.variational.advi(n=100000)
        step = pm.NUTS(scaling=hierarchical_model.dict_to_array(sds)**2,
            is_cov=True)
        hierarchical_trace = pm.sample(5000, step, start=mu)

    pm.traceplot(hierarchical_trace[500:])
    plt.show()

if __name__ == "__main__":
    main()
```
```

From the trace plots in figure 6.5, we can see convergence in our posterior distributions for α_c and β_c, indicating different intercepts and slopes for different counties.