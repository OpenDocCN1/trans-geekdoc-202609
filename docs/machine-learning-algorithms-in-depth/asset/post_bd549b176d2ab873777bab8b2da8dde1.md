
Let $p_{XY}(i,j)=|x_i\cap y_j|/N$ be the probability that a label belongs to cluster $x_i$ in $X$ and $y_j$ in $Y$. Define $p_X(i)=|x_i|/N$ and $p_Y(j)=|y_j|/N$ similarly. Then, we get the following equation.

$$I(X;Y)=\sum_i\sum_j p_{XY}(i,j)\log\frac{p_{XY}(i,j)}{p_X(i)p_Y(j)} \tag{8.3}$$

Thus, NMI lies between 0 and 1, with higher values indicating more similar label assignments. The variation of information ($VI$) is defined as follows.

$$VI(X;Y)=H(X)+H(Y)-2I(X;Y)=H(X|Y)+H(Y|X) \tag{8.4}$$

Thus, $VI$ decreases as the overlap between label assignments $X$ and $Y$ increases. The ARI computes a similarity measure between two clusters by considering all pairs of samples and counting pairs assigned in the same or different clusters in the predicted and true clusters.

$$\begin{aligned}
ARI &= \frac{RI-E[RI]}{\max RI-E[RI]}\\
RI &= \frac{TP+TN}{TP+FP+FN+TN}
\end{aligned} \tag{8.5}$$

Thus, ARI approaches 1 for cluster assignments that are similar to each other. Let’s implement the Dirichlet process K-means algorithm from scratch!

## Listing 8.1 Dirichlet process K-means

```python
import numpy as np
import matplotlib.pyplot as plt

import time
from sklearn import metrics
from sklearn.datasets import load_iris

np.random.seed(42)

class dpmeans:

    def __init__(self,X):
        self.K = 1
        self.K_init = 4
        self.d = X.shape[1]
        self.z = np.mod(np.random.permutation(X.shape[0]),self.K)+1
        self.mu = np.random.standard_normal((self.K, self.d))
        self.sigma = 1
```

```python
self.nk = np.zeros(self.K)
self.pik = np.ones(self.K)/self.K

self.mu = np.array([np.mean(X,0)])
self.Lambda = self.kpp_init(X,self.K_init)
self.max_iter = 100
self.obj = np.zeros(self.max_iter)
self.em_time = np.zeros(self.max_iter)

def kpp_init(self,X,k):

    [n,d] = np.shape(X)
    mu = np.zeros((k,d))
    dist = np.inf*np.ones(n)

    mu[0,:] = X[int(np.random.rand() *n-1),:]
    for i in range(1,k):
        D = X-np.tile(mu[i-1,:], (n,1))
        dist = np.minimum(dist, np.sum(D*D,1))
        idx = np.where(np.random.rand() <
    np.cumsum(dist/float(sum(dist))))
        mu[i,:] = X[idx[0][0],:]
        Lambda = np.max(dist)

    print "Lambda: ", Lambda

    return Lambda

def fit(self,X):

    obj_tol = 1e-3
    max_iter = self.max_iter
    [n,d] = np.shape(X)

    obj = np.zeros(max_iter)
    em_time = np.zeros(max_iter)
    print 'running dpmean !.'

    for iter in range(max_iter):
        tic = time.time()
        dist = np.zeros((n,self.K))

        for kk in range(self.K):
            Xm = X - np.tile(self.mu[kk,:],(n,1))
            dist[:,kk] = np.sum(Xm*Xm,1)

        dmin = np.min(dist,1)
        self.z = np.argmin(dist,1)
        idx = np.where(dmin > self.Lambda)

        if (np.size(idx) > 0):
            self.K = self.K + 1
            self.z[idx[0]] = self.K-1 #cluster labels in [0,...,K-1]
```

Initializes mean

Initializes lambda

K++ initialization

Lambda is the max distance to k++ means

Assignment step

Updates labels

```python
MI = Hx + Hy - Hxy;
nmi = MI/float(0.5*(Hx+Hy))

return nmi

def generate_plots(self,X):
    plt.close('all')
    plt.figure(0)
    for kk in range(self.K):
        #idx = np.where(self.z == kk)
        plt.scatter(X[self.z == kk,0], X[self.z == kk,1], \
                    s = 100, marker='o', c = np.random.rand(3,),
                    label = str(kk))
    #end for
    plt.xlabel('X1')
    plt.ylabel('X2')
    plt.legend()
    plt.title('DP-means clusters')
    plt.grid(True)
    plt.show()

    plt.figure(1)
    plt.plot(self.obj)
    plt.title('DP-means objective function')
    plt.xlabel('iterations')
    plt.ylabel('penalized l2 squared distance')
    plt.grid(True)
    plt.show()

if __name__ == "__main__":

    iris = load_iris()
    X = iris.data
    Y = iris.target

    dp = dpmeans(X)
    labels, obj, em_time = dp.fit(X)
    dp.generate_plots(X)

    nmi = dp.compute_nmi(Y,labels)
    ari = metrics.adjusted_rand_score(Y,labels)

    print("NMI: %.4f" % nmi)
    print("ARI: %.4f" % ari)
```

