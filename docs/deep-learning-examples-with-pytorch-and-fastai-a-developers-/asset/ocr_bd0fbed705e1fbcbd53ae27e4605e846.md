(n + m - 1)
m (19.2)
When we do the math we get:
(16) 16! 2! = 120(19.3)2 = (16 - 2)! ·

We want to use the PETS dataset again for our Siamese Twin Data experiment.

```
from fastai.vision.all import *
src = untar_data(URLs.PETS)/'images'
We grab all the file names.
items = get_image_files(src)
```

Next step is preparing the dataset. This time we are using just the low-level api from fastai. The first part is building the transforms. We want to open the image from a given filename and resize it.

```
def resized_image(fn:Path, sz=128):
"""Opens an image from `fn` and resizes it to `sz`""" x =
Image.open(fn).convert('RGB').resize((sz,sz)) return
tensor(array(x)).permute(2,0,1).float()/255.
```

Now let’s get two random images (that we know are different).

```
img1 = resized_image(items[0], 448)
img2 = resized_image(items[1], 448)
```

We do not have a custom image-type for this kind of problem. Therefore we create a new class called TitledImage that uses the function show_titled_image from the fastai library to print the image aside with a given title.

```
class TitledImage(fastuple):
def show(self, ctx=None, **kwargs):
show_titled_image(self, ctx=ctx, **kwargs)
TitledImage(img1, 'Test-Title').show()
```

Now we go on and use this idea with our Siamese problem. We create a class SiamesePair that concatenates the two images together and puts some title onto the new image.