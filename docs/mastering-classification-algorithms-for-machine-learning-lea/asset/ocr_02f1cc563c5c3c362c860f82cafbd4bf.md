Refer to Figure Annexure 3.3:

![](bbox=[0.289, 0.126, 0.71, 0.532])

# # Compressing color images

Now, we walk through the process of compressing color images. The process would be the same except that we have three channels per pixel in color images - one for Red, one for Green, and one for Blue.

The image used for this demonstration can be found at this **link**.¹

Let us load the image and visualize it.

```
imageArray = np.array(Image.open('./Temple.jpeg'))

imageArray.shape

(4032, 3024, 3)

# Normalize the intensity values in each pixel
image = imageArray / 255
```

> ¹ https://drive.google.com/file/d/1rqGt1XnuxzBfLse0ZXMC7RTq9EY0uG5/view