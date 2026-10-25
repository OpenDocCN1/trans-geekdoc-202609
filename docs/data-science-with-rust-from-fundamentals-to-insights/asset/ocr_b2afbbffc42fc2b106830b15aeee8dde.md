In this example, the function one_sample_t_test calculates the sample mean and standard deviation, computes the t-value, and determines whether this t-value exceeds the critical value for the given significance level. If the t-value is greater than the critical value, the null hypothesis is rejected, indicating that the sample mean significantly differs from the population mean.

# Two-Sample t-Test

A two-sample t-test compares the means of two independent groups. This is useful when assessing whether the means from two different populations are equal, such as testing the effectiveness of two different treatments.

```
'''rust fn two_sample_t_test(data1: &[f64], data2: &[f64], alpha: f64) -> bool { let mean1: f64 = data1.iter().sum::() / data1.len() as f64; let mean2: f64 = data2.iter().sum::() / data2.len() as f64; let var1: f64 = data1.iter().map(|x| (x - mean1).powi(2)).sum::() / (data1.len() - 1) as f64; let var2: f64 = data2.iter().map(|x| (x - mean2).powi(2)).sum::() / (data2.len() - 1) as f64;

let pooled_var = ((data1.len() - 1) as f64 * var1 + (data2.len() - 1) as f64 * var2) / ((data1.len() + data2.len() - 2) as f64);
let t_value = (mean1 - mean2) / (pooled_var / data1.len() as f64 + pooled_var / data2.len() as f64).sqrt();
let degrees_of_freedom = (data1.len() + data2.len() - 2) as f64;

let students_t = StudentsT::new(0.0, 1.0, degrees_of_freedom).unwrap();
let critical_value = students_t.inverse_cdf(1.0 - alpha / 2.0);

t_value.abs() > critical_value
}

fn main() {
    let data1 = vec![14.8, 15.1, 15.5, 14.9, 15.2];
    let data2 = vec![15.3, 15.7, 16.0, 15.8, 15.9];
```