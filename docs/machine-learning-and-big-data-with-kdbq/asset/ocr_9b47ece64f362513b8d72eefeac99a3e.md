# Neural Networks

# 457

8.10451e-008 0.0133227 0.986677 0 1
3.073432e-005 0.6700523 0.3299169 0 1
0.9973873 0.002612676 1.243462e-009 1 0
0.9973153 0.002684707 1.280416e-009 1 0

It is worth noting that 5th and 9th row represent a case where the model does not work. In the cases where the model works, the probability for a correct class is usually close to 1, while in the confused case, the probabilities are instead distributed across classes. This fact can be further utilised in interpreting and adding some measure of uncertainty for every prediction.

# 22.3.3 Regression

The third example is to regress, where the dependent variable is a real-valued array. We have mentioned in the introductory part that by suitable choice of the neural network parameters, we can turn the network into a dimensionality reduction tool. We explore this situation in our example as it provides both a handy and practical tool.

In particular, we select the case of four real-valued features. Each feature is constructed as a linear combination of a common factor and an idiosyncratic noise:

$x_i = c_i \cdot \phi + \sqrt{1 - \alpha_i^2} \cdot e_i$ with $i = 1, \dots, 4,$

where $\alpha_i$, is a parameter within $[0, 1]$, $e_i$ is an idiosyncratic noise, and $\phi$ is a factor across different features. The factor and the idiosyncratic noise have the same variance thus all the features have the same variance as.

We employ the uniform distribution to define factor and idiosyncratic noise variables:

```
factor:neg[1]+2*500?1;
tmp1:neg[1]+2*500?1;
tmp2:neg[1]+2*500?1;
tmp3:neg[1]+2*500?1;
tmp4:neg[1]+2*500?1;
```

The features are defined as linear combinations defined in eq. (22.24) with corresponding coefficients:

```
c1:0.2;
c2:0.4;
c3:0.6;
c4:0.0;
cX1:(c1*factor)+sqrt[1-c1*c1]+tmpC1;
cX2:(c2*factor)+sqrt[1-c2*c2]+tmpC2;
cX3:(c3*factor)+sqrt[1-c3*c3]+tmpC3;
cX4:(c4*factor)+sqrt[1-c4*c4]+tmpC4;
```

The last factor is not correlated to the common factor. Let us confirm that the correlation between factor and the features reflects the corresponding factors:

```
cor[cX1; factor];
```