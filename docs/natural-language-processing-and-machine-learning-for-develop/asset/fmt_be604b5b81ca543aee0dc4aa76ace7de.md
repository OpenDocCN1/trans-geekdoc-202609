
{images': array(      \[\[\[0.,   0.,   5., ...,       1.,    0.,   0.\],        \[0.,   0.,  13., ...,  15.,   5.,   0.\],        \[0.,   3.,  15., ...,  11.,   8.,   0.\],        ...,        \[0.,   4.,  11., ...,  12.,   7.,   0.\],        \[0.,   2.,  14., ...,  12.,   0.,   0.\],        \[0.,   0.,   6., ...,   0.,   0.,   0.\]\]), 'target': array(\[0, 1, 2, ..., 8, 9, 8\]), 'frame': None, 'feature_names': \['pixel\_0\_0', 'pixel\_0\_1', 'pixel\_0\_2', 'pixel\_0\_3', 'pixel\_0\_4', 'pixel\_0\_5', 'pixel\_0\_6', 'pixel\_0\_7', 'pixel\_1\_0', 'pixel\_1\_1', 'pixel\_1\_2', 'pixel\_1\_3', 'pixel\_1\_4', 'pixel\_1\_5', 'pixel\_1\_6', 'pixel\_1\_7', 'pixel\_2\_0', 'pixel\_2\_1', 'pixel\_2\_2', 'pixel\_2\_3', 'pixel\_2\_4', 'pixel\_2\_5', 'pixel\_2\_6', 'pixel\_2\_7', 'pixel\_3\_0', 'pixel\_3\_1', 'pixel\_3\_2', 'pixel\_3\_3', 'pixel\_3\_4', 'pixel\_3\_5', 'pixel\_3\_6', 'pixel\_3\_7', 'pixel\_4\_0', 'pixel\_4\_1', 'pixel\_4\_2', 'pixel\_4\_3', 'pixel\_4\_4', 'pixel\_4\_5', 'pixel\_4\_6', 'pixel\_4\_7', 'pixel\_5\_0', 'pixel\_5\_1', 'pixel\_5\_2', 'pixel\_5\_3', 'pixel\_5\_4', 'pixel\_5\_5', 'pixel\_5\_6', 'pixel\_5\_7', 'pixel\_6\_0', 'pixel\_6\_1', 'pixel\_6\_2', 'pixel\_6\_3', 'pixel\_6\_4', 'pixel\_6\_5', 'pixel\_6\_6', 'pixel\_6\_7', 'pixel\_7\_0', 'pixel\_7\_1', 'pixel\_7\_2', 'pixel\_7\_3', 'pixel\_7\_4', 'pixel\_7\_5', 'pixel\_7\_6', 'pixel\_7\_7'\], 'target_names': array(\[0, 1, 2, 3, 4, 5, 6, 7, 8, 9\]), 'images': array(\[\[\[ 0.,  0.,  5., ...,  1.,  0.,  0.\],         \[ 0.,  0., 13., ..., 15.,  5.,  0.\],         \[ 0.,  3., 15., ..., 11.,  8.,  0.\], // data omitted for brevity \])} 

[Listing F.17](#appF.xhtml#listF.17) displays the contents of load_digits2.py that illustrates how to plot one of the Digits dataset (which you can change in order to display a different digit).

***LISTING F.17: load_digits2.py***

```python
from sklearn.datasets import load_digits
from matplotlib import pyplot as plt
digits = load_digits()  # set interpolation='none'
fig = plt.figure(figsize=(3, 3))
plt.imshow(digits['images'][66], cmap="gray", interpolation='none')
plt.show()
```

[Listing F.17](#appF.xhtml#listF.17) imports the load_digits class from Sklearn in order to initialize the variable digits with the contents of the Digits dataset that is available in Sklearn. The next portion of [Listing F.17](#appF.xhtml#listF.17) initializes the variable fig and invokes the method imshow() of the plt class in order to display a number in the digits dataset.

[Figure F.16](#appF.xhtml#figF.16) displays a plot of one of the digits in the Digits dataset based on the code in [Listing F.17](#appF.xhtml#listF.17).

```
if (condVar > someVal) {console.log("xxx")}
```
