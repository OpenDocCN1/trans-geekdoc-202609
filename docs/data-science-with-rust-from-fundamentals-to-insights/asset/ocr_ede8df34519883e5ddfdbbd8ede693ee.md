# # Probability Distributions

Probability distributions describe how the values of a random variable are distributed. They can be either discrete or continuous.

# ## Discrete Probability Distributions

+   1. **Binomial Distribution**: Represents the number of successes in a fixed number of independent Bernoulli trials (e.g., flipping a coin 10 times). The probability mass function (PMF) is given by: [ P(X = k) = \binom{n}{k} p^k (1-p)^{n-k} ] where ( n ) is the number of trials, ( k ) is the number of successes, and ( p ) is the probability of success.

```
```rust
use rand_distr::{Binomial, Distribution};

fn binomial_distribution() {
    let binomial = Binomial::new(10, 0.5).unwrap(); // 10 trials, 50% success
    probability
    let successes: u64 = binomial.sample(&mut rand::thread_rng());
    println!("Number of successes in 10 trials: {}", successes);
}

fn main() {
    binomial_distribution();
}
```
```

+   1. **Poisson Distribution**: Models the number of events occurring within a fixed interval of time or space. The PMF is: [ P(X = k) = \frac{\lambda^k e^{-\lambda}}{k!} ] where ( \lambda ) is the average number of events.

```
```rust
use rand_distr::{Poisson, Distribution};

fn poisson_distribution() {
    let poisson = Poisson::new(5.0).unwrap(); // Average of 5 events
```
```