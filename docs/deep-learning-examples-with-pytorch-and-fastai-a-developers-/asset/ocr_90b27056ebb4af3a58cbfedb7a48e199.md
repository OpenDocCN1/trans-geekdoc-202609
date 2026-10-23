![](bbox=[0.115, 0.08, 0.885, 0.71])

E.g. when doing handwritten digit classification, you could use this code:

```
mnist = DataBlock(type=(PILImageBW, Category),
get_items=get_image_files,
splitter=GrandparentSplitter(), get_y=parent_label)

databunch = mnist.databunch(untar_data(URLs.MNIST_TINY))
databunch,show_batch(max_n=9, figsize=(4,4))
```