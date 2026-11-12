![](bbox=[0.285, 0.095, 0.715, 0.355])

```
x = np.arange(-10., 10., 0.2)
x = np.arange(-10., 10., 0.2)
sig = tanh(x)
plt.plot(x,sig)
plt.show()
```

# 6. Python code for perceptron learning.

```
import numpy as np
class Perceptron1(object1):
    def __init__(selfl, no_of_inputs, threshold=50, learning_rate=0.02):
        Self1.threshold1 = threshold1
        self.learning_rate1 = learning_rate
        self.weights1 = np.zeros1(no_of_inputs + 1)

def predict1(self, inputs):
    Summation1 = np.dot(inputs, self.weights1[1:]) + self.weights[0]
    if summation1 > 0:
        Activation1 = 1
    else:
        Activation1 = 0
    return activation1
```