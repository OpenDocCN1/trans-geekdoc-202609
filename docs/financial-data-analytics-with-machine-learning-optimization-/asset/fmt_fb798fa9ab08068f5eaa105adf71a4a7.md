
# A Bayesian Approach to Parameter Estimation

A Bayesian approach to the estimation of parameters is a probabilistic method in which an optimal decision rule is taken, in contrast to the usual maximum likelihood estimation (MLE) method. Compared with MLE, whose resulting `θ̂` maximizes the probability of obtaining the given sample of training dataset, the Bayesian approach evaluates the conditional probability of `θ` given the sample taking various values instead; see [Figure 1.1](#c01.xhtml#c01-fig-0001) for an illustration of the comparison. Indeed, for `Bayesian inference`, the training stage updates our prior belief on the probabilities of `θ` using the input data, resulting in posterior probabilities as shown in [Figure 1.1](#c01.xhtml#c01-fig-0001)b.

The theoretical foundation of Bayesian inference is based on an extended form of `Bayes' theorem`: Let `A₁, …, Aₙ` be mutually exclusive events and `∪ᵢ₌₁ⁿ Aᵢ = A`. Then, for any event `B ⊆ A`, we have

(1.10) `P(A₍ⱼ₁,…,ⱼₖ₎ | B) = P(B | A₍ⱼ₁,…,ⱼₖ₎) P(A₍ⱼ₁,…,ⱼₖ₎) / Σᵢ₌₁ⁿ P(B | Aᵢ) P(Aᵢ) = Σᵅ₌₁ᵏ P(B | Aⱼₐ) P(Aⱼₐ) / Σᵢ₌₁ⁿ P(B | Aᵢ) P(Aᵢ)`

where `A₍ⱼ₁,…,ⱼₖ₎ = ∪ᵅ₌₁ᵏ Aⱼₐ`.

## Example 1.2

John undertook a diagnostic test for heart disease. It is known that 1% of the whole population suffers from the disease. Suppose that 95% of patients (having disease) would be diagnosed by the test as positive, i.e., the accuracy of the test is 95%. On the other hand, 95% of healthy individuals would be correctly diagnosed as negative. Unfortunately, John's test result was positive.

Let `A` be the event of John having heart disease and `B` be the event of having a positive test result. Then we have:
