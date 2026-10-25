```
group.mean().unwrap().powi(2)).sum()))
.sum::<f64>();
let df_between = data.len_of(ndarray::Axis(0)) as f64 - 1.0;
let df_within = data.len_of(ndarray::Axis(1)) as f64 *
data.len_of(ndarray::Axis(0)) as f64 - data.len_of(ndarray::Axis(0)) as f64;
(ss_between / df_between) / (ss_within / df_within)
}
...
```

**Explanation**:
- `one_way_anova` function calculates the F-statistic for one-way ANOVA.
- It compares variances between groups and within groups to determine significance.

# 4. Mann-Whitney U Test

**Purpose**: The Mann-Whitney U test is a non-parametric test used to compare differences between two independent groups when the data does not follow a normal distribution.

**Example**: Comparing the performance of two different machine learning models on a non-normally distributed dataset.

# Implementation in Rust:

+   1. Set Up Your Rust Environment:
+   ```sh
+   cargo new mann_whitney_u_test cd
+   mann_whitney_u_test
+   ```

+   1. Add Dependencies:
+   Update Cargo.toml:
+   ```toml
+   [dependencies] ndarray = "0.15"
+   ```

+   1. Implementing the Mann-Whitney U Test: