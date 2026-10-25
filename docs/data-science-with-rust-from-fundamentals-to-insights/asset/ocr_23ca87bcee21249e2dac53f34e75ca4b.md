# 1. Load and Prepare Data:

Suppose we have a dataset of hours studied and exam scores:

```
use ndarray::Array1;

fn main() {
    let hours_studied: Array1<f64> = array![1.0, 2.0, 3.0, 4.0, 5.0];
    let scores: Array1<f64> = array![50.0, 55.0, 60.0, 65.0, 70.0];

    let correlation = pearson_correlation(&hours_studied,
        &scores).unwrap();
    println!("Pearson Correlation Coefficient: {}", correlation);
}

fn pearson_correlation(x: &Array1<f64>, y: &Array1<f64>) -> Result<f64,
    &'static str> {
    if x.len() != y.len() {
        return Err("Input arrays must have the same length");
    }

    let x_mean = x.mean().unwrap();
    let y_mean = y.mean().unwrap();
    let numerator = x.iter().zip(y.iter()).map(|(&xi, &yi)| (xi - x_mean) * (yi - y_mean)).sum::<f64>();
    let denominator = ((x.iter().map(|&xi| (xi - x_mean).powi(2)).sum::<f64>()) *
    (y.iter().map(|&yi| (yi - y_mean).powi(2)).sum::<f64>
    ())).sqrt();

    Ok(numerator / denominator)
}
```

**Explanation**:
- The `pearson_correlation` function calculates the correlation coefficient using the Pearson method.