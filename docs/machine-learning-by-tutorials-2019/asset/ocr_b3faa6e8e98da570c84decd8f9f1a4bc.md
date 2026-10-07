# Machine Learning Chapter 9: Beyond Classification

The on_epoch_end() method is called by Keras as it completes an epoch of training, i.e., after the generator has run out of batches. Here, on_epoch_end() creates an instance variable, rows that contains the indices of the rows in the DataFrame. Normally self rows is [0, 1, 2, ...] if shuffle is true, the indices in self rows get randomly ordered. BoundingGenerator's constructor, __init__ in Python, also calls on_epoch_end() to make sure the rows are properly shuffled before the first epoch.

The method of work happens when __getitem__(). This is called when you next() or when you write train_generator[some_index]. This is where the batch gets put together. __getitem__() does the following:

+   1. Create NumPy arrays to hold the images X, and the targets y_class and y_box for each. These arrays are initially empty.
2. Get the indices of the rows to include in this batch. This looks up in self.rows.
3. For every row index, grab the corresponding row from the DataFrame. Load the image, preprocess using the standard MobileNet normalization function, and put it into X. Also get the class name, use label2index dictionary to convert it to a number and put it into y_class. Finally, get the bounding box coordinates and put them into y_box.
4. Return X, as well y_class and y_box, to the caller.

> Note: __getitem__() returns a tuple of two elements: The first one holds the array with the training images X, the second element holds the targets. But you have two different targets, one for the class and one for the bounding boxes. If you earlier wrote X, (y_class, y_box) = next(train_iter), to unpack this second tuple element into y_class and y_box variables.

To test that the generator works OK, the images and bounding boxes that it returns:

```
def plot_image_from_batch(X, y_class, y_bbox, img_idx):
    class_name = labels(y_class[img_idx])
    bbox = y_bbox[img_idx]
    plot_image(X[img_idx], [+bbox, class_name])
nplot_image_from_batch(X, y_class, y_bbox, 0)
```

raywendlich.com 319