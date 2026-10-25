```
let rolling_mean = df.lazy()
.select([
col("Price").rolling_mean(3, None, false)
])
.collect()?;
println!("{:?}", rolling_mean);
Ok(())
}
```

This code calculates a 3-day rolling mean of prices, smoothing out daily variations for clearer trend analysis.

# Practical Applications

Data aggregation techniques are integral to various stages of data science and analytics projects. Here are some practical applications:

+   1. **Business Analytics**

Aggregation helps in summarizing sales data, customer behavior, and operational metrics, facilitating strategic decision-making.

```
use polars::prelude::*;

fn main() -> Result<()> {
    let df = CsvReader::from_path("sales_data.csv")?
    .has_header(true)
    .finish()?;

    let summary = df.groupby("Product")?
    .agg(&[
    ("Revenue", &["sum"]),
    ("Quantity", &["mean"])
    ])?;

    println!("{:?}", summary);
}
```