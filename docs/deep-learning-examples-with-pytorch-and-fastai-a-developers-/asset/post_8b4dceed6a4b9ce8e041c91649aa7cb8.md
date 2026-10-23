
```
path = untar_data(URLs.PETS)
path_hr = path/'image_gen'
path_lr = path/'crappy_gan'
```

We use the parallel-function from the fastai package to increase speed on crapifying. If we run ??parallel we see that this is a function defined in the file torch_core.py. The document says this function Applies func in parallel to items, using n_workers.

And indeed, if we look at the source code, we see that it starts a ProcessPoolExecutor with a given number of workers (8 by default) and returns a list with progress bars indicating the status of each started worker.

```
def parallel(f, items, *args, n_workers=defaults.cpus, total=None, progress=True, **kwargs):
    "Applies `func` in parallel to `items`, using `n_workers`"
    with ProcessPoolExecutor(n_workers) as ex:
        r = ex.map(f, items, *args, **kwargs)
        if progress:
            if total is None: total = len(items)
            r = progress_bar(r, total=total, leave=False)
    return L(r)
```

```
items = get_image_files(path_hr)
parallel(Crappifier(path_lr, path_hr), items);
```

Now we can have a look at a random image and inspect both versions (the original and the crappified one). We see that the crappified image is a bit blurred, the resolution is smaller and there is a number printed on the image. We want to use our super-res GAN to clean those crappified images back to original quality.

```
bad_img = get_image_files(path_lr)
img1 = PILImage.create(items[0])
img2 = PILImage.create(bad_img[0])
img1.show(); img2.show(figsize=(4,4))
```

<matplotlib.axes._subplots.AxesSubplot at 0x7fe949b8c9d0>

![](img/d5454da46c702784893ef8b0b539e5b9_273_0.png)

## 18.2 Build our DataBlock

Now that we have our training dataset, we can go on building the datablock.
We are using ImageBlock to ImageBlock for our datablocks. The X values are the low resolution images and the y-values are the equivalent original high resolution images.

```
dblock = DataBlock(blocks=(ImageBlock, ImageBlock),
get_items=get_image_files,
get_y = lambda x: path_hr/x.name,
splitter=RandomSplitter(),
item_tfms=Resize(224),
batch_tfms=[*aug_transforms(max_zoom=2.),
→ Normalize.from_stats(*imagenet_stats)])
```

![](img/d5454da46c702784893ef8b0b539e5b9_273_1.png)

We are specifying the number of classes to 3 because we have colour images (*remember we need one channel for each colour!*). When we deal with grayscale images, we would use 1 channel. When we work on a classification problem, we need as many channels as we have classes.

```
def get_dls(bs:int, size:int):
    """Generates two `GAN` DataLoaders"""
    dblock = DataBlock(blocks=(ImageBlock, ImageBlock),
                       get_items=get_image_files,
                       get_y=lambda x: path_hr/x.name,
                       splitter=RandomSplitter(),
                       item_tfms=Resize(size),
                       batch_tfms=[*aug_transforms(max_zoom=2.),
                                   Normalize.from_stats(*imagenet_stats)])
    dls = dblock.dataloaders(path_lr, bs=bs)
    dls.c = 3  # For 3 channel image
    return dls
```

## 18.3 Pre-Trained Generator

The goal of this model will be to generate our “Super-Resolution” images (or to make an image look better).
First thing is grabbing the dataloaders – now we can specify the batch-size and the image-size with our get_dls-function.
If we show a sample batch, we see the crappified images along with our yvalues, are indeed the high resolution images.

```
dls_gen = get_dls(32, 128)
dls_gen.show_batch(max_n=4, figsize=(12, 8))
```

![](img/d5454da46c702784893ef8b0b539e5b9_275_0.png)

![](img/d5454da46c702784893ef8b0b539e5b9_275_1.png)

![](img/d5454da46c702784893ef8b0b539e5b9_275_2.png)

![](img/d5454da46c702784893ef8b0b539e5b9_275_3.png)

![](img/d5454da46c702784893ef8b0b539e5b9_275_4.png)

![](img/d5454da46c702784893ef8b0b539e5b9_275_5.png)

![](img/d5454da46c702784893ef8b0b539e5b9_275_6.png)

![](img/d5454da46c702784893ef8b0b539e5b9_275_7.png)

Now we define some of the hyper-parameters for our model. We choose some default values for weight-decay, y-range and the loss-function.
The generator itself is going to be a UNet-model based on a RESNET34 pretrained architecture.
We are just training for some epochs because the generator should be perfect from the start. The generator is just one part of this model.

```
wd, y_range, loss_gen = 1e-3, (-3., 3.), MSELossFlat()
bbone = resnet34
cfg = unet_config(blur=True, norm_type=NormType.Weight,
                  self_attention=True,
                  y_range=y_range)

def create_gen_learner(dls, backbone, loss_func, config):
    return unet_learner(dls, backbone, loss_func=loss_func, config=config)
```

