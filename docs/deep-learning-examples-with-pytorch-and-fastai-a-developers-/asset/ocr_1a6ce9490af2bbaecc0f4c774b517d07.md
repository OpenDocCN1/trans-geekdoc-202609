course for any competition like kaggle, your results could benefit a lot from this technique.

# Chapter 7

# FastAI – A Glance on the internal API

This chapter focuses on the internals of the fastai API. We will have a look at an example on how to use the most basic fastai api on the whole processing pipeline. We will do this with Points objects because this is a very simple object.

```
from fastai.vision.all import *
```

First we are inspecting the PILImage class and will rebuild it from scratch. We can easily download an image with the download_url-method, providing just the url to the image.

We are using an image of a dog from wikimedia.

```
img_url = 'https://upload.wikimedia.org/wikipedia/commons^ d/d6/Thai-Ridgeback.jpg'
img_path = Path('images/dog.jpg')
download_url(img_url, img_path)
```

# 7.1 The PILImage-Class

Now going back to PILImage-class. What does this class contain? Let’s open the code: ??PILImage.

```
??PILImage
class PILImage(PILBase): pass
```

Wow. Not too much code inside this class. Indeed PILImage is just a wrapper