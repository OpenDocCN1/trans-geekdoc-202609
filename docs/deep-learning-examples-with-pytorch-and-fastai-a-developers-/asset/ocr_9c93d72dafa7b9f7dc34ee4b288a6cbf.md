![](bbox=[0.12, 0.09, 0.7, 0.39])

# Channel 0 Image 0: 128 X 63px

![](bbox=[0.15, 0.42, 0.72, 0.71])

```
get_y = lambda x: x.name[0]
```

Now we can build a DataBlock with an audio module.

```
aud_digit = DataBlock(blocks=(AudioBlock, CategoryBlock),
get_items=get_audio_files,
splitter=RandomSplitter(),
item_tfms = item_tfms,
get_y=get_y)
```