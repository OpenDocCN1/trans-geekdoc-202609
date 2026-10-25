```
let mut class_counts = HashMap::new();
for &prediction in &predictions {
    *class_counts.entry(prediction).or_insert(0) += 1;
}

*class_counts.iter().max_by(|a, b| a.1.cmp(b.1)).unwrap().0
```

```
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

    let prediction = bagging(&train_data, &test_instance, 10);
    println!("Predicted class: {}", prediction);
}
```

...

+   1. Implement Boosting:

+   2. Write Rust code to implement the Boosting algorithm:

```
```rust
use ndarray::Array2;

fn boosting(train_data: &Array2<f64>, test_instance: &Array2<f64>,
    num_models: usize) -> f64 {
    let mut weights = Array2::ones((train_data.nrows(), 1));
    let mut predictions = Vec::new();

    for _ in 0..num_models {
        let model = // Train model on weighted train_data
        let prediction = model.predict(test_instance);
        predictions.push(prediction);
```
```