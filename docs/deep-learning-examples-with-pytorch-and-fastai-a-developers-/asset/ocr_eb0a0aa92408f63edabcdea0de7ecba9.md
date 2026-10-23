```
get_items=get_image_files,
splitter=FileSplitter(path/"valid.txt"), get_y=get_mask,
batch_tfms=[*aug_transforms(size=half_size),
→ Normalize.from_stats(*imagenet_stats)] )
```

Create the dataloaders

```
dataloaders = camvid.dataloaders(path/"images/", bs=2)
```

Now we can look at a batch. We see that the segmentation mask is an overlay of the original image.

```
dataloaders.show_batch(max_n=4, figsize=(14,10))
```

![](bbox=[0.12, 0.35, 0.49, 0.67])

![](bbox=[0.53, 0.35, 0.88, 0.67])

With the CAMVID training data we get a void-colour, that represents “noclass”. We have to adapt our loss-function to deal with this void class. dataloaders.vocab = codes

We create a dictionary with dictionary comprehension, so we can look up a class index in the vocabulary and get back the corresponding label. (The enumerate function iterates over a list of values and returns each value along with an index.)

```
name2id = {v:k for k,v in enumerate(codes)}
```