Which indeed shows this is an image of a salad:

![](bbox=[0.331, 0.146, 0.668, 0.318])

# The classifier portion of the model already works

In fact, if you do `classifier_model.predict(x)`, which uses the last chapter's model without the bounding layers added, then you should get the exact same probability distribution. (Try it!)

Of course, you can also use the generator to make predictions:

```
preds = model.predict_generator(train_generator)
```

This will create predictions for all the rows in the `train_annotations` dataframe, an array of size (7040, 20) for the classification output, and an array of size (7040, 4) for the bounding box output. But as you've seen, the bounding box predictions don't make sense yet... unless you train the model.

# # Train it!

Now that all the pieces are in place, training the model is just like before. This model is again trained on a machine with a fast GPU. (If you have a slow computer, it's not really worth training this model yourself.)

First, create a generator for the validation set, with shuffle to False:

```
val_generator = BoundingBoxGenerator(val_annotations, val_dir, image_height, image_width, batch_size, shuffle=False)
```

Some of the code now lives in `helpers.py`, so import those functions:

```
from helpers import combine_histories, plot_loss, plot_bbox_histories = []
```