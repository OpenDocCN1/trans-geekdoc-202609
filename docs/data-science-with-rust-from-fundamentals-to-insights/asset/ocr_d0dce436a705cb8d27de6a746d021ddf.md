```
file.write_all(serialized.as_bytes()).unwrap();
}

fn load_model(path: &str) -> Model {
    let mut file = File::open(path).unwrap();
    let mut contents = String::new();
    file.read_to_string(&mut contents).unwrap();
    serde_json::from_str(&contents).unwrap()
}

fn main() {
    let model = Model {
        weights: vec![0.1, 0.2, 0.3],
        biases: vec![0.01, 0.02, 0.03],
    };

    save_model(&model, "model.json");

    let loaded_model = load_model("model.json");
    println!("Loaded Model: {:?}", loaded_model);
}
```

This example demonstrates how to serialize a model into JSON format and save it to disk, as well as how to load it back for inference.

# API Development

To serve predictions, you need to expose the model via an API. Rust's actix-web library provides a powerful framework for building web APIs.

Ensure your Cargo.toml includes the necessary dependencies:

```
```toml [dependencies] actix-web = "4.0" serde = { version = "1.0", features = ["derive"] } serde_json = "1.0" ```
```