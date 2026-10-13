
*   **L₀**: This term can be interpreted as a reconstruction term that predicts the log-probability of the original data samples given the first-step latent variables. The term plays the same role as the corresponding one in the VAE in Eq. [(19.22)](#Chp019_997-1102_B9780443292385000251.xhtml#deq47). Due to the Gaussian nature of the conditionals, this component can also be computed in closed form. For the case of Eq. [(19.69)](#Chp019_997-1102_B9780443292385000251.xhtml#deq143), it is straightforward to see that minimizing **L₀** is equivalent with forcing **μ_θ(x₁, 1)** to be close, in the Euclidean norm sense, to **x₀**.

The cost function results by averaging over all the observations, i.e., **𝔼[x₀ ∼ q(x₀)][L[x₀]]**, which in practice is obtained by taking the sample mean over all the observed input examples.

### A simplified model

The model simplification that was introduced before, i.e., **Σ_θ(x[t], t) = σ[t]²I**, was further exploited in [85]. There are different possible choices for the sequence **σ[t]²**. One possibility is to set **σ[t]² = β[t]** that makes the covariance matrices involved in the reverse path to be equal to those involved in the forward process. This assumption leads to Eq. [(19.70)](#Chp019_997-1102_B9780443292385000251.xhtml#deq144), and the training is simplified to adjust the output of the neural network at time step *t*, **μ_θ(x[t], t)**, to predict **μ̃_t(x_t, x_0)**. Let us now elaborate a bit more on Eq. [(19.70)](#Chp019_997-1102_B9780443292385000251.xhtml#deq144).

Combining Eqs. [(19.59)](#Chp019_997-1102_B9780443292385000251.xhtml#deq135) and [(19.66)](#Chp019_997-1102_B9780443292385000251.xhtml#deq140) and after a bit of algebra ([Problem 19.8](#Chp019_997-1102_B9780443292385000251.xhtml#o0080)), one obtains that

```
μ̃_t(x_t, x_0) = (1/√a_t) (x_t - (β_t/√(1 - ā_t)) ε)
```