The performance of DP-means algorithm is shown in figure 8.2. The performance of the DP-means algorithm was evaluated on the iris dataset. We can see good clustering results based on high NMI and ARI metrics. In the following section, we’ll discuss a popular clustering algorithm that models each cluster as a Gaussian distribution, taking into account not just the mean but also the covariance information.

![](img/325742126d3ff007c6c385f4ffb5c3be_191_0.png)

![](img/325742126d3ff007c6c385f4ffb5c3be_191_1.png)

Figure 8.2 DP-means cluster centers (left) and objective (right) for the iris dataset

## 8.2 Gaussian mixture models

Mixture models are commonly used to model complex density distributions. For example, you may be interested in discovering patterns in census data consisting of information about the person's age, income, occupation, and other dimensions. If we plot the resulting data in high-dimensional space, we'll likely discover nonuniform density characterized by groups or clusters of data points. We can model each cluster using a base probability distribution. Mixture models consist of a convex combination of K base models. In the case of Gaussian mixture models, the base distribution is Gaussian and can be written as follows.

$p(x_i|\theta)=\sum_{k=1}^{K}\pi_k p_k(x_i|\theta)=\sum_{k=1}^{K}\pi_k\mathcal{N}(x_i|\mu_k,\Sigma_k)\tag{8.6}$

Here, $\pi_k$ are the mixing proportions that satisfy $0 \le \pi_k \le 1$ and $\sum\pi_k=1$. In contrast to K-means that only models cluster means, GMM models the cluster covariance as well. Thus, GMMs can capture the data more accurately.

### 8.2.1 Expectation maximization (EM) algorithm

The expectation maximization (EM) algorithm provides a way of computing ML/MAP estimates when we have unobserved latent variables or missing data. EM exploits the fact that if the data were fully observed, then the ML/MAP estimates would be easy to compute. In particular, EM is an iterative algorithm that alternates between inferring the latent variables, given the parameters (E step) and then optimizing the parameters given filled-in data (M step).

In the EM algorithm, we define the complete data log likelihood $l_c(\theta)$, where $x_i$ are the observed random variables and $z_i$ are unobserved. Since we don't know $z_i$, we

can’t compute $p(x_i, z_i | \theta)$, but we can compute an expectation of $\ell_c(\theta)$ wrt to parameters $\theta^{(k-1)}$ from the previous iteration.

$$l_c(\theta) = \sum_{i=1}^{N} \log p(x_i, z_i | \theta) \tag{8.7}$$

The goal of the E step is to compute $Q(\theta, \theta^{(k-1)})$, on which the ML/MAP estimates depend. The goal of the M step is to recompute $\theta$ by finding the ML/MAP estimates.

$$\text{E-step} : \quad Q\left(\theta, \theta^{(k-1)}\right) = E_{\theta^{(k-1)}}\left[\ell_c(\theta) | D, \theta^{(k-1)}\right]$$ $$\text{M-step} : \quad \theta^{(k)} = \arg\max_{\theta} Q\left(\theta, \theta^{(k-1)}\right) + \log p(\theta) \tag{8.8}$$

To derive the EM algorithm for GMM, we first need to compute the expected complete data log likelihood.

$$Q(\theta, \theta^{(k-1)}) = E\left[\sum_i \log p(x_i, z_i | \theta)\right]$$ $$= \sum_i E\left[\log \prod_{k=1}^{K} \left(\pi_k p(x_i | \theta_k)\right)^{\mathbf{1}\{z_i=k\}}\right]$$ $$= \sum_i \sum_k E\left[\mathbf{1}\{z_i = k\}\right] \log \left[\pi_k p(x_i | \theta_k)\right]$$ $$= \sum_i \sum_k p\left(z_i = k | x_i, \theta^{(k-1)}\right) \log \left[\pi_k p(x_i | \theta_k)\right]$$ $$= \sum_i \sum_k r_{ik} \log \pi_k + \sum_i \sum_k r_{ik} \log p(x_i | \theta_k) \tag{8.9}$$

Here, $r_{ik} = p(z_i = k | x_i, \theta^{(k-1)})$ is the soft assignment of point $x_i$ to cluster $k$.

We now start the E step. Given $\theta^{(k-1)}$, we want to compute the soft assignments.

$$r_{ik} = p\left(z_i = k | x_i, \theta^{(k-1)}\right)$$ $$= \frac{p\left(z_i = k, x_i | \theta^{(k-1)}\right)}{\sum_{k=1}^{K} p\left(z_i = k, x_i | \theta^{(k-1)}\right)}$$ $$= \frac{p\left(x_i | z_i = k, \theta^{(k-1)}\right) \pi_k}{\sum_{k=1}^{K} p\left(x_i | z_i = k, \theta^{(k-1)}\right) \pi_k} \tag{8.10}$$
