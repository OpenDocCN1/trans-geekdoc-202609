
```rust
4.0, 5.0, 1.0,
5.0, 6.0, 1.0
]).unwrap();
let centroids = kmeans(&data, 2, 100);
println!("Centroids: {:?}", centroids);
}
...
```

## Step 7: Hyperparameter Tuning

- 1. Implement Hyperparameter Tuning:
- 2. Write Rust code to perform hyperparameter tuning using grid search:

```rust
use ndarray::Array2;
use std::collections::HashMap;

fn hyperparameter_tuning(train_data: &Array2<f64>, test_instance: &Array2<f64>) -> HashMap<String, f64> {
    let mut best_params = HashMap::new();
    let mut best_score = f64::INFINITY;

    for learning_rate in vec![0.01, 0.1, 0.2] {
        for num_epochs in vec![100, 200, 300] {
            let model = // Train model with learning_rate and num_epochs
            let prediction = model.predict(test_instance);

            let score = // Calculate score (e.g., MSE)
            if score < best_score {
                best_score = score;
                best_params.insert("learning_rate".to_string(), learning_rate);
                best_params.insert("num_epochs".to_string(), num_epochs);
            }
        }
    }

    best_params
}
```

```rust
fn main() {
    let train_data = Array2::from_shape_vec((5, 3), vec![
    1.0, 2.0, 0.0,
    2.0, 3.0, 0.0,
    3.0, 4.0, 1.0,
    4.0, 5.0, 1.0,
    5.0, 6.0, 1.0
    ]).unwrap();

    let test_instance = Array2::from_shape_vec((1, 2), vec![1.5,
    2.5]).unwrap();

    let best_params = hyperparameter_tuning(&train_data,
    &test_instance);
    println!("Best parameters: {:?}", best_params);
}
```

## Step 8: Model Deployment and Performance Monitoring

- 1. Implement Model Deployment:
- 2. Write Rust code to deploy the model using a simple web server:

```rust
use warp::Filter;

fn main() {
    let predict = warp::path!("predict" / f64 / f64)
    .map(|feature1, feature2| {
    let test_instance = Array2::from_shape_vec((1, 2), vec![feature1,
    feature2]).unwrap();
    let prediction = // Load model and predict test_instance
    format!("Predicted value: {}", prediction)
    });

    warp::serve(predict)
    .run([127, 0, 0, 1], 3030));
}
```

- 1. Implement Performance Monitoring:
- 2. Write Rust code to log model performance metrics:

```rust
fn main() {
    env_logger::init();

    let train_data = Array2::from_shape_vec((5, 3), vec![
        1.0, 2.0, 0.0,
        2.0, 3.0, 0.0,
        3.0, 4.0, 1.0,
        4.0, 5.0, 1.0,
        5.0, 6.0, 1.0
    ]).unwrap();

    let test_instance = Array2::from_shape_vec((1, 2), vec![1.5,
        2.5]).unwrap();

    let prediction = // Train and predict
    info!("Prediction: {}", prediction);

    let accuracy = // Calculate accuracy
    info!("Accuracy: {}", accuracy);
}
```

## Step 9: Documenting and Presenting the Project

- 1. Write a Report:
- 2. Summarize the project objectives, steps taken, and results.
- 3. Discuss challenges faced and how they were overcome.
- 4. Include sample visualizations and explain their significance.
- 5. Prepare a Presentation:
- 6. Create a presentation to showcase your project, including code snippets, output results, and your findings.
- 7. Submit Your Project:
- 8. Ensure all code is well-documented and organized.
- 9. Submit your project report, presentation, and code files as specified by your instructor.

They will learn how to implement, evaluate, and interpret various models, providing a solid foundation for more complex data science tasks and projects.

## Comprehensive Project: "Data Engineering with Rust"

### Project Overview

In this project, students will build a complete data engineering pipeline using Rust. This project will involve extracting data from various sources, transforming and cleaning the data, and loading it into a database. The students will also implement batch processing, data streaming, and integrate data storage solutions.

### Project Objectives

- 1. Understand the components of a data pipeline.
- 2. Implement ETL processes using Rust.
- 3. Utilize SQL and NoSQL databases for data storage.
- 4. Perform batch and stream processing.
- 5. Apply best practices in data engineering.

### Project Steps

### Step 1: Setting Up the Rust Environment

