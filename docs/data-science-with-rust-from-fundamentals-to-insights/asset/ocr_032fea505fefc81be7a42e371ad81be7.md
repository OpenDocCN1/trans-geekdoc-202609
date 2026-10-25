```
let confidence_level = 0.95;
let (lower_bound, upper_bound) = confidence_interval_mean(&data,
confidence_level);
println!("95% Confidence Interval: ({:.2}, {:.2})", lower_bound, upper_bound);
}
```

In this example, the function confidence_interval_mean calculates the sample mean, standard deviation, and standard error. It then uses the t-distribution to find the critical value and constructs the confidence interval around the sample mean.

# Confidence Interval for a Proportion

Constructing a confidence interval for a proportion follows a similar process. Let's consider an example where we estimate the proportion of defective items in a batch:

```
use statrs::distribution::ContinuousCDF;
fn confidence_interval_proportion(successes: u32, trials: u32, confidence_level:
f64) -> (f64, f64) {
    let p_hat = successes as f64 / trials as f64;
    let z = statrs::distribution::Normal::new(0.0, 1.0).unwrap().inverse_cdf((1.0 +
confidence_level) / 2.0);
    let margin_of_error = z * (p_hat * (1.0 - p_hat) / trials as f64).sqrt();
    let lower_bound = p_hat - margin_of_error;
    let upper_bound = p_hat + margin_of_error;
    (lower_bound, upper_bound)
}
fn main() {
    let successes = 45;
    let trials = 100;
```