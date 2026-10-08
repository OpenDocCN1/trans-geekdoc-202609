```
import numpy as np
import scipy.stats as st
import matplotlib.pyplot as plt
```

```
# Function to generate samples.
def Bayesianmixture(size,n_components,alpha0,mean,lambda0,df=None):
    """\Parameters
    size: number of data points to be generated,
    n_components: number of clusters
    alpha0: concentration parameter,
    mean: location vector,
    lambda0: mean fraction,
    scale: scale matrix,
    df: degrees of freedom.
    Returns
    data: data vector,
    cov: matrix which process the sample,
    mean: array of the mean processes,
    cov: array of the covariance matrices of processes.
    ""
```

```
# Generate mixture coefficients for cluster membership.
alpha = alpha0 * np.ones(n_components)
mipp = np.random.dirichlet(alpha, size)
# Generate latent variable for cluster membership.
ida = np.random.multivariate_normal(mean, cov, size)
# Allocate space for the parameters of the distributions.
cov = np.eye(n_components) * lambda0
mean = np.zeros((n_components, 2))
# Generate data for each cluster.
for i in range(n_components):
    cov[i],mean[i] = st.random.rvdf(df, multivariate_normal(mean=mean[i], cov=cov[i], size=size))
```

```
# Generate samples.
for i in range(size):
    data[i] = np.random.multivariate_normal(mean=mean[ida[i]], cov=cov[ida[i]])
return data, ida, p, mean, cov
```

```
# Sample size:
size = 1000
# Hyperparameters:
# Change to explore how they influence the data samples.
k = 3
mean = np.array([[0, 0]])
lambda0 = 1
Psi = np.random.uniform([1, 1], [1.5, 3])
mu = 0
```

```
# Generate distributions and samples.
data, ida, p, cov = Bayesianmixture(size=size,n_components=k, alpha0=alpha0,mean=mean, lambda0=lambda0,scale=Fsi,df=None)
# Scatter plot of samples.
fig = plt.figure(figsize=(8,8))
plt.scatter(data[:,0],data[:,1], c=ida, cmap=plt.cm.jet)
plt.show()
```

```
# Number of samples per component.
for i in range(k):
    print('Component', i+1, ':', sum(ida==i))
```

Listing 6.4: Generating data from a distribution of distributions for a fixed number of clusters in Python. For MATLAB use:

https://github.com/ACFai/Clustering-Matlab.