![](bbox=[0.1, 0.08, 0.9, 0.24])

Fig. 12.1: The effect of the distance threshold $d$ on the number of classes and the size of the class.

Next, we discuss the choice of the similarity matrix parameter $\sigma$. Since the input parameters are artificially set, there is a considerable amount of uncertainty and instability. The NJW algorithm [9] is used to select the best $\sigma$ of the clustering results as parameters by repeatedly running the NJW algorithm. Despite the elimination of human input, it is still a considerable time cost. At present, many scholars are studying the selection of the parameters of $\sigma$, which are usually determined by experience. A uniform standard has not been formed, and the selection standards cannot be given quantitatively. They are limited in the scope of their respective fields of knowledge.

According to the flexibility of parameter selection, researchers have been trying to determine the parameter $\sigma$ automatically according to the situation of the data set itself. In 2004, Zelnik-Manor et al. proposed a self-training (self-tuning) algorithm [18]. According to the geometric characteristics of each data point, the ST algorithm computes an adaptive parameter $\sigma_i = \|x_i - x_p\|$ for each data point $x_i$ by neighbourhood information ($x_p$ is the $k$th nearest neighbour of point $x_i$). Based on this idea, the similarity matrix is transformed into

```
$$ W_{ij} = \exp\left(-\frac{\|x_i - x_j\|^2}{\sigma_i\sigma_j}\right) \quad (12.2) $$
```

Similarly, Fisher et al. proposed a method for dynamically selecting the parameter $\sigma$ in 2005 [19]. By solving $\sum_{j=1}^n \exp(-\|x_i - x_j\|^2/2\sigma_i^2) = \tau$, where $\tau$ is a constant, a parameter $\sigma_i$ is determined for each data point $x_i$. Here, the similarity matrix is defined as

```
$$ W_{ij} = \min \left\{ \exp\left(-\frac{\|x_i - x_j\|^2}{2\sigma_i^2}\right), \exp\left(-\frac{\|x_i - x_j\|^2}{2\sigma_j^2}\right) \right\} \quad (12.3) $$
```

In summary, constructing a similar matrix depends on choosing not only the appropriate similarity measure but also the parameter $\sigma$ that suits its own data set. This will become a hot and complex research topic in future spectral estimation learning methods.