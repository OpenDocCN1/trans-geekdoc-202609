```
Ok(())
}
...
```

In this example, the dataset is grouped by the "Department" column, and the sum and mean of salaries are calculated for each department. This approach provides a clear picture of departmental earnings, facilitating informed financial planning and resource allocation.

# Advanced Grouping Techniques

Beyond basic grouping, Rust and polars offer more sophisticated methods to gain deeper insights.

# Example: Grouping by Multiple Columns

Let's take a dataset of city populations over different years:

```
use polars::prelude::*;

fn main() -> Result<()> {
    let df = df! {
        "City" => &["Vancouver", "Toronto", "Vancouver", "Toronto", "Calgary"],
        "Year" => &[2021, 2021, 2022, 2022, 2021],
        "Population" => &[675218, 2930000, 681917, 2950000, 1239220]
    }?;

    let grouped_df = df.groupby(&["City", "Year"])?
        .agg(&[
            ("Population", &["sum", "mean"])
        ])?;

    println!("{:?}", grouped_df);

    Ok(())
}
...
```