- 1. Install Rust:
- 2. Follow the instructions on the official Rust website to install Rust using the rustup tool.
- 3. Verify the installation by running rustc --version in your terminal.
- 4. Set Up Visual Studio Code (VSCode):
- 5. Download and install VSCode.
- 6. Install the Rust extension for VSCode by searching for "rust-analyzer" in the extensions marketplace.
- 7. **Create a New Rust Project:**
- 8. Open your terminal and run: `bash cargo new data_engineering_project cd data_engineering_project` - Open the project folder in VSCode.
- 1. **Understand Cargo:**
- 2. Explore the Cargo.toml file which manages dependencies.
- 3. Learn basic Cargo commands like cargo build and cargo run.

### Step 2: Building ETL Processes

- 1. **Add Dependencies:**
- 2. Add the following crates to Cargo.toml for handling CSV, JSON, and database connections:

```toml
[dependencies]
csv = "1.1"
serde = { version = "1.0", features = ["derive"] }
serde_json = "1.0"
tokio = { version = "1.0", features = ["full"] }
sqlx = { version = "0.5", features = ["runtime-tokio-rustls", "postgres"] }
mongodb = "2.0"
```

- 1. **Extracting Data:**
- 2. Write Rust code to read data from a CSV file:

```rust
use csv::ReaderBuilder;
use std::error::Error;

fn read_csv(file_path: &str) -> Result<(), Box<dyn Error>> {
    let mut rdr = ReaderBuilder::new().from_path(file_path)?;
    for result in rdr.records() {
        let record = result?;
        println!("{:?}", record);
    }
    Ok(())
}
```

```rust
fn main() {
    if let Err(err) = read_csv("data/input.csv") {
        println!("Error reading CSV file: {}", err);
    }
}
```

- 1. **Transforming Data:**
- 2. Write Rust code to transform and clean the data:

```rust
use serde::Deserialize;
use std::error::Error;

#[derive(Debug, Deserialize)]
struct Record {
    id: u32,
    name: String,
    age: Option<u8>,
    email: Option<String>,
}
```

```rust
fn transform_data(record: Record) -> Option<Record> {
    if record.age.is_some() && record.email.is_some() {
        Some(record)
    } else {
        None
    }
}
```

```rust
fn read_and_transform_csv(file_path: &str) -> Result<(), Box<dyn Error>> {
    let mut rdr = ReaderBuilder::new().from_path(file_path)?;
    for result in rdr.deserialize() {
        let record: Record = result?;
        if let Some(cleaned_record) = transform_data(record) {
            println!("{:?}", cleaned_record);
        }
    }
    Ok(())
}
```

```rust
fn main() {
    if let Err(err) = read_and_transform_csv("data/input.csv") {
        println!("Error processing CSV file: {}", err);
    }
}
```

- 1. Loading Data into a Database:
- 2. Write Rust code to load data into a PostgreSQL database:

```rust
use sqlx::postgres::PgPoolOptions;
use std::error::Error;

#[derive(Debug, sqlx::FromRow)]
struct Record {
    id: i32,
    name: String,
    age: i32,
    email: String,
}

async fn load_data(pool: &sqlx::PgPool, record: Record) -> Result<(), Box<dyn Error>> {
    sqlx::query("INSERT INTO records (id, name, age, email) VALUES ($1, $2, $3, $4)")
        .bind(record.id)
        .bind(record.name)
        .bind(record.age)
        .bind(record.email)
        .execute(pool)
        .await?;

    Ok(())
}
```

```rust
#[tokio::main]
async fn main() -> Result<(), Box<dyn Error>> {
    let pool = PgPoolOptions::new()
        .max_connections(5)
        .connect("postgres://user:password@localhost/database")
        .await?;

    let record = Record {
        id: 1,
        name: "John Doe".to_string(),
        age: 30,
        email: "john.doe@example.com".to_string(),
    };

    load_data(&pool, record).await?;

    Ok(())
}
```

### Step 3: Data Storage Solutions

- 1. Working with SQL Databases:
- 2. Write Rust code to interact with a SQL database (PostgreSQL) for CRUD operations:

```rust
use sqlx::postgres::PgPoolOptions;
use std::error::Error;

#[derive(Debug, sqlx::FromRow)]
struct Record {
    id: i32,
    name: String,
    age: i32,
    email: String,
}
```

```rust
async fn create_record(pool: &sqlx::PgPool, record: &Record) -> Result<(), Box<dyn Error>> {
    sqlx::query("INSERT INTO records (id, name, age, email) VALUES ($1, ...
```
