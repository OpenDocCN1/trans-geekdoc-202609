

Equation (A.4) helps us calculate the often-appearing expectation 𝔼[*x*]\[*x*^(*n*) ⋅ *e*^(*x*)\]. In fact, 𝔼[*x*]\[*e*^(*x*)\] and 𝔼[*x*]\[*x* ⋅ *e*^(*x*)\] are very common in several areas of Applied Mathematics. Again, note that this holds true for any distribution for *x*.

The MGF should be thought of as an alternative specification of a random variable (alternative to specifying its Probability Distribution). This alternative specification is very valuable because it can sometimes provide better analytical tractability than working with the Probability Density Function or Cumulative Distribution Function (as an example, see the below section on the MGF for linear functions of independent random variables).

## A.2 MGF FOR LINEAR FUNCTIONS OF RANDOM VARIABLES

Consider *m* independent random variables *x*[1], *x*[2], …, *x*[*m*]. Let *α*[0], *α*[1], …, *α*[*m*] ∈ ℝ. Now consider the random variable

```
x = α₀ + Σ(αᵢ * xᵢ)
```

The Probability Density Function of *x* is complicated to calculate as it involves convolutions. However, observe that the MGF *f*[*x*] of *x* is given by:

```
fₓ(t) = E[e^(t(α₀ + Σ(αᵢ * xᵢ)))] = e^(α₀t) · Π(E[e^(tαᵢxᵢ)]) = e^(α₀t) · Π(f_{αᵢxᵢ})(t) = e^(α₀t) · Π(f_{xᵢ})(αᵢt)
```

This means the MGF of *x* can be calculated as *e*^(α₀*t*) times the product of the MGFs of *αᵢxᵢ* (or of *αᵢ*-scaled MGFs of *xᵢ*) for all *i* = 1, 2, …, *m*. This gives us a much better way to analytically tract the probability distribution of *x* (compared to the convolution approach).

## A.3 MGF FOR THE NORMAL DISTRIBUTION

Here we assume that the random variables *x* follows a normal distribution. Let *x* ∼ 𝒩(*μ*, *σ*²).

```
f_{x~N(μ,σ²)}(t) = E_{x~N(μ,σ²)}[e^(tx)]
                = ∫(1/(√(2π)σ)) · e^(-(x-μ)²/(2σ²)) · e^(tx) · dx
                = ∫(1/(√(2π)σ)) · e^(-(x-(μ+tσ²))²/(2σ²)) · e^(μt + σ²t²/2) · dx
                = e^(μt + σ²t²/2) · E_{x~N(μ+tσ²,σ²)}[1]
                = e^(μt + σ²t²/2)
```

(A.5)

```
f'_{x~N(μ,σ²)}(t) = E_{x~N(μ,σ²)}[x · e^(tx)] = (μ + σ²t) · e^(μt + σ²t²/2)
```

(A.6)

```
f''_{x~N(μ,σ²)}(t) = E_{x~N(μ,σ²)}[x² · e^(tx)] = ((μ + σ²t)² + σ²) · e^(μt + σ²t²/2)
```

(A.7)

```
f'_{x~N(μ,σ²)}(0) = E_{x~N(μ,σ²)}[x] = μ
```

```
f''_{x~N(μ,σ²)}(0) = E_{x~N(μ,σ²)}[x²] = μ² + σ²
```

```
f'_{x~N(μ,σ²)}(1) = E_{x~N(μ,σ²)}[x · e^x] = (μ + σ²)e^(μ + σ²/2)
```

```
f''_{x~N(μ,σ²)}(1) = E_{x~N(μ,σ²)}[x² · e^x] = ((μ + σ²)² + σ²)e^(μ + σ²/2)
```

## A.4 MINIMIZING THE MGF

Now let us consider the problem of minimizing the MGF. The problem is to:

```
min_{t∈ℝ} fₓ(t) = min_{t∈ℝ} Eₓ[e^(tx)]
```

This problem of minimizing 𝔼[*x*]\[*e*^(*t**x*)\] shows up a lot in various places in Applied Mathematics when dealing with exponential functions (e.g., when optimizing the Expectation of a Constant Absolute Risk-Aversion (CARA) Utility function $U(y) = (1 - e^(-γy))/γ$ where *γ* is the coefficient of risk-aversion and where *y* is a parameterized function of a random variable *x*).

Let us denote *t*^(\*) as the value of *t* that minimizes the MGF. Specifically,

```
t* = arg min_{t∈ℝ} fₓ(t) = arg min_{t∈ℝ} Eₓ[e^(tx)]
```

### A.4.1 Minimizing the MGF When x Follows a Normal Distribution

Here we consider the fairly typical case where *x* follows a normal distribution. Let *x* ∼ 𝒩(*μ*, *σ*²). Then we have to solve the problem:

```
min_{t∈ℝ} f_{x~N(μ,σ²)}(t) = min_{t∈ℝ} E_{x~N(μ,σ²)}[e^(tx)] = min_{t∈ℝ} e^(μt + σ²t²/2)
```

From Equation (A.6) above, we have:

```
f'_{x~N(μ,σ²)}(t) = (μ + σ²t) · e^(μt + σ²t²/2)
```

Setting this to 0 yields:

```
(μ + σ²t*) · e^(μt* + σ²t*²/2) = 0
```

which leads to:

```
t* = -μ/σ²
```

(A.8)

From Equation (A.7) above, we have:

```
f''_{x~N(μ,σ²)}(t) = ((μ + σ²t)² + σ²) · e^(μt + σ²t²/2) > 0 for all t ∈ ℝ
```

which confirms that *t*^(\*) is a minima.

Substituting *t* = *t*^(\*) in $f_{x~N(μ,σ²)}(t) = e^(μt + σ²t²/2)$ yields:

```
min_{t∈ℝ} f_{x~N(μ,σ²)}(t) = e^(μt* + σ²t*²/2) = e^(-μ²/(2σ²))
```

(A.9)

### A.4.2 Minimizing the MGF When x Follows a Symmetric Binary Distribution

Here we consider the case where *x* follows a binary distribution: *x* takes values *μ* + *σ* and *μ* − *σ* with probability 0.5 each. Let us refer to this distribution as *x* ∼ ℬ(*μ* + *σ*, *μ* − *σ*). Note that the mean and variance of *x* under ℬ(*μ* + *σ*, *μ* − *σ*) are *μ* and *σ*², respectively. So we have to solve the problem:

```
min_{t∈ℝ} f_{x~B(μ+σ,μ-σ)}(t) = min_{t∈ℝ} E_{x~B(μ+σ,μ-σ)}[e^(tx)] = min_{t∈ℝ} 0.5(e^((μ+σ)t) + e^((μ-σ)t))
```

```
f'_{x~B(μ+σ,μ-σ)}(t) = 0.5((μ + σ) · e^((μ+σ)t) + (μ - σ) · e^((μ-σ)t))
```

