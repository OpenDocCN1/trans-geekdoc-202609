```
let xt = x.t();
let xtx = xt.dot(&x);
let xty = xt.dot(&y);

let beta = xtx.solve_into(xty).unwrap();
println!("Regression coefficients: {:?}", beta);
}
```

+   1. **Evaluate Model Performance:**
+   2. Write code to calculate Mean Squared Error (MSE): ```rust
+   fn mean_squared_error(y_true: &Array2, y_pred: &Array2)
+   -> f64 { let diff = y_true - y_pred; diff.mapv(|x|
+   x.powi(2)).mean().unwrap() }
+   ```

```
fn main() {
// (same as above)
let beta = xtx.solve_into(xty).unwrap();

let y_pred = x.dot(&beta);
let mse = mean_squared_error(&y, &y_pred);

println!("Mean Squared Error: {}", mse);
}
```

# **Step 4: Implementing Logistic Regression**

+   1. **Add Dependencies for Optimization:**
+   2. Add the ndarray-rand crate for random number generation in
+   ndarray: ```toml [dependencies] ndarray = "0.15"
+   ndarray-rand = "0.14"
+   ```

+   1. **Implement Logistic Regression:**
+   2. Write Rust code to fit a logistic regression model using
+   gradient descent: ```rust use ndarray::Array2; use