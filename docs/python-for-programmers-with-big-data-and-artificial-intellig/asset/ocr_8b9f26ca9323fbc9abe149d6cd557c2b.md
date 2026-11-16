We can confirm the number of samples and features (per sample) by looking at the data array’s shape attribute, which shows that there are 1797 rows (samples) and 64 columns (features):

lick here to view code image

```
```
In [5]: digits.data.shape
Out[5]: (1797, 64)
```
```

You can confirm that the number of target values matches the number of samples by looking at the target array’s shape:

lick here to view code image

```
```
In [6]: digits.target.shape
Out[6]: (1797,)
```
```

# A Sample Digit Image

Each image is two-dimensional—it has a width and a height in pixels. The Bunch object returned by load_digits contains an images attribute—an array in which each element is a two-dimensional 8-by-8 array representing a digit image’s pixel intensities. Though the original dataset represents each pixel as an integer value from 0–16, scikit-learn stores these values as floating-point values (NumPy type float64). For example, here’s the two-dimensional array representing the sample image at index 13:

lick here to view code image

```
```
In [7]: digits.images[13]
Out[7]:
array([[ 0.,  2.,  9., 15., 14.,  9.,  3.,  0.],
       [ 0.,  4., 13.,  8.,  9., 16.,  8.,  0.],
       [ 0.,  0.,  0.,  6., 14., 15.,  3.,  0.],
       [ 0.,  0.,  0., 11., 14.,  2.,  0.,  0.],
       [ 0.,  0.,  0.,  2., 15., 11.,  0.,  0.],
       [ 0.,  0.,  0.,  0.,  2., 15.,  4.,  0.],
       [ 0.,  1.,  5.,  6., 13., 16.,  6.,  0.],
       [ 0.,  2., 12., 12., 13., 11.,  0.,  0.]])
```
```

and here’s the image represented by this two-dimensional array—we’ll soon show the code for displaying this image: