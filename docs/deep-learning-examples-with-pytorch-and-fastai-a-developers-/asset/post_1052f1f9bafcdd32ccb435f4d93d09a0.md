
We see exactly the same pattern on the points, marking the corners of the image – rescaled. Next we scale back the coordinates – along with our encoder/decoder structure.

```python
def _myUnscale_pnts(y, sz):
    return TensorPoint((y+1)*tensor(sz).float()/2,
                       img_size=sz)
```

If we decode the points we should get our initial coordinates!

```python
unscaled_tps = [_myUnscale_pnts(tp, 224) for tp in scaled_tps]
unscaled_tps
[TensorPoint([0., 0.]), TensorPoint([0., 414.]), TensorPoint([601., 0.]), TensorPoint([601., 414.])]
```

Looks straight forward! Nice! Now we can transform our points on a new image, have it cropped, resized, rotated, etc.

This is rather the same as the original code from the fastai library:

```python
def _scale_pnts(y, sz, do_scale=True, y_first=False):
    if y_first:
        y = y.flip(1)
    res = y * 2/tensor(sz).float() if do_scale else y
    return TensorPoint(res, img_size=sz)
```

```python
def _unscale_pnts(y, sz):
    return TensorPoint((y+1) * tensor(sz).float()/2, img_size=sz)
```

```python
class PointScaler(Transform):
    "Scale a tensor representing points"
    order = 1

    def __init__(self, do_scale=True, y_first=False):
        self.do_scale, self.y_first = do_scale, y_first

    def _grab_sz(self, x):
        self.sz = [x.shape[-1], x.shape[-2]] if isinstance(x, Tensor) else x.size
        return x

    def _get_sz(self, x):
        sz = x.get_meta('img_size')
        assert sz is not None or self.sz is not None, \
            "Size could not be inferred, pass it in the init of your TensorPoint with `img_size=...`"
        return self.sz if sz is None else sz
```

```python
def setup(self, dl):
    its = dl.do_item(0)
    for t in its:
        if isinstance(t, TensorPoint): self.c = t.numel()

def encodes(self, x:(PILBase,TensorImageBase)): return self._grab_sz(x)
def decodes(self, x:(PILBase,TensorImageBase)): return self._grab_sz(x)

def encodes(self, x:TensorPoint):
    return _scale_pnts(x, self._get_sz(x), self.do_scale, self.y_first)
def decodes(self, x:TensorPoint):
    return _unscale_pnts(x.view(-1, 2), self._get_sz(x))
```

Now we can make a DataBlock with our implemented code. We follow along the usual pattern: First call create, second do the scaling.

my_point_block = TransformBlock(type_tfms=myTensorPointCreate,
item_tfms=myPointScaler) If we use the @patch decorator, we can use any transform on our tensor-points.

```python
def _neg_axis(x, axis):
    x[..., axis] = -x[..., axis]
    return x
```

```python
@patch
def flip_lr(x: TensorPoint): return TensorPoint(_neg_axis(x.clone(), 0))
```

We have seen how to explore the internals of fastai. You could do this with any framework. Try replicating the implementation. This way you learn very well how the framework is built.

## Chapter 8
### Image Segmentation

Image segmentation masks areas of images and classifies them. You want to use image segmentation for example to mark special areas on medical image data like xrays, ct- or mrt-images.
Here we have an image of the brain with some regions annotated:

In this chapter we will be using the CAMVID dataset that consists of traffic images. If you want to implement autonomous driving, your algorithm has to classify the different objects in traffic. We then create what is called a *mask* to mark the pixels that belong to a certain class.

The image on the left shows a plane and the image on the right shows the mask that is overlaid.
*Image Sources:*
- https://public.md.ai/hub/projects/public
- https://www.researchgate.net/profile/Anna_Boers/publication/235885350/figure/fig2/AS:299772243136518@1448482680597/Example-of-incorrect-automated-segmentation-due-to-hemorrhage-and-erroneous-midline.png
- https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2018/11/26/semantic-segmentation-1.jpg

### 8.1 Let’s get the CAMVID Dataset

The CAMVID trainingdata set classifies nearly 40 different classes in images. It is also available from the URLs class of the fastai library. The images within the dataset were taken by dashcams of cars.

![](img/d5454da46c702784893ef8b0b539e5b9_104_0.png)

![](img/d5454da46c702784893ef8b0b539e5b9_105_0.png)

First we have to download the dataset. We see that the filenames for validation are listed in a file called valid.txt (one filename per line).

```python
from fastai.basics import *
from fastai.vision.all import *
from fastai.callback.all import *

path = untar_data(URLs.CAMVID)
valid_filenames = (path/"valid.txt").read().split('\n')
```

![](img/d5454da46c702784893ef8b0b539e5b9_105_1.png)

Now grab the paths to the images and the labels folders.

```python
path_imgs = path/'images'
path_lbls = path/'labels'
```

Now we can have a look at an image to check that everything works fine. With our variables containing the paths to the images and the labels, we can openly read the images with the get_image_files method.

```python
fnames = get_image_files(path_imgs)
labels = get_image_files(path_lbls)
```

We also run the get_image_files method for the labels. The labels themselves are just tables, containing a number for each pixel that declares the class the certain pixel belongs to. These tables are then often saved as png or jpg images in order to use the compression of these filetypes.

Now we can grab a filename from our list of our image files. Create a PILImage from it and call the show method on the image.

```python
img_file_name = fnames[1]
img = PILImage.create(img_file_name)
img.show()
```

```
<matplotlib.axes._subplots.AxesSubplot at 0x7efbffb67c10>
```

Now with the CAMVID dataset we want to segment this image. Our algorithm should classify each pixel. Afterwards we can say, *this is a pedestrian, this is a car, . . . . etc.*

We can also show the mask for the training images on the CAMVID training data.

We have to look into the labels folder and search for a file with the same filename like our image but with a _P-suffix in the filename. So let’s build a lambda function that does this job for us. We use the stem and suffix functions from python’s pathlib library (https://docs.python.org/3/library/pathlib.html).

The stem-function returns all characters before the .-sign and the suffix returns all characters after .-sign.

![](img/d5454da46c702784893ef8b0b539e5b9_107_0.png)

```python
get_mask = lambda i: path/'labels/'f'{i.stem}_P{i.suffix}'
```

The masks are of type PILMask. When we show our mask we can set a value for alpha. We use 1 as we do not want to overlay on an existing image for now.

What does this mask file contain? The mask just contains the values of the class of each pixel it belongs to. E.g. we have an 4x4 image. The mask file would look like this:

```
0000
0100
0110
0000
```

This mask only contains one classtype that is marked with 1 while the 0 just represents the background. This can be any type of object you want to segment on.

If we now call .show on this mask file, the fastai library automatically generates a colour scheme that suits our classes.

```python
mask = PILMask.create(get_mask(img_file_name))
mask.show(figsize=(5,5), alpha=1)
<matplotlib.axes._subplots.AxesSubplot at 0x7efbffaba4d0>
```

The image above shows this pixel map. It is the same as the one for our

![](img/d5454da46c702784893ef8b0b539e5b9_108_0.png)

simple 4x4 image – just larger and contains more classes. We can even have a look at the raw data of the mask. If we print the mask as a tensor we can identify the values for the different classes. E.g. the 4 code represents a house (in the upper left corner of the image), the 26 are trees (in the upper right of the image), etc.

tensor(mask)

```
tensor([[ 4, 4, 4, ..., 26, 26, 26], [ 4, 4, 4, ..., 26, 26, 26], [ 4, 4, 4, ..., 26, 26, 26], ..., [17, 17, 17, ..., 17, 17, 17], [17, 17, 17, ..., 17, 17, 17], [17, 17, 17, ..., 17, 17, 17]], dtype=torch.uint8)
```

With the CAMVID dataset we get a file called codes.txt that contains the labels for all of the codes used in the masks.

```python
codes = np.loadtxt(path/'codes.txt', dtype=str)
```

codes

```
array(['Animal', 'Archway', 'Bicyclist', 'Bridge', 'Building', 'Car', 'CartLuggagePram', 'Child', 'Column_Pole', 'Fence', 'LaneMkgsDriv', 'LaneMkgsNonDriv', 'Misc_Text', 'MotorcycleScooter', 'OtherMoving', 'ParkingBlock', 'Pedestrian', 'Road', 'RoadShoulder', 'Sidewalk', 'SignSymbol', 'Sky', 'SUVPickupTruck', 'TrafficCone', 'TrafficLight', 'Train', 'Tree', 'Truck_Bus', 'Tunnel', 'VegetationMisc', 'Void', 'Wall'],
```
