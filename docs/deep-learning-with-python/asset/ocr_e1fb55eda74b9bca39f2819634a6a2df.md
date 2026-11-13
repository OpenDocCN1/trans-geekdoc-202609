![](bbox=[0.174, 0.082, 0.542, 0.378])

Figure 9.12 The test cat picture

```
Listing 9.8 Instantiating a model that returns layer activations

from tensorflow.keras import layers

layer_outputs = []
layer_names = []
for layer in model.layers:
    if isinstance(layer, (layers.Conv2D, layers.MaxPooling2D)):
        layer_outputs.append(layer.output)
        layer_names.append(layer.name)
activation_model = keras.Model(inputs=model.input, outputs=layer_outputs)
```

When fed an image input, this model returns the values of the layer activations in the original model, as a list. This is the first time you’ve encountered a multi-output model in this book in practice since you learned about them in chapter 7; until now, the models you’ve seen have had exactly one input and one output. This one has one input and nine outputs: one output per layer activation.

```
Listing 9.9 Using the model to compute layer activations

activations = activation_model.predict(img_tensor)
```

For instance, this is the activation of the first convolution layer for the cat image input:

>>> first_layer_activation = activations[0]
>>> print(first_layer_activation.shape)
(1, 178, 178, 32)