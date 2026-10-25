+   3. **Calculating the Margin of Error**: This typically involves the standard error of the estimate and a critical value from the appropriate distribution (e.g., z-distribution for large samples or t-distribution for smaller samples).

+   4. **Assembling the Interval**: Combine the point estimate and the margin of error to form the lower and upper bounds of the confidence interval.

# # Example: Confidence Interval for a Mean

Let's consider an example where we construct a 95% confidence interval for the mean height of a sample of plants using Rust:

```
```rust
use statrs::distribution::{StudentsT, Univariate};

fn confidence_interval_mean(data: &[f64], confidence_level: f64) -> (f64, f64) {
    let sample_mean: f64 = data.iter().sum::<f64>() / data.len() as f64;
    let variance: f64 = data.iter().map(|x| (x - sample_mean).powi(2)).sum::<f64>()
    () / (data.len() - 1) as f64;
    let std_dev = variance.sqrt();
    let std_error = std_dev / (data.len() as f64).sqrt();
    let degrees_of_freedom = data.len() as f64 - 1.0;

    // Calculate the critical t-value from the StudentsT distribution
    let students_t = StudentsT::new(0.0, 1.0, degrees_of_freedom).unwrap();
    let critical_value = students_t.inverse_cdf((1.0 + confidence_level) / 2.0);

    let margin_of_error = critical_value * std_error;
    let lower_bound = sample_mean - margin_of_error;
    let upper_bound = sample_mean + margin_of_error;

    (lower_bound, upper_bound)
}

fn main() {
    let data = vec![14.8, 15.1, 15.5, 14.9, 15.2];
```
```