```
5.0, 6.0,
6.0, 7.0,
7.0, 8.0,
8.0, 9.0,
9.0, 10.0,
10.0, 11.0
]).unwrap();

let mut rng = thread_rng();
let mut data_vec: Vec<_> = data.axis_iter(ndarray::Axis(0)).collect();
data_vec.shuffle(&mut rng);

let train_size = (data_vec.len() as f64 * 0.8) as usize;
let (train_data, test_data) = data_vec.split_at(train_size);

println!("Training data: {:?}", train_data);
println!("Testing data: {:?}", test_data);

}
```

...

# Step 3: Implementing Linear Regression

+   1. **Add Dependencies for Linear Algebra:**
+   2. Add the `ndarray-linalg` crate to handle linear algebra
+   operations: `` `toml [dependencies] ndarray = "0.15"
+   ndarray-linalg = "0.14" ``

...

+   1. **Implement Linear Regression:**
+   2. Write Rust code to implement linear regression: `` `rust
+   use ndarray::Array2; use ndarray_linalg::Solve;
+   
+   fn main() {
+       let x = Array2::from_shape_vec((5, 2), vec![1.0, 1.0, 1.0, 2.0, 1.0, 3.0,
+   1.0, 4.0, 1.0, 5.0]).unwrap();
+       let y = Array2::from_shape_vec((5, 1), vec![1.0, 2.0, 3.0, 4.0,
+   5.0]).unwrap();