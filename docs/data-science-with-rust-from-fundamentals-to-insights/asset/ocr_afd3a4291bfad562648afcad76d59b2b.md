# Setting Up for Data Aggregation in Rust

To perform data aggregation in Rust, you will need to set up the polars library. Add the following to your Cargo.toml file:

```
toml [dependencies] polars = "0.22"
```

Run cargo build to ensure the dependencies are correctly installed.

# Summarization Techniques

Summarization is the simplest form of data aggregation, providing quick insights into a dataset's overall characteristics.

+   1. Sum and Average

Calculating the sum and average of numerical data helps in understanding the total and mean values, which are often initial steps in data analysis.

```
rust use polars::prelude::*;

fn main() -> Result<()> {
    let df = df! {
        "Values" => &[10, 20, 30, 40, 50]
    }?;

    // Sum
    let sum_value = df["Values"].sum();
    println!("Sum: {:?}", sum_value);

    // Average
    let avg_value = df["Values"].mean();
    println!("Average: {:?}", avg_value);
}
```