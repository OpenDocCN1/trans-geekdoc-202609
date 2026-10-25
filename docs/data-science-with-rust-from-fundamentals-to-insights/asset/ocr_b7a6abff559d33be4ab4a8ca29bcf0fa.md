```
```rust
let normal = Normal::new(0.0, 1.0).unwrap();
let p_value = 2.0 * (1.0 - normal.cdf(t_statistic.abs())));
println!("t-statistic: {}", t_statistic);
println!("p-value: {}", p_value);
}
...
```

# Step 5: Regression Analysis and Correlation

# 1. Simple Linear Regression:

2. Write Rust code to perform simple linear regression:

```
```rust
use ndarray::Array2; use ndarray_linalg::Solve;
fn main() {
let x = Array2::from_shape_vec((5, 2), vec![1.0, 1.0, 1.0, 2.0, 1.0, 3.0,
1.0, 4.0, 1.0, 5.0]).unwrap();
let y = Array2::from_shape_vec((5, 1), vec![1.0, 2.0, 3.0, 4.0,
5.0]).unwrap();
let xt = x.t();
let xtx = xt.dot(&x);
let xty = xt.dot(&y);
let beta = xtx.solve_into(xty).unwrap();
println!("Regression coefficients: {:?}", beta);
}
...
```

# 1. Correlation Analysis:

2. Write Rust code to calculate the Pearson correlation coefficient:

```
```rust
use stats::statistics::Statistics;
fn main() {
let sample1 = vec![1.0, 2.0, 3.0, 4.0, 5.0];
let sample2 = vec![2.0, 3.0, 4.0, 5.0, 6.0];
let correlation = sample1.pearson(&sample2).unwrap();
println!("Pearson correlation coefficient: {}", correlation);
```