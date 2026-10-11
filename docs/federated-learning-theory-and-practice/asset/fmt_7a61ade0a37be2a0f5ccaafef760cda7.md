
## 2. Group privacy

Group privacy implies that the DP will degrade gracefully with the size of the group.

### Theorem 3.2: Group privacy [[6]](#Chp003_57-74_B9780443190377000119.xhtml#br0030)

Let `𝒜 : 𝒳 → ℝ` be `(ϵ, δ)`-DP, then `𝒜` is also `(kϵ, k e^((k−1)ϵ) δ)`-DP for groups of size k.

## 3. Composition

Composition implies that multiple DP mechanisms can be combined to construct more advanced DP mechanisms.

### Theorem 3.3: Composition [[6]](#Chp003_57-74_B9780443190377000119.xhtml#br0030)

Let `𝒜[i]` for `i ∈ [k]` be `(ϵ[i], δ[i])`-DP mechanisms, then the composition `𝒜` of all `𝒜[i]`s defined as `𝒜(x) = (𝒜[1](x), …, 𝒜[k](x))`, is `(∑_{i=1}^k ϵ_i, ∑_{i=1}^k δ_i)`-DP.

Theorem 3.3 states that if we have `k` mechanisms, each guaranteeing `(ϵ/k, δ/k)`-DP, then the overall mechanism will guarantee `(ϵ, δ)`-DP. We note that the result of this composition can be improved from `O(ϵ/k)` to `O(ϵ/√k)` to achieve better dependence on `k` [[7]](#Chp003_57-74_B9780443190377000119.xhtml#br0035).

These properties of DP are crucial for the development and analyses of more advanced DP mechanisms including DP-guaranteeing algorithms for FL. In the next section, we discuss algorithms for both sample and client-level DP with their associated performance guarantees.

## 3.3 DP guaranteed algorithms

In this section, we will discuss FedAvg and other FL algorithms for obtaining some form of DP. First, we discuss the standard procedure to obtain DP in a centralized setting for a vanilla SGD algorithm. Later in the chapter, similar ideas will be utilized to develop DP algorithms for FL.

The usual mechanism to endow any algorithm with DP guarantees is by first employing a clipping operation on the output of the algorithm, such as parameters and gradients, and then adding a carefully calibrated perturbation. One can customize the centralized SGD to provide DP guarantees by adding clipping and perturbation to the gradients. Moreover, the adjacent datasets in the centralized setting are defined as two datasets differing by only a single sample (see sample-level DP in Definition 3.2), thereby ensuring privacy for each sample. The differentially private SGD with gradient clipping (referred to as DP-SGD) with tight DP guarantees is proposed in [[1]](#Chp003_57-74_B9780443190377000119.xhtml#br0005); see Algorithm 2 for detailed steps. Specifically, at each iteration `t`, the algorithm samples a random sample `ℬ^(t)` of size `B` and computes the stochastic gradients `g̃^(t,i)` for each `i ∈ ℬ^(t)`. Then per-sample gradient is clipped using the gradient clipping operation (3.3).

![Algorithm 2 Differentially private SGD [DP-SGD].](OEBPS/images/B9780443190377000119/gr002.jpg)

Algorithm 2 Differentially private SGD [DP-SGD].

### Gradient clipping [[1]](#Chp003_57-74_B9780443190377000119.xhtml#br0005)

The (per-sample) gradient `g̃[m]^(t,i)` is clipped at each step (see Algorithm 2, line 5) as

```
clip(g̃^(t,i), C) = g̃^(t,i) / max(1, ||g̃^(t,i)||_2 / C)
```

(3.3)

with `C > 0` being a constant. This per-sample clipping ensures that when `||g̃^(t,i)||_2 ≤ C`, we keep `g̃^(t,i)` unchanged; otherwise we scale the gradient so that `||g̃^(t,i)||_2 = C`. The clipping operation is a key step that ensures bounded sensitivity in output when changing training samples and allows one to obtain provable DP guarantees, where the sensitivity refers to the maximum change in the size of the output when a single data point is changed. After the clipping operation, we add a carefully calibrated noise to the individual stochastic gradients in line 6, and average the resulting quantities to update the model in line 7. The next result states the precise DP guarantees for DP-SGD (Algorithm 2).

### Theorem 3.4: DP-SGD [[1]](#Chp003_57-74_B9780443190377000119.xhtml#br0005)

There exist constants `c[1]` and `c[2]` so that, given the sampling probability `q = B/|𝒟|` and the number of steps `τ`, for any `ε < c[1] ⋅ q² ⋅ τ`, Algorithm 2 is `(ε, δ)`-differentially private for any `δ > 0`, if we choose

```
σ ≥ c_2 (C ⋅ q √(τ ⋅ log(1/δ))) / ε
```

where `|D|` is the total number of samples.

The proof of Theorem 3.4 follows the standard approach of approximating the final output of the algorithm by a sequential composition of bounded-norm stochastic gradients and designing the noise variance to guarantee DP. In fact, [[1]](#Chp003_57-74_B9780443190377000119.xhtml#br0005) provides a tighter DP guarantee compared to the simple application of the composition theorem (Theorem 3.3) by utilizing the information of the injected noise distribution. Specifically, the proof in [[1]](#Chp003_57-74_B9780443190377000119.xhtml#br0005) utilizes a moments accountant technique where the bounds on moments of the privacy loss random variable are tracked throughout the execution of the algorithm. These moment bounds are then used to find the tail bounds of the differential privacy random variable, thereby guaranteeing DP.

Next, we discuss how to extend DP-SGD to FL models.

### 3.3.1 Sample-level DP
