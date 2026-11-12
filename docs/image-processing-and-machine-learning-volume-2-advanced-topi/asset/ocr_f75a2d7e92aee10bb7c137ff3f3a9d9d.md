# 2.13 Spatial Processing in Color Images

The essential feature of the linear transformation operations discussed in the previous section was that the new pixel value finally calculated depends exclusively on the original pixel value of each plane and is located in the same position in the planes of the new image. Although it is possible to perform many effects on images using pixel operations, there are conditions under which it is not possible to use them to generate certain effects, such as in the case of image smoothing or edge detection. Spatial processing of color images can be considered as an operation where the newly computed pixel depends not only on the original pixel but also on other pixels that are in a given neighborhood relative to it. Evidently, this processing considers that the operations are carried out independently on each color plane that defines the image. Figure 2.28 shows the process of a special operation on a color image.

This type of processing is closely related to the operations from Chapter 2, except that in the case of color images, the processing is performed on each color plane. Considering the above, most of the operations explained in Chapter 2, such as filtering, can be applied to this type of image. Therefore, only those operations that, due to their importance, are considered the most common will be discussed.

# 2.13.1 Color Image Smoothing

As has been discussed in Chapter 2, in an intensity image or a color image, regions or pixels can experiment with an abrupt change locally in the value

![](bbox=[0.225, 0.615, 0.775, 0.895])

FIGURE 2.28 Spatial processing of a color image. The processing is performed using a coefficient matrix that defines a processing region that operates on each color plane.