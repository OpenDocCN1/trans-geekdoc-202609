run swiftly, providing real-time insights into inventory levels, reorder points, and stock turnover rates.

```
'''rust extern crate chrono;

use chrono::prelude::*;
use std::collections::HashMap;

fn main() {
    let mut inventory = HashMap::new();
    inventory.insert("raw_materials", (5000, Utc::now()));
    inventory.insert("finished_goods", (2000, Utc::now()));

    update_inventory(&mut inventory, "raw_materials", -500);
    let stock_levels = check_stock_levels(&inventory);

    println!("Current stock levels: {:?}", stock_levels);
}

fn update_inventory(inventory: &mut HashMap<&str, (i32, DateTime<Utc>)>,
                    item: &str, quantity: i32) {
    if let Some(stock) = inventory.get_mut(item) {
        stock.0 += quantity;
        stock.1 = Utc::now();
    }
}

fn check_stock_levels(inventory: &HashMap<&str, (i32, DateTime<Utc>)>) -> HashMap<&str, i32> {
    inventory.iter().map(|(&item, &(quantity, _))| (item, quantity)).collect()
}
'''
```

This example showcases a basic inventory management system where stock levels are updated and checked in real-time. Rust's efficient data handling ensures that inventory levels are accurate, helping manufacturers avoid costly overstock or stockout situations.