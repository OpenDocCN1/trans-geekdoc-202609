
## 11.4.4 Training Issues

During training, we need to iteratively update three parameters: the weight `w`, the hyperparameter `α`, and the kernel parameter vector `η`. One way to update these parameters is to optimize over `w|α` and `η` simultaneously. This allows us to find the optimal solution, but will be computationally intensive. Another way to do it is to interleave the update of `w`/`α` and `η`. For each (`w`,), we search a few steps for `Δη` based on the gradient of the log-likelihood, and update `η` by adding `τ · Δη` to it, where `τ` > 0 is the momentum. This approach may not lead to the desired solution, but is more efficient. In this chapter, we follow the local update approach. We train multiple adversarial RVM models, and select `M` models that satisfy `u`[+] < `ρ` · `u`[−], where `u`[+] denotes the uncertainty of predicting a positive training instance, and `u`[−] the uncertainty of predicting a negative training instance, and `ρ` ∈ (0, 1] is a positive constant. The smaller the ratio

```
ρ = u₊ / u₋,
```

the farther away the decision boundary from the positive training examples. That is, while the number of classifiers in the ensemble is less than `M`, train an adversarial RVM classifier `h`[i] by learning `w`/`α` and `η`; then add `h`[i] to the ensemble if

```
u₊ < ρ · u₋
```

The uncertainties `u`[+] and `u`[−] are estimated on the positive and negative training data as follows:

```
u₊ = (Σᵢ yᵢ · (1 - h(xᵢ; w))) / Σᵢ yᵢ          (11.4)
```

```
u₋ = (Σᵢ (1 - yᵢ) · h(xᵢ; w)) / Σᵢ (1 - yᵢ)    (11.5)
```

where

```
Σᵢ yᵢ
```

is the total number of positive training instances, and

```
Σᵢ (1 - yᵢ)
```

is the number of negative training instances. We select `M` such models and combine them to make the final predictions through majority vote.

### 11.4.5 Adversarial RVM Learning Algorithm

We now present the algorithm of adversarial RVM learning, namely `AD-RVM`. Given a set of training data, we first initialize the value of `α` and use it to update the weight vector `w`; next, we update the kernel parameter vector `η` with the given `w` and `α`; finally we update the hyperparameter `α`. The process iterates for a pre-defined maximum number of rounds. We train multiple such classifiers and select `M` classifiers that satisfy `ρ u`[+] < `u`[−] to form an ensemble. The detailed algorithm is given in [Algorithm 11.1](#ch11.xhtml#alg11_1).

## 11.5 Experimental Results

### 11.5.1 Datasets

We used one artificial dataset and two real datasets in our experiments. We model the attacks at classification time by moving positive test instances closer to randomly selected negative instances plus local random noise. Attacks on the test data are designed to challenge all the learning models at increasingly more difficult levels. The difficulty is controlled using the attack factor `f`[attack]. More specifically,

```
xᵢⱼ⁺ = xᵢⱼ⁺ + f[attack] · (xᵢⱼ⁻ - xᵢⱼ⁺) + ε    (11.6)
```

where `ε` is local random noise. Notice `f`[attack] = 1 models the worst case attacks where a positive data point is arbitrarily close to a negative one within the range of the random local noise. [Figure 11.3](#ch11.xhtml#fig11_3a) illustrates the attack with `f`[attack] = 0.3.

![Figure 11.3 Attack factor = 0.3. White dots: negative data, black dots: positive data before attacks, black “+”: positive data after attacks.](images/fig11_3.jpg)

[Figure 11.3 Attack factor = 0.3. White dots: negative data, black dots: positive data before attacks, black “+”: positive data after attacks.](#ch11.xhtml#Ffig11_3)

We compare four learning models: `AD-RVM`, `RVM`, `SVM`, and `One-class SVM` on the three datasets. All results reported are averaged over 10 random runs.

### 11.5.2 Experiments on the Artificial Dataset

The synthetic dataset is generated from a bivariate normal distribution with specified means (−5.0, −6.0) and (5.0, 6.0), and covariance matrix

```
( 1.0  0.5 )
( 0.5  2.0 )
```

We first consider the cases where the training data is clean and only the test data has been corrupted. Attacks on the test data are created using Equation (11.6). [Table 11.1](#ch11.xhtml#table11_1a) shows the classification performance on this set of data in terms of error rates. The `ρ` value which controls the uncertainty of predicting positive and negative data is chosen as 0.67. We discuss the impact of `ρ` later.

**Table 11.1** Classification errors of `AD-RVM`, `RVM`, `SVM`, and `1-CLASS SVM` on synthetic data. Best results are bolded.

| | `f`[attack] |
|---|---|---|---|---|---|
| | 0.1 | 0.3 | 0.5 | 0.7 | 0.9 |
| `AD-RVM` | **0.0025** | **0.0175** | **0.1435** | **0.3205** | **0.4500** |
| `RVM` | 0.0100 | 0.0810 | 0.2542 | 0.4305 | 0.5000 |
| `SVM` | 0.0105 | 0.0705 | 0.2500 | 0.4355 | 0.4910 |
| `1-class SVM` | 0.0059 | 0.1310 | 0.5000 | 0.5000 | 0.5000 |
