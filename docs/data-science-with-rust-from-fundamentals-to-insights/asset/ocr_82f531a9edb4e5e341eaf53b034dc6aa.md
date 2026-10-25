# # Computing Descriptive Statistics

# ## 1. Central Tendency

The central tendency measures the "typical" value within a dataset. Here's how you can compute the mean, median, and mode in Rust using polars:

```
```rust
use polars::prelude::*;

fn main() -> Result<()> {
    let df = df! {
        "Values" => &[10, 20, 20, 30, 40, 50, 50, 50]
    }?;

    // Mean
    let mean_value = df["Values"].mean();
    println!("Mean: {:?}", mean_value);

    // Median
    let median_value = df["Values"].median();
    println!("Median: {:?}", median_value);

    // Mode
    let mode_value = df["Values"].mode();
    println!("Mode: {:?}", mode_value);

    Ok(())
}
```
```

This code computes the mean, median, and mode of a dataset, providing a quick overview of the central tendency.

# ## 1. Variability

Variability measures the spread or dispersion of data points. Common metrics include range, variance, and standard deviation:

```
```rust
use polars::prelude::*;
```
```