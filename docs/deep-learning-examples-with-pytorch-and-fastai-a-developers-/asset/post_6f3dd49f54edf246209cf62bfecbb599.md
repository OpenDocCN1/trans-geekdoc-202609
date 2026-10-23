
![](img/d5454da46c702784893ef8b0b539e5b9_202_0.png)

For more information on the clamp see the pytorch document: https://pytorch.org/docs/stable/torch.html

The encoding function is the thing we apply when creating our items.

```python
class ClampBatch(Transform):
    """Clamp points to a minimum and maximum in a batch""" order = 4
def __init__(self, min=-1, max=1, **kwargs):
```

```
(#8936) [Path('cat-dataset/00000975_025.jpg'),Path('catdataset/00000102_004.jpg'),Path('cat-dataset/00001468_016.jpg'),Path('cat-dataset/00000891_025.jpg'),Path('cat-dataset/00000167_010.jpg'),Path('catdataset/00001087_025.jpg'),Path('cat-dataset/00000132_029.jpg'),Path('catdataset/00001021_008.jpg'),Path('cat-dataset/00000586_014.jpg'),Path('catdataset/00000127_021.jpg')...]
```

With how our get_y is implemented, we hand in a base path of ”. Let’s look at a datablock.summary() output now to see what’s going on in our Pipeline.

