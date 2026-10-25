```
ClientOptions::parse("mongodb://localhost:27017").await?;
let client = Client::with_options(client_options)?;
let database = client.database("test_db");
let collection = database.collection("test_collection");
let filter = doc! { "title": "Rust with MongoDB" };
collection.delete_one(filter, None).await?;
Ok(())
}
...
```

# Advanced Querying Techniques

NoSQL databases offer a range of advanced querying capabilities. Let's explore some examples using MongoDB.

+   1. Aggregation Framework:

Perform complex aggregations to transform and analyze data:

```
...rust use mongodb::{Client, options::ClientOptions, bson::doc};
\#[tokio::main]
async fn main() -> mongodb::error::Result<()> {
let client_options =
ClientOptions::parse("mongodb://localhost:27017").await?;
let client = Client::with_options(client_options)?;
let database = client.database("test_db");
let collection = database.collection("test_collection");
let pipeline = vec![
doc! { "\$(match)": { "title": "Rust with MongoDB" } },
doc! { "\$(group)": { "_id": "\$(title)", "count": { "\$(sum)": 1 } } }
];
let cursor = collection.aggregate(pipeline, None).await?;
for result in cursor {
println!("{:?}", result?);
}
```