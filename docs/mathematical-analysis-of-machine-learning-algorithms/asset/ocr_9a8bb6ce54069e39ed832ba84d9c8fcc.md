# ### 13.1 Martingale Exponential Inequalities

Using the technique of logarithmic moment generating functions, we can obtain martingale inequalities similar to those of Chapter 2.

**Lemma 13.1**  *Consider a sequence of real-valued random (measurable) functions ξ₁(S₁), …, ξₜ(Sₜ). Let τ ≤ T be a stopping time so that 1(t ≤ τ) is measurable in Sₜ. We have*

$$E_{S_T}\exp\left(\sum_{i=1}^{\tau}ξ_i-\sum_{i=1}^{\tau}\ln E_{Z_i^{(y)}}e^{ξ_i}\right)=1.$$

*Proof.* We prove the lemma by induction on T. When T = 0, the equality is trivial. Assume that the claim holds at T − 1 for some T ≥ 1. Now we will prove the equation at time T using the induction hypothesis.

Note that ξ̃ᵢ = ξᵢ1(i ≤ τ) is measurable in Sᵢ. We have

$$\sum_{i=1}^{\tau}ξ_i-\sum_{i=1}^{\tau}\ln E_{Z_i^{(y)}}e^{ξ_i}=\sum_{i=1}^{T}ξ̃_i-\sum_{i=1}^{T}\ln E_{Z_i^{(y)}}e^{ξ̃_i}.$$

It follows that

$$E_{Z_1,\ldots,Z_T}\exp\left(\sum_{i=1}^{\tau}ξ_i-\sum_{i=1}^{\tau}\ln E_{Z_i^{(y)}}e^{ξ_i}\right)$$
$$=E_{Z_1,\ldots,Z_T}\exp\left(\sum_{i=1}^{T}ξ̃_i-\sum_{i=1}^{T}\ln E_{Z_i^{(y)}}e^{ξ̃_i}\right)$$
$$=E_{Z_1,\ldots,Z_{n-1},Z_T^{(y)}}\exp\left(\sum_{i=1}^{T-1}ξ̃_i-\sum_{i=1}^{T-1}\ln E_{Z_i^{(y)}}e^{ξ̃_i}\right)E_{Z_T^{(y)}}\exp\left(ξ̃_T-\ln E_{Z_T^{(y)}}e^{ξ̃_T}\right)=1$$
$$=E_{Z_1,\ldots,Z_{T-1}}\exp\left(\sum_{i=1}^{T-1}ξ̃_i-\sum_{i=1}^{T-1}\ln E_{Z_i^{(y)}}e^{ξ̃_i}\right)$$
$$=E_{Z_1,\ldots,Z_{T-1}}\exp\left(\sum_{i=1}^{\min(τ,T-1)}ξ_i-\sum_{i=1}^{\min(τ,T-1)}\ln E_{Z_i^{(y)}}e^{ξ_i}\right)=1.$$

Note that the last equation follows from the induction hypothesis, and the fact that min(τ, T − 1) is a stopping time ≤ T − 1.

The following result is a direct consequence of Lemma 13.1, which generalizes Theorem 2.5 for sum of independent variables to martingales.

**Theorem 13.2**  *Consider a sequence of random functions ξ₁(S₁), …, ξₜ(Sₜ), …, with filtration {Fₜ}. We have for any δ ∈ (0, 1) and λ > 0,*

$$\Pr\left[\exists n>0:-\sum_{i=1}^{n}ξ_i\ge\frac{\ln(1/δ)}{λ}+\frac{1}{λ}\sum_{i=1}^{n}\ln E_{Z_i^{(y)}}e^{-λξ_i}\right]\le δ.$$