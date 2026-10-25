```
fn main() {
    let user_purchases = vec!["book", "laptop", "smartphone"];
    let recommended_products = recommend_products(user_purchases);

    println!("Recommended for you: {:?}", recommended_products);
}

fn recommend_products(purchases: Vec<&str>) -> Vec<&str> {
    let mut rng = rand::thread_rng();
    let mut recommendations = Vec::new();

    for _ in 0..3 {
        let category = match rng.gen_range(0..3) {
            0 => "electronics",
            1 => "books",
            _ => "gadgets",
        };
        recommendations.push(category);
    }

    recommendations
}
...
```

In this simplified example, we simulate a recommendation engine that suggests product categories based on user purchases. While this is a basic implementation, it underscores Rust's ability to handle tasks efficiently.

# Inventory Management with Rust

Effective inventory management is crucial for retail success. Overstocking or understocking can lead to significant financial losses. Rust can help create sophisticated inventory management systems that predict stock levels based on historical data and current trends.