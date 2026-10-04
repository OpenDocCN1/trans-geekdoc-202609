180 T. P. Fowdur, L. Babooram, M. N-U-D-Ibn Nazir Rosun and M. Indoonundon

Hence,

```
O = \begin{pmatrix} -1 & -6 & -2 & 10 \ 0 & -1 & 4 & 9 \ 11 & -4 & -3 & 9 \ 12 & -4 & -6 & 4 \end{pmatrix}
```

Lower pixel values represent darker pixels in the image. The second column of O has a large number of low pixel values which indicate the presence of vertical edges.

In MATLAB, CNNs can be trained using the trainNetwork function which is available from the Deep Learning Toolbox [42]. The syntax of the function for training a CNN is as follows:

```
net= trainNetwork(images,layers,options)
```

The input to the function is described below:

+   * images: Image data in a datastore format.
"* layers: Layers to be used in CNN.
"* options: Training parameters.

The function outputs net which is the CNN in a SeriesNetwork object format.

The CNN can then classify new data using MATLAB's classify function from the Deep Learning Toolbox. The syntax of the function is as follows:

```
YPred= classify(net,imds)
```

The input to the function is described below:

+   * net: Trained CNN.
"* imds: Predicted class label."

The function outputs YPred which is the CNN in a SeriesNetwork object format.

A MATLAB simulation in which a CNN is trained to identify handwritten digits is demonstrated below [48]. The Digit Dataset from the Deep Learning Toolbox, containing 10,000 synthetic grayscale images of handwritten digits [49], is used for this demonstration. The dataset is loaded to the workspace by using the codes in Listing 3.33: