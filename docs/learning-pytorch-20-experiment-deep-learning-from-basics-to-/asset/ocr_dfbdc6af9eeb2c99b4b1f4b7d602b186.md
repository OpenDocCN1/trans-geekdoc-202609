```
pip install onnx-tf
```

# Loading Pre-trained TensorFlow Model

Next, we import the necessary libraries and load the pre-trained MobileNet model.

```
import tensorflow as tf
```

```
model =
tf.keras.applications.MobileNetV2(weights='imagenet',
include_top=True)
```

In the above code, tf.keras.applications.MobileNetV2 is used to load the pre-trained MobileNet model, and weights='imagenet' specifies that we want the version of the model that was trained on the ImageNet dataset.

# Converting TensorFlow Model to ONNX

After loading the TensorFlow model, we convert it to ONNX using the tf2onnx converter.

First, you need to install the tf2onnx converter.