# An Introduction to Deep Convolutional Neural Networks With Keras

Now we write the program on two-input OR gate.

```
#TRAIN AND TEST MODEL ON OR GATE
import Keras
import numpy as np
from IPython.display import SVG
from keras.utils.vis_utils import model_to_dot

input = np.array([[0,0], [0,1], [1,0], [1,1]])
print(input)

[[0 0] [0 1] [1 0] [1 1]]

output = np.array([[0],[1],[1],[1]])
print(output)

[[0] [1] [1] [1]]

model=keras.models.Sequential(layers=[keras.layers.Dense(input_dim =2, units = 1), keras.Activation(keras.activations.sigmoid())])nmodel.compile(optimizer=keras.optimizers.SGD(lr=.5),loss='mse')
model.summary()
```

| Layer (type) | Output Shape | Param # |
|---|---|--|
| dense_2 (Dense) | (None, 1) | 3 |
| activation_2 (Activation) | (None, 1) | 0 |

Total params: 3
Trainable params: 3
Non-trainable params:

SVG(model_to_dot(model, show_shapes=True).create(prog='dot', format='svg')

```
Epoch 1/1000
4/4 [====================================] - 0s - loss: 0.2879
Epoch 2/1000
4/4 [====================================] - 0s - loss: 0.2681
Epoch 3/1000
```