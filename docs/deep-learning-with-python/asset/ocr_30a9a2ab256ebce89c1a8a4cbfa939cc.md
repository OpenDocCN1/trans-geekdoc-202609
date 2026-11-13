![](bbox=[0.13, 0.08, 0.87, 0.28])

Figure 7.4 Plot of our new model

# 7.2.3 Subclassing the Model class

The last model-building pattern you should know about is the most advanced one: Model subclassing. You learned in chapter 3 how to subclass the Layer class to create custom layers. Subclassing Model is pretty similar:

+   - In the `__init__()` method, define the layers the model will use.
+   - In the `call()` method, define the forward pass of the model, reusing the layers previously created.
+   - Instantiate your subclass, and call it on data to create its weights.

# REWRITING OUR PREVIOUS EXAMPLE AS A SUBCLASSED MODEL

Let’s take a look at a simple example: we will reimplement the customer support ticket management model using a Model subclass.

# Listing 7.14 A simple subclassed model

```
class CustomerTicketModel(keras.Model):

    def __init__(self, num_departments):
        super().__init__()
        self.concat_layer = layers.Concatenate()
        self.mixing_layer = layers.Dense(64, activation="relu")
        self.priority_scorer = layers.Dense(1, activation="sigmoid")
        self.department_classifier = layers.Dense(
            num_departments, activation="softmax")

    def call(self, inputs):
        title = inputs["title"]
        text_body = inputs["text_body"]
        tags = inputs["tags"]

        features = self.concat_layer((title, text_body, tags))
        features = self.mixing_layer(features)
```