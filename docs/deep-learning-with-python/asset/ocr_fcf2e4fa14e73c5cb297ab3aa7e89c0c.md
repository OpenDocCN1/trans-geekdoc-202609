```
priority = self.priority_scorer(features)
department = self.department_classifier(features)
return priority, department
```

Once you've defined the model, you can instantiate it. Note that it will only create its weights the first time you call it on some data, much like Layer subclasses:

```
model = CustomerTicketModel(num_departments=4)
```

```
priority, department = model(
    {"title": title_data, "text_body": text_body_data, "tags": tags_data})
```

So far, everything looks very similar to Layer subclassing, a workflow you encountered in chapter 3. What, then, is the difference between a Layer subclass and a Model subclass? It's simple: a “layer” is a building block you use to create models, and a “model” is the top-level object that you will actually train, export for inference, etc. In short, a Model has fit(), evaluate(), and predict() methods. Layers don't. Other than that, the two classes are virtually identical. (Another difference is that you can save a model to a file on disk, which we will cover in a few sections.)

You can compile and train a Model subclass just like a Sequential or Functional model:

```
model.compile(optimizer="rmsprop",
    loss=["mean_squared_error", "categorical_crossentropy"],
    metrics=[["mean_absolute_error"], ["accuracy"]])
model.fit(({"title": title_data,
    "text_body": text_body_data,
    "tags": tags_data},
    [priority_data, department_data],
    epochs=1)
model.evaluate(({"title": title_data,
    "text_body": text_body_data,
    "tags": tags_data},
    [priority_data, department_data])
priority_preds, department_preds = model.predict(({"title": title_data,
    "text_body": text_body_data,
    "tags": tags_data}))
```

The structure of what you pass as the loss and metrics arguments must match exactly what gets returned by call()—here, a list of two elements.

The structure of the target data must match exactly what is returned by the call() method—here, a list of two elements.

The structure of the input data must match exactly what is expected by the call() method—here, a dict with keys title, text_body, and tags.

The Model subclassing workflow is the most flexible way to build a model. It enables you to build models that cannot be expressed as directed acyclic graphs of layers—imagine, for instance, a model where the call() method uses layers inside a for loop, or even calls them recursively. Anything is possible—you're in charge.

# BEWARE: WHAT SUBCLASSED MODELS DON'T SUPPORT

This freedom comes at a cost: with subclassed models, you are responsible for more of the model logic, which means your potential error surface is much larger. As a result, you will have more debugging work to do. You are developing a new Python object, not just snapping together LEGO bricks.