# 14.3.3.1 Extracting Local Visual Words

Converting an image into its local-word form is the one black box that we won't open. We will simply use a routine out of OpenCV, an image processing library, called SIFT_create, that can pull out interesting pieces of an image. Here, interesting refers to things like the orientations of edges and the corners of shapes in the image. Every image gets converted to a table of local words. Each image's table has the same number of columns but its own number of rows. Some images have more remarkable characteristics that need to be described using more rows. Graphically, this looks like Figure 14.3.

![](bbox=[0.15, 0.3, 0.9, 0.62])

Figure 14.3 Extracting local visual words from the images.

We'll make use of a few helper functions to locate the image files on our hard drive and to extract the local words from each image.

```
In [26]:

def img_to_local_words(img):
    ' heavy lifting of creating local visual words from image '
    sift = cv2.xfeatures2d.SIFT_create()
    key_points, descriptors = sift.detectAndCompute(img, None)
    return descriptors

def id_to_path(img_id):
    ' helper to get file location '
    cat, num = img_id
    return osp.join(objcat_path, cat, "image_{:04d}.jpg".format(num))
```