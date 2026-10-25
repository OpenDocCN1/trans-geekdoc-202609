```
```rust
use mongodb::{Client, options::ClientOptions, bson::doc};

#[tokio::main]
async fn main() -> mongodb::error::Result<()> {
    let client_options =
        ClientOptions::parse("mongodb://localhost:27017").await?;
    let client = Client::with_options(client_options)?;

    let database = client.database("test_db");
    let collection = database.collection("test_collection");

    let new_doc = doc! { "title": "Rust with MongoDB", "body": "Creating records in MongoDB" };
    collection.insert_one(new_doc, None).await?;

    Ok(())
}
```
```

# 1. Reading Records:

Retrieve documents from the collection:

```
```rust
use mongodb::{Client, options::ClientOptions, bson::doc};

#[tokio::main]
async fn main() -> mongodb::error::Result<()> {
    let client_options =
        ClientOptions::parse("mongodb://localhost:27017").await?;
    let client = Client::with_options(client_options)?;

    let database = client.database("test_db");
    let collection = database.collection("test_collection");

    let filter = doc! { "title": "Rust with MongoDB" };
    let document = collection.find_one(filter, None).await?;

    if let Some(doc) = document {
        println!("Document: {:?}", doc);
    } else {
```
```