# 36 | Scientific programming with Python

Hence, this operation to find the red spot is really a convolution over space and addition over channel (convadd). This operation is illustrated in Fig. 2.10. This operation has

![](bbox=[0.203, 0.163, 0.763, 0.003385])

**Fig. 2.10** illustration of 2-dimensional convolutions with adding of channels. In this example different $2 \times 2$ filters are applied over the color channel and the corresponding elements are multiplied and then added up. The filter is then moved by an amount of pixels specified by the stride until the image was covered.

become the workforce in computer vision with convolutional neural networks that we explore later in this book.

It is useful to mention that applications of convolutions are sometimes modified slightly to accommodate the preservation of the signal size. We have seen that the output of a convolution has a reduced size that depends on the size of the filter. Sometimes we want the output image to be the same size. We can achieve this by simply adding appropriate columns and rows to the input image. This is called padding, and padding with zeros is a common choice. Of course, this method can introduce some artifacts that might not be desirable.

Finally, it is interesting to note that edge detectors are an important part of computer vision systems. For example, we can apply to an image $2 \times 2$ filter with $1s$ on the left column and $-1s$ on the right column,

> $$\begin{pmatrix} -1 & 1 \ -1 & 1 \end{pmatrix}$

For example, if we have an image with two color like

> $$\begin{pmatrix} 0 & 0 & 1 \ 0 & 1 & 1 \ 0 & 0 & 1 \ 0 & 1 & 1 \end{pmatrix}$

then the filtered image would be

> $$\begin{pmatrix} 0 & 0 & 2 \ 0 & 2 & 0 \ 0 & 2 & 0 \endend{pmatrix}$