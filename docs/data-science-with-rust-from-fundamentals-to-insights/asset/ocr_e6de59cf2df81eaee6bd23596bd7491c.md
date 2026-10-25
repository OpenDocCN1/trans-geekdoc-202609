```
opt.backward_step(&loss);
train_loss += f64::from(loss);
}
train_loss / 100.0
}
...
```

In this example, the network consists of three fully connected layers with ReLU activation functions. We use the Adam optimizer for training and evaluate the model using cross-entropy loss.

# 4. Evaluating Neural Network Models

Evaluating neural networks involves assessing their performance on unseen data. Common metrics include:

+   - **Accuracy:** The proportion of correctly classified instances.
+   - **Precision and Recall:** Metrics for evaluating binary classifiers, particularly in imbalanced datasets.
+   - **F1 Score:** The harmonic mean of precision and recall.

Here's an example of calculating accuracy:

```
...rust fn accuracy(predictions: &Tensor, labels: &Tensor) -> f64 {
let correct = predictions.argmax1(-1,
false).eq1(labels).sum(tch::Kind::Float); let total = labels.size()[0]
as f64; f64::from(correct) / total }
...
```

Using the accuracy function, we can evaluate the model's performance on the test dataset:

```
...rust fn main() { // (existing code for training the model) let
test_images = mnist.test_images.view([-1, 784]); let test_labels =
mnist.test_labels.to_kind(tch::Kind::Int64); let predictions =
```