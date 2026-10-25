likelihood, the total probability of the evidence under all possible hypotheses.

# Components of Bayesian Inference

+   1. Prior Distribution: Represents our initial beliefs about the parameter before observing any data. Priors can be informative (based on previous knowledge) or non-informative (vague or flat priors).
+   
+   2. Likelihood: Reflects the probability of the observed data under different parameter values. It quantifies how well the data supports various hypotheses.
+   
+   3. Posterior Distribution: Combines the prior and likelihood to form an updated belief distribution after observing the data. This is the crux of Bayesian inference, where we derive the probability of different hypotheses given the evidence.

# Constructing Bayesian Models

Constructing a Bayesian model involves specifying the prior distribution, the likelihood function, and then using Bayes' theorem to obtain the posterior distribution. Let's consider a simple example of estimating the probability of success in a binomial experiment using Rust:

```
```rust use rand_distr::{Distribution, Beta};

fn bayesian_update(prior_alpha: f64, prior_beta: f64, successes: u32, trials: u32) -
> (f64, f64) {
    let posterior_alpha = prior_alpha + successes as f64;
    let posterior_beta = prior_beta + (trials - successes) as f64;

    (posterior_alpha, posterior_beta)
}
```