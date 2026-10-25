# Reading and Writing CSV Files

# Why CSV Files?

CSV (Comma-Separated Values) files are a staple in data science due to their simplicity and compatibility. They offer a straightforward way to represent tabular data, making it easy to import and export datasets between various tools and platforms. Whether you’re dealing with financial records, user data, or experimental results, CSV files provide a versatile solution for data handling.

# Setting Up Your Rust Environment for CSV Handling

To work with CSV files in Rust, we’ll utilize the `csv` crate, which simplifies the process of reading and writing CSV data. Start by updating your `Cargo.toml` to include the `csv` crate:

```
```toml [dependencies] csv = "1.1" serde = { version = "1.0", features = ["derive"] } ```
```

The `serde` crate is also included to facilitate the serialization and deserialization of data, making it easier to convert between CSV records and Rust structs.

# Reading CSV Files

Imagine you’re working on a financial analysis project, and you’ve just received a CSV file containing historical stock prices. The first step is to read this data into your Rust program. Here’s an example of how to accomplish this:

```
```rust use csv::ReaderBuilder; use serde::Deserialize; use std::error::Error;

#[derive(Debug, Deserialize)]
struct StockPrice {
    date: String,
    open: f64,
    high: f64,
```
```