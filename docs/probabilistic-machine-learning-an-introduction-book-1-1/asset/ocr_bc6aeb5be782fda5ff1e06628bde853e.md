with equality iff X and Y are independent. This shows that, on average, conditioning on data never increases one’s uncertainty. The caveat “on average” is necessary because for any particular observation (value of X), one may get more “confused” (i.e., 𝔍(Y|x) > 𝔍(Y)). However, in expectation, looking at the data is a good thing to do. (See also Sec. 6.3.7.)

We can rewrite Eq. (6.14) as follows:

𝔍(X₁, X₂) = 𝔍(X₁) + 𝔍(X₂|X₁)  (6.16)

This can be generalized to get the **chain rule for entropy**:

𝔍(X₁, X₂, …, Xₙ) = Σᵢ₌₁ⁿ 𝔍(Xᵢ|X₁, …, Xᵢ₋₁)  (6.17)

# 6.1.5 Perplexity

The **perplexity** of a discrete probability distribution p is defined as

perplexity(p) ≜ 2^{𝔍(p)}  (6.18)

This is often interpreted as a measure of predictability. For example, suppose p is a uniform distribution over K states. In this case, the perplexity is K. Obviously the lower bound on perplexity is 2⁰ = 1, which will be achieved if the distribution can perfectly predict outcomes.

Now suppose we have an empirical distribution based on data 𝒟:

p_D(x|𝒟) = 1/N Σₙ₌₁^N δ_{xₙ}(x)  (6.19)

We can measure how well p predicts 𝒟 by computing

perplexity(p_D, p) ≜ 2^{𝔍(p_D, p)}  (6.20)

Perplexity is often used to evaluate the quality of statistical language models, which is a generative model for sequences of tokens. Suppose the data is a single long document x of length N, and suppose p is a simple unigram model. In this case, the cross entropy term is given by

H = -1/N Σₙ₌₁^N log p(xₙ)  (6.21)

and hence the perplexity is given by

perplexity(p_D, p) = 2^H = √[N]{∏ₙ₌₁^N 1/p(xₙ)}  (6.22)

This is sometimes called the **exponentiated cross entropy**. We see that this is the geometric mean of the inverse predictive probabilities.