```
Ok(())
}

fn main() {
    if let Err(err) = read_and_transform_csv("data/input.csv") {
        println!("Error processing CSV file: {}", err);
    }
}
```

+   1. Loading Data into a Database:

+   2. Write Rust code to load data into a PostgreSQL database:

```
```rust use sqlx::postgres::PgPoolOptions; use std::error::Error;

#[derive(Debug, sqlx::FromRow)]
struct Record {
    id: i32,
    name: String,
    age: i32,
    email: String,
}

async fn load_data(pool: &sqlx::PgPool, record: Record) -> Result<(),
Box<dyn Error>> {
    sqlx::query("INSERT INTO records (id, name, age, email) VALUES ($1, \
(2, \)3, \4")")
        .bind(record.id)
        .bind(record.name)
        .bind(record.age)
        .bind(record.email)
        .execute(pool)
        .await?;

    Ok(())
}
```