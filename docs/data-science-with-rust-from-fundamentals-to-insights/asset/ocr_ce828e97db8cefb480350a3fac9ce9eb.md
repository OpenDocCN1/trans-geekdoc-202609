# 4. Mean Squared Error (MSE) and Root Mean Squared Error (RMSE)

For regression tasks, MSE and RMSE are common metrics.

+   - **MSE**: Measures the average squared difference between the actual and predicted values.
+   - **RMSE**: The square root of MSE, providing an error metric in the same unit as the target variable.

# Formulas:

```
[ \text{MSE} = \frac{1}{n} \sum_{i=1}^n (y_i - \hat{y}_i)^2 ]
[ \text{RMSE} = \sqrt{\text{MSE}} ]
```

# Rust Implementation:

+   1. **Calculate MSE and RMSE:**

```
```rust use ndarray::Array1;
fn main() {
    // Example predictions and true values
    let predictions = Array1::from(vec![2.5, 0.0, 2.1, 1.6]);
    let true_values = Array1::from(vec![3.0, -0.5, 2.0, 1.5]);

    let mse = calculate_mse(&predictions, &true_values);
    let rmse = calculate_rmse(mse);

    println!("MSE: {:.2}", mse);
    println!("RMSE: {:.2}", rmse);
}

fn calculate_mse(predictions: &Array1<f64>, true_values: &Array1<f64>) -> f64 {
    let sum_squared_error: f64 = predictions.iter()
        .zip(true_values.iter())
        .map(|(pred, &true_value)| (pred - true_value).powi(2))
        .sum();
}
```
```