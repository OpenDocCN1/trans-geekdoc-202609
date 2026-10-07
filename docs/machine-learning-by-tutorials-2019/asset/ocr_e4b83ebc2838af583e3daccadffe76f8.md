A bit of math is needed to convert the bounding boxes from one format to the other.

Once all the annotations for the current image have been converted and added to the img_annotations list, you append it to the grand list of all annotations:

```
if len(img_annotations) > 0:
    all_annotations.append(img_annotations)
else:
    all_annotations.append(None)
```

If there were no annotations, you still need to append something to that so list has exactly the same number of rows as the SFrame. In that case, you append None, which is Python's version of Swift's.

Finally, once you've looped through all images, the al_annotations list contains all their ground-truth bounding boxes in Turf. Put this into an SArray object and assign it to a new column in the SFrame named "annotations":

```
data['annotations'] = tc.SArray(data=all_annotations, dtype=list)
return data.dropna()
```

There's one more thing to do. Here, not all images will have annotations. For such images, the annotations field in the SFrame be None. You don't want to include these images during training.

The easiest way to remove those images from the SFrame is to call data.dropna(). This filters out any rows with missing values.

And that's for load_images_with_annotations().

Now you can train the images and their bounding boxes. Make sure the folder you're working in contains the snacks dataset. If you haven't downloaded it already, open the snacks-download-link.webloc from the starter folder, and once downloaded, move the snacks folder to your working directory.

Load the images with the following code:

```
data_dir = "snacks"
train_dir = os.path.join(data_dir, "train")
train_data = load_images_with_annotations(train_dir,
data_dir + "/annotations-train.csv")
```