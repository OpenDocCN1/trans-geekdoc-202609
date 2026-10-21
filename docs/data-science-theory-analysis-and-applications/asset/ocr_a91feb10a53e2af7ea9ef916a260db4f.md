# 11.3.4 Pixel Density

Density features are calculated by applying a uniform grid over document images (see Figure 11.5). This consists of dividing the document images into a predefined number of cells having the same size as much as possible. For each cell, the pixel density corresponds to the ratio between the number of text pixels and the cell size.

Density = \frac{Number of text pixels}{Number of pixels in the cell} \quad (11.9)

In this respect, each cell is substituted by the density value. Then, the size of the density feature vector is equal to the number of cells.

# 11.3.5 Run Length Feature

RLF has been introduced for writer identification to approximate the shape of handwritten text [21]. Basically, RLF seeks text and background pixel sequences along the horizontal, vertical, and diagonal directions. For each direction, a (N×M) matrix is calculated, where N is the number of pixel values and M is the maximum possible run length in the corresponding image. Presently, all document images undergo a binarization step using Otsu method [22]. Thereby, P (N×M) is a two-line matrix. Figure 11.6 shows an example of an RLF calculation.

To get the final feature vector, matrices are reshaped into normalized vectors that are subsequently concatenated to form the RLF vector.

![](bbox=[0.12, 0.55, 0.85, 0.88])

FIGURE 11.5 Pixel density features calculation using a uniform grid.