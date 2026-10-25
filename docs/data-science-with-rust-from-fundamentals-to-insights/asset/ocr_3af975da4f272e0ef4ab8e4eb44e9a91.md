```
email: String,
}

async fn create_record(client: &Client, record: &Record) -> Result<(),
Box<dyn Error>> {
    let collection = client.database("testdb").collection("records");
    collection.insert_one(record, None).await?;
    Ok(())
}

async fn read_record(client: &Client, id: i32) -> Result<Record, Box<dyn
Error>> {
    let collection = client.database("testdb").collection("records");
    let filter = doc! { "id": id };
    let result = collection.find_one(filter, None).await?;
    Ok(result.unwrap())
}

\#[tokio::main]
async fn main() -> Result<(), Box<dyn Error>> {
    let mut client_options =
ClientOptions::parse("mongodb://localhost:27017").await?;
    client_options.app_name = Some("MyApp".to_string());
    let client = Client::with_options(client_options)?;

    let record = Record {
        id: 1,
        name: "John Doe".to_string(),
        age: 30,
        email: "john.doe@example.com".to_string(),
    };

    create_record(&client, &record).await?;
    let fetched_record = read_record(&client, 1).await?;
    println!("{:?}", fetched_record);
    Ok(())
}
```