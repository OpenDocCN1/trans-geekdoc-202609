# Validation of Model Conversion

After converting the model from TensorFlow to PyTorch via ONNX, you may want to validate the conversion to ensure it was successful. This process usually involves performing inference on both the original TensorFlow model and the converted PyTorch model, then comparing the outputs.

Below is a simple approach to validating your converted model:

# Make TensorFlow Model Prediction

First, use your TensorFlow model to make a prediction on a sample input.

```
```python
import numpy as np

# Create a random input tensor in TensorFlow

input_tensor = np.random.rand(1, 224, 224,
3).astype(np.float32)
```
```