This helps us understand how our augmentation is doing.
datablock.summary(")

Setting-up type transforms pipelines Collecting items from Found 8936 items 2 datasets of sizes 7149,1787 Setting up Pipeline: PILBase.create Setting up Pipeline: get_y -> TensorPoint.create

Building one sample Pipeline: dataset/00001111_004.jpg applying

PILBase.create starting from cat-dataset/00001111_004.jpg applying PILBase.create gives PILImage mode=RGB size=500x451 Pipeline: get_y -> TensorPoint.create starting from cat-dataset/00001111_004.jpg applying get_y gives Tensor of size 9x2 applying TensorPoint.create gives TensorPoint of size 9x2

Final sample: (PILImage mode=RGB size=500x451, TensorPoint([[164., 96.], [203., 100.], [173., 134.], [153., 79.], [147., 18.], [185., 48.], [215., 52.], [242., 23.], [236., 89.]]))

Setting up after_item: Pipeline: PointScaler -> Resize -> ToTensor Setting up before_batch: Pipeline: Setting up after_batch: Pipeline: ClampBatch -> IntToFloatTensor -> AffineCoordTfm

Building one batch Applying item_tfms to the first sample: Pipeline: PointScaler -> Resize -> ToTensor starting from (PILImage mode=RGB size=500x451, TensorPoint of size 9x2) applying PointScaler gives (PILImage mode=RGB size=500x451, TensorPoint of size 9x2) applying Resize gives (PILImage mode=RGB size=448x448, TensorPoint of size 9x2) applying ToTensor gives (TensorImage of size 3x448x448, TensorPoint of

size 9x2)

Adding the next 3 samples
No before_batch transform to apply
Collating items in a batch

Applying batch_tfms to the batch built Pipeline: ClampBatch -> IntToFloatTensor -> AffineCoordTfm starting from (TensorImage of size 4x3x448x448, TensorPoint of size 4x9x2) applying ClampBatch gives (TensorImage of size 4x3x448x448, TensorPoint of size 4x9x2) applying IntToFloatTensor gives (TensorImage of size 4x3x448x448, TensorPoint of size 4x9x2) applying AffineCoordTfm gives (TensorImage of size 4x3x448x448, TensorPoint of size 4x9x2)

This summary shows exactly what is happening within our model. When anything goes wrong while applying the transforms, we can go through and debug our model to adjust the transforms.

By now we can be sure that the pipeline works (at least for one demo example): Building one sample
Pipeline: PILBase.create
starting from
cat-dataset/00000169_028.jpg
applying PILBase.create gives
PILImage mode=RGB size=333x500
Pipeline: get_y -> TensorPoint.create
starting from
cat-dataset/00000169_028.jpg
applying get_y gives
Tensor of size 9x2
applying TensorPoint.create gives

TensorPoint of size 9x2
So we can create our dataloaders and have a look at a sample batch.

```python
dataloaders = datablock.dataloaders('.', path='', bs=bs)
dataloaders.show_batch()
```

![](img/d5454da46c702784893ef8b0b539e5b9_206_0.png)
![](img/d5454da46c702784893ef8b0b539e5b9_206_1.png)
![](img/d5454da46c702784893ef8b0b539e5b9_206_2.png)
![](img/d5454da46c702784893ef8b0b539e5b9_206_3.png)
![](img/d5454da46c702784893ef8b0b539e5b9_206_4.png)
![](img/d5454da46c702784893ef8b0b539e5b9_206_5.png)
![](img/d5454da46c702784893ef8b0b539e5b9_206_6.png)
![](img/d5454da46c702784893ef8b0b539e5b9_206_7.png)
![](img/d5454da46c702784893ef8b0b539e5b9_206_8.png)

The sample batch looks good.
Now we set the c (classes) property of our dataloaders so we can create the model’s output easier.

```python
dataloaders.c = dataloaders.train.after_item.c
dataloaders.c
18
```

This means our model generates 18 classes – remember we want to regress on 9 different keypoints. This means we have to generate 9 pairs of keypoint coordinates (or 18 single values).

Now we can build our model. We want to use a custom model and a head for regression.

If we know about our outputs and inputs we can make use of the functions create_body and create_head. The create_body function chops off the top layer of the pre-trained model. The create_head function creates a custom fastai head-layer.

- Which input/output layers do we need for our model:
  - output-layer: 18 (as stated before, 9 tuples of coordinates)
  - input-layer: 1024 filter (2-times of the last layer’s dimension of the ResNet18 model because our custom fastai head layer contains two parallel layers.

```python
body = create_body(resnet18, pretrained=True)
head = create_head(nf=1024, n_out=18)
```

Now we can analyze the head as well as the body.

```python
body[-1][-1]
```

```
BasicBlock( (conv1):
1), padding=(1, 1),
05, momentum=0.1, ReLU(inplace=True) stride=(1, 1), padding=(1, 1),
bias=False) eps=1e-05, momentum=0.1, affine=True,
track_running_stats=True) ) Conv2d(512, bias=False) affine=True, (conv2):
Conv2d(512, 512, kernel_size=(3, 3), stride=(1, (bn1): BatchNorm2d(512,
eps=1etrack_running_stats=True) (relu): 512, kernel_size=(3, 3), (bn2):
BatchNorm2d(512,
```

head

```
Sequential( (0): AdaptiveConcatPool2d( (ap):
AdaptiveAvgPool2d(output_size=1) (mp):
AdaptiveMaxPool2d(output_size=1) ) (1): Flatten(full=False) (2):
BatchNorm1d(1024, eps=1e-05, momentum=0.1, affine=True,
track_running_stats=True) (3): Dropout(p=0.25, inplace=False) (4):
Linear(in_features=1024, out_features=512, bias=False) (5):
ReLU(inplace=True) (6): BatchNorm1d(512, eps=1e-05, momentum=0.1,
affine=True, track_running_stats=True) (7): Dropout(p=0.5, inplace=False)
```

```python
(8): Linear(in_features=512, out_features=18, bias=False)
```

Here we see the first layer of the fastai header that contains two parallel pooling layers. This means that the output of the model goes to both of them at once. If we look at the last Linear-layer we can see that this has 512 inputs. Therefore we have to double them and we need a head with 1024 input nodes.

Now we concatenate the body and the head.

```python
model_arch = nn.Sequential(body, head)
```

To split this model we use the default split-method from pytorch this time. We have to make sure that we really can split the model, so we have to index into it. Because we had wrapped the whole model into a Sequential model we have two indices. The first index takes 0 or 1 for body or head and second index is used to address a specific layer within that part of the whole model.

```python
def _resnet_split(m):
    return L(m[0][:6], m[0][6:], m[1:]).map(params)
model_arch[1:]

Sequential (1): Sequential (0): AdaptiveConcatPool2d( (ap):
AdaptiveAvgPool2d(output_size=1) (mp):
AdaptiveMaxPool2d(output_size=1) ) (1): Flatten(full=False) (2):
BatchNorm1d(1024, eps=1e-05, momentum=0.1, affine=True,
track_running_stats=True) (3): Dropout(p=0.25, inplace=False) (4):
Linear(in_features=1024, out_features=512, bias=False) (5):
ReLU(inplace=True) (6): BatchNorm1d(512, eps=1e-05, momentum=0.1,
affine=True, track_running_stats=True) (7): Dropout(p=0.5, inplace=False)
(8): Linear(in_features=512, out_features=18, bias=False) ) )
```

The slicing-index [1:] grabs the head of the model. Now we can freeze the body for training. We want to initialize our model with kaiming_normal (https://pytorch.org/docs/stable/nn.init.html).

We will use MSELossFlat as our loss-function, ranger and optimizer and start training.

```python
dataloaders.train.dataset[:10]
```
