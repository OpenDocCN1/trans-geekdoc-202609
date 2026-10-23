```
datasource = Datasets(train_images+test_images,
tfms=[[PILImage.create],
[parent_label, Categorize]], splits=split_list)
show_at(datasource.train, 1)
<matplotlib.axes._subplots.AxesSubplot at 0x7f7ca41468d0>
```

![](bbox=[0.12, 0.21, 0.56, 0.45])

datasource.n_subsets
3
Now we can to create the dataloaders.

```
dataloaders = datasource.dataloaders(bs=bs,
after_item=item_tfms, after_batch=batch_tmfs)
```

```
dataloaders.show_batch(figsize=(8,8))
```