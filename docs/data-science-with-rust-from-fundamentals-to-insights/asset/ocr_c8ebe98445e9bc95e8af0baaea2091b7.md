```
y_true.mean().unwrap(); let ss_tot = (y_true - y_mean).mapv(|x|
x.pow(2)).sum(); 1.0 - (ss_res / ss_tot) }
fn main() {
// (existing code to compute y_pred from the model)
let y_pred = x.dot(&coefficients);
let r2 = r_squared(&y, &y_pred);
println!("R-squared: {}", r2);
}
...
```

# ## 5. Real-World Applications

Linear regression is widely applicable across various fields:

+   - **Finance**: Predicting stock prices based on historical data.
+   - **Marketing**: Estimating sales based on advertising spend.
+   - **Economics**: Understanding the impact of interest rates on economic growth.

# ## 6. Conclusion

# ### Logistic Regression: Decoding Classification Problems

# ## Introduction

Logistic regression is designed to predict the probability that a given input belongs to a particular category. Unlike linear regression, which outputs a continuous value, logistic regression outputs a probability value between 0 and 1, which is then used to classify the input into one of two categories.

The logistic regression model is defined by the logistic function, also known as the sigmoid function:

```
[ \sigma(z) = \frac{1}{1 + e^{-z}} ]
```

where ( z ) is the linear combination of the input variables: