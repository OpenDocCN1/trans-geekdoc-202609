
For example, in the task of income level prediction (i.e., Adult dataset [\[9\]](#Chp008_143-160_B9780443190377000168.xhtml#br0045)), a model is trained to predict if a person has high or low income (i.e., binary classification) based on 14 features characterizing personal information (e.g., age, sex, education, occupation, etc.). We define the age from 30 to 50 as high-income age since most people with high income lie within this age interval. Assume that sex is the sensitive attribute to protect. Additionally, assume that in client `m` the percentage of populations with high-income age is similar between males and females while in client `m'` the percentage of populations with high-income age is higher in males than that of females. A simple model that makes predictions based solely on the attribute age will probably achieve fairness in client `m` (i.e., predicting 1 with the same probability between male group than female group). However, the model can hardly achieve fairness in client `m'` since it will predict 1 with a higher probability on the male group due to its higher percentage of high-income age populations. Another problem is that the protected attribute can vary across clients. For example, the sensitive attribute in the dataset of client `m` is sex while it is race in that of client `m'`. It is not clear how enforcing global fairness with respect to some unified sensitive attributes can be useful to each client in these scenarios. Therefore, a more refined algorithmic fairness notion with performance disparity defined with respect to each client is needed. Define a unique sensitive attribute for each client `m`: `c[m] ∈ {0, 1}` which can be the same across different clients. Denote `D[m]^((ij)) = {(x, y, c[m]) : (x, y, c[m]) ∈ D[m], ŷ[w] = i, c[m] = j}` and `D[m]^((·j)) = {(x, y, c[m]) : (x, y, c[m]) ∈ D[m], ŷ[w] ∈ {0, 1}, c[m] = j}`. It leads to

## Definition 8.8

### Multi-client algorithmic fairness [\[1\]](#Chp008_143-160_B9780443190377000168.xhtml#br0005)

In a federated learning (FL) system, a model `f(w, ·)` achieves `{ε[m], m ∈ {1, …, n}}` multi-client algorithmic fairness if

```
ΔDP_m(w) = | |D_m^(11)| / |D_m^(·1)| - |D_m^(10)| / |D_m^(·0)| | ≤ ε_m  ∀ m ∈ { 1,…,n } .
```

Here `ΔDP[m](w)` is the absolute difference of the probability of samples predicted as positive with model `w` between two groups on the local dataset of client `m`.

The multi-client algorithmic fairness requires low performance disparity with respect to each client `m` with a possibly unique sensitive attribute `c[m]` and an individual budget `ε[m]` for the performance disparity in each client. As illustrated in the income level prediction example, achieving fairness in the local dataset of different clients can sometimes conflict with each other. Therefore, it is more challenging to achieve multi-client algorithmic fairness than global algorithmic fairness even if `∑_{m = 1}^{n} ε_m = ε`.

## 8.3 Algorithms to achieve fairness in FL

### 8.3.1 Algorithms to achieve equitable fairness

We will focus on discussing the details of the AFL [\[17\]](#Chp008_143-160_B9780443190377000168.xhtml#br0085) and q-FFL [\[12\]](#Chp008_143-160_B9780443190377000168.xhtml#br0060) algorithms to achieve good-intent equitable fairness and performance equitable fairness correspondingly here and refer readers to [\[2\]](#Chp008_143-160_B9780443190377000168.xhtml#br0010) for an in-depth discussion on the algorithm to achieve Pareto-optimal equitable fairness.

A common approach to equitable fairness is to modify the global objective of the training to achieve similar model performances on the clients' local data. AFL [\[17\]](#Chp008_143-160_B9780443190377000168.xhtml#br0085) proposes a min–max objective. Defining `Δ^(n)` as an `(n − 1)`-dimensional probability simplex and considering `λ ∈ Δ^(n)`, the objective function is defined as `g(w, λ) = ∑_{m = 1}^{n} λ_m g_m(w)` where `g_m(w)` is the local training loss of model parameterized by `w ∈ W` on client `m`. The objective of the AFL is defined as

```
min_{w ∈ W} max_{λ ∈ Δ^n} g(w, λ) .
```
