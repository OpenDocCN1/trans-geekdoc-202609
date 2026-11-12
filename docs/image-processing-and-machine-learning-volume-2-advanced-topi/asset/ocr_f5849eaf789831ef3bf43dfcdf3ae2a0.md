![](bbox=[0.172, 0.123, 0.453, 0.273])

![](bbox=[0.528, 0.123, 0.831, 0.273])

![](bbox=[0.172, 0.306, 0.453, 0.456])

![](bbox=[0.528, 0.306, 0.831, 0.456])

(a)

(b)

(c)

(d)

FIGURE 1.21 Morphological operations performed on grayscale images. (a) Original image, (b) eroded image, (c) dilated image, and (d) morphological gradient.

the valleys, if they are smaller than the structure, will be filled. Figure 1.22e shows the result of the closing operation.

Contrary to the opening operation, the closing operation allows the cancelation of small, obscured values present in the image, which are smaller than the size of the used reference structure, leaving the other intensity values without significant change.

Because the opening operation suppresses bright details smaller than the reference structure and the closing operation removes dark artifacts, both operations are used in combination to smooth and denoise images.

The filter product of the combination of the opening and closing operations is called the opening and closing filter; such a filter has the ability to simultaneously remove bright and dark artifacts from images, similar to salt and pepper noise. In the filter operation, the grayscale image is opened (removing bright artifacts), and the result of this process is then closed (removing dark artifacts). Figure 1.23 shows the effect of the opening and closing operations on a grayscale image, to which salt and pepper-type noise was added. Likewise, the result of using the opening and closing filters is also shown.

Another way to use the opening and closing filters is to apply them repetitively, varying the size of the reference structure in each iteration.