```
loss_func=loss_func,
config=config)

learn_gen = create_gen_learner(dls_gen, bbone, loss_gen, cfg)
learn_gen.fit_one_cycle(2, pct_start=0.8, wd=wd)
```

| epoch | train_loss | valid_loss | time |
|-------|------------|------------|------|
| 0 | 0.056139 | 0.036853 | 01:05 |
| 1 | 0.016925 | 0.015305 | 01:02 |

learn_gen.unfreeze()
learn_gen.fit_one_cycle(3, slice(1e-6,1e-3), wd=wd)

| epoch | train_loss | valid_loss | time |
|-------|------------|------------|------|
| 0 | 0.015125 | 0.014412 | 01:07 |
| 1 | 0.011957 | 0.012065 | 01:07 |
| 2 | 0.010941 | 0.011944 | 01:07 |

learn_gen.show_results(max_n=4, figsize=(12,12))

## 18.4 Build the Critic

Now we are going to build the second part. The critic that will decide if it got a fake image or a real image. First we need the predictions. We put the images into our dataloader, do the prediction and then save them away.

```
name_gen = 'image_gen'
path_gen = path/name_gen
path_gen.mkdir(exist_ok=True)

def save_preds(dl, learn):
    "Save away predictions"
    names = dl.dataset.items
    preds,_ = learn.get_preds(dl=dl)
    for i,pred in enumerate(preds):
        dec = dl.after_batch.decode((TensorImage(pred[None],))[0][0]
```

### Input/Target/Prediction

![](img/d5454da46c702784893ef8b0b539e5b9_277_0.png)

![](img/d5454da46c702784893ef8b0b539e5b9_277_1.png)

![](img/d5454da46c702784893ef8b0b539e5b9_277_2.png)

![](img/d5454da46c702784893ef8b0b539e5b9_277_3.png)

![](img/d5454da46c702784893ef8b0b539e5b9_277_4.png)

![](img/d5454da46c702784893ef8b0b539e5b9_277_5.png)

![](img/d5454da46c702784893ef8b0b539e5b9_277_6.png)

![](img/d5454da46c702784893ef8b0b539e5b9_277_7.png)

![](img/d5454da46c702784893ef8b0b539e5b9_277_8.png)

```
arr = dec.numpy().transpose(1,2,0).astype(np.uint8)
Image.fromarray(arr).save(path_gen/names[i].name)
```

Now we want to get rid of the augmentations from the training dataloader.

We use the new function on the dataloader’s training data. This replaces the
current training data with an unshuffled one and applies some after-batch transforms.

```
dl = dls_gen.train.new(shuffle=False,
                       drop_last=False,
                       after_batch=[IntToFloatTensor,
                                    Normalize.from_stats(*imagenet_stats)])
```

Next we put this dataloader into our learner and grab some of the predictions.

```
preds, _ = learn_gen.get_preds(dl=dl)
```

If we take a look at a predicted image, we see that it’s a 3-channel image:

```
preds[0].shape torch.Size([3, 128, 128])
```

If we want to use the prediction from above and get an image, we can use decode on any of the transforms. Then we convert it into a numpy array and use transpose to get the different channels.

```
dec = dl.after_batch.decode((TensorImage(preds[0][None]),))[0][0]
arr = dec.numpy().transpose(1,2,0)
```

```
plt.imshow(arr.astype(np.uint8)) <matplotlib.image.AxesImage at 0x7fe927ff1510>
```

![](img/d5454da46c702784893ef8b0b539e5b9_278_0.png)

Now we save them away:

```
save_preds(dl, learn_gen)
```

## 18.5 Training of the Critic

Now we can build and train our critic model architecture.

```
path_gen; name_gen
'image_gen'

# We have to do this because of a bug for right now
path_g = get_image_files(path/name_gen)
path_i = get_image_files(path/"images_gan")
fnames = path_g + path_i
```

We are working on the dataset-level. We are getting our images from the paths and use a RandomSplitter for doing our training-/validation-set split. Our discriminator is a binary classifier - either true image or fake (generated) image. On top of this we build the dataloaders.

```
def get_crit_dls(fnames, bs:int, size:int):
    """Generate two `Critic` DataLoaders"""
    splits = RandomSplitter(0.1)(fnames)
    datasource = Datasets(fnames,
                          tfms=[[PILImage.create],
                                [parent_label, Categorize]],
                          splits=splits)
    tfms = [ToTensor(),
            Resize(size)]
    gpu_tfms = [IntToFloatTensor(),
                Normalize.from_stats(*imagenet_stats)]
    return datasource.dataloaders(bs=bs,
                                  after_item=tfms,
                                  after_batch=gpu_tfms)
```

dataloaders_critic = get_crit_dls(fnames, bs=32, size=128)
Let’s inspect a random batch:
dataloaders_critic.show_batch()
We are using BCEWithLogitsLoss loss-function for training our model.

Now it’s time to create the learner object. This will be a gan_critic model
