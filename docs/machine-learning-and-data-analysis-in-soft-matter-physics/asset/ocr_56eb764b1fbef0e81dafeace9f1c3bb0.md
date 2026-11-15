transform samples from an easy-to-sample probability distribution, such as Gaussian noise, into realistic samples of the objects of interest. These methods have been used to draw photorealistic images, generate speech or music audio, and generate chemical structures to design molecules or materials with certain properties. If the aim is to learn a probability distribution from sampling data (density estimation) or to learn to efficiently sample from a given probability distribution, one typically faces the challenge of matching the probability distribution of the trained model with a reference Matching probability distributions can be achieved by minimizing probability distances. The most commonly used probability distance is the Kullback–Leibler (KL) divergence, also called relative entropy between two distributions q and p:

```
KL(q || p) = \int q(x) [log q(x) - log p(x)] dx. (16)
```

In Boltzmann generation, aim to efficiently sample the equilibrium distribution \mu(x) of a many-body system defined by its energy function u(x) (Equation 1).We can learn the parameters \theta of a neural network that generates samples from the distribution p_X(x; \theta) by making its generated distribution similar to the target equilibrium distribution. Choosing q \equiv p_X(x) and p \equiv \mu(x) in Equation 16, we can minimize the KL\theta [q X || \mu X] with the energy loss (EL):

```
EL = E_{x ~ p_X(x; \theta)} [log p_X(x; \theta) + u(x)] (17)
```

As the network samples from an energy surface u(x; \theta) = - log p_X(x; \theta) + const (Equation 1), this loss is performing energy matching. In order to evaluate the loss (Equation 17), we need not only to be able to generate samples x ~ p_X(x; \theta) from the network but also to be able to compute p_X(x; \theta) for every sample x. The reverse case is density estimation. Suppose we have simulation data x, and we want to train the probability distribution p_X(x; \theta) to resemble the data distribution. We choose q(x) as the data distribution and p \equiv p_X(x; \theta) in Equation 16 and exploit that Ex~data [log q(x)] is a constant that does not depend on the parameters \theta. Then we can minimize the loss:

```
NL = -E_{x ~ data} [log p_X(x; \theta)]. (18)
```

This loss is the negative likelihood (NL) that the model generates the observed sample; hence, minimizing it corresponds to a maximum likelihood approach. Likelihood maximization is abundantly used in ML.