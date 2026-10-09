In this modification, we have added the following to the baseline model:

+   from tensorflow.keras.regularizers import l1
In each dense layer definition, we added the kernel_regularizer parameter and set it to l1(0.01). This applies L1 regularization to the weights of each dense layer with a regularization strength of 0.01. This value provides a moderate regularization effect. It is often chosen as a starting point and adjusted based on model performance during training. Typical values range from 0.001 to 0.1, with some adjustments made based on empirical observations during model training.

To add L2 regularization, we can follow a similar approach, but use the l2 function from Keras instead:

```
```python
from tensorflow.keras.regularizers import l2

def create_and_train_model(
    self,
    train_features,
    train_labels,
    epochs=100,
    batch_size=32
):
    self.input_shape = (train_features.shape[1],)
    self.model = Sequential([
        Dense(
            64,
            activation='relu',
            kernel_regularizer=l2(0.01),
            input_shape=self.input_shape
        ),
    ```
```