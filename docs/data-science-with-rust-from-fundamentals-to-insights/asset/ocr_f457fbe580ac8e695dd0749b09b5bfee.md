# Loading Data and Training the Model

Let's consider a dataset of iris flowers, a classic example for classification tasks.

```
```rust
/// rust use ndarray::array; use linfa::prelude::*; use
/// linfa_svm::Svm; use linfa_svm::SvmParams; use linfa_svm::Kernel;
fn main() {
    // Example data: sepal length, sepal width, petal length, petal width (4
    // features)
    let x = array![[5.1, 3.5, 1.4, 0.2],
        [4.9, 3.0, 1.4, 0.2],
        [5.8, 2.7, 5.1, 1.9],
        [7.1, 3.0, 5.9, 2.1]];
    let y = array![0, 0, 1, 1]; // species labels

    // Define the SVM parameters
    let params = SvmParams::new()
        .kernel(Kernel::Rbf { gamma: 0.1 })
        .c(1.0);

    // Train the SVM model
    let svm = Svm::new(params)
        .fit(&x, &y)
        .expect("Failed to fit SVM model");

    // Predict the species of a new iris flower
    let new_flower = array![[6.0, 3.0, 4.8, 1.8]];
    let prediction = svm.predict(&new_flower);
    println!("Prediction: {:?}", prediction);
}
///
```
```

In this example, the x array contains the features, while the y array contains the species labels. The SVM model is trained using the RBF