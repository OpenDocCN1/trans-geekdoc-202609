The “None” in the tensor shapes represents the batch size: this model allows batches
of any size.

Access to layer connectivity also means that you can inspect and reuse individual
nodes (layer calls) in the graph. The model.layers model property provides the list
of layers that make up the model, and for each layer you can query layer.input and
layer.output.

# Listing 7.12 Retrieving the inputs or outputs of a layer in a Functional model

```
>>> model.layers
[<tensorflow.python.keras.engine.input_layer.InputLayer at 0x7fa963f9d358>,
<tensorflow.python.keras.engine.input_layer.InputLayer at 0x7fa963f9d2e8>,
<tensorflow.python.keras.layers.input_layer.InputLayer at 0x7fa963f9d470>,
<tensorflow.python.keras.layers.merge.Concatenate at 0x7fa963f9d860>,
<tensorflow.python.keras.layers.core.Dense at 0x7fa964074390>,
<tensorflow.python.keras.layers.core.Dense at 0x7fa963f9d898>,
<tensorflow.python.keras.layers.core.Dense at 0x7fa963f95470>]
>>> model.layers[3].input
[<tf.Tensor 'title:0' shape=(None, 10000) dtype=float32>,
<tf.Tensor "text_body:0" shape=(None, 10000) dtype=float32>,
<tf.Tensor "tags:0" shape=(None, 100) dtype=float32>]
>>> model.layers[3].output
<tf.Tensor "concatenate/concat:0" shape=(None, 20100) dtype=float32>
```

This enables you to do feature extraction, creating models that reuse intermediate fea-
tures from another model.

Let’s say you want to add another output to the previous model—you want to esti-
mate how long a given issue ticket will take to resolve, a kind of difficulty rating. You
could do this via a classification layer over three categories: “quick,” “medium,” and
“difficult.” You don’t need to recreate and retrain a model from scratch. You can start
from the intermediate features of your previous model, since you have access to them,
like this.

# Listing 7.13 Creating a new model by reusing intermediate layer outputs

```
features = model.layers[4].output
layers[4] is our intermediate
Difficulty = layers.Dense(3, activation="softmax", name="difficulty") (features) ← Dense layer

new_model = keras.Model(
inputs=[title, text_body, tags],
outputs=[priority, department, difficulty])
```

Let’s plot our new model (see figure 7.4):

```
keras.utils.plot_model(
new_model, "updated_ticket_classifier.png", show_shapes=True)
```