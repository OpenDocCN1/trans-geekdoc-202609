```
```python
pat = r'/([^/]+)_\d+.*'

batch_tfms = [*aug_transforms(size=224, max_warp=0),
Normalize.from_stats(*imagenet_stats)]
item_tfms = RandomResizedCrop(460, min_scale=0.75,
    ratio=(1.,1.))
bs=32

pets = DataBlock(blocks=(ImageBlock, CategoryBlock),
get_items=get_image_files,
splitter=RandomSplitter(),
get_y=RegexLabeller(pat = r'/([^/]+)_\d+.*'), item_tfms=item_tfms,
batch_tfms=batch_tfms)

dls = pets.dataloaders(path, bs=bs)
dls.show_batch(max_n=9, figsize=(6,7))
```
```

![](bbox=[0.127, 0.443, 0.646, 0.899])