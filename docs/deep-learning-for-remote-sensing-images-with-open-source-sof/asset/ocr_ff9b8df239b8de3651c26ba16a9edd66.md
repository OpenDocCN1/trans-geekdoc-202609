```
or
otbcli_TensorflowModelServe -help
```

As you can notice, the applications now have 2 sources, namely *source1* and *source2*, each one with its parameters.

> **Important note**
> 
> If you try with the **TensorflowModelServe** application, you can notice that there is **OTB_TF_NSOURCES+1** sources. This comes from the fact that there is at least one more source for the reference input: in the case of the classification task for instance, this additional input is required for the labels of the ground truth.

# 8.2  Model with multiple inputs

We propose a CNN with two inputs with different resolution: the 10-m-spacing bands of Sentinel-2 (Spectral band 2, 3, 4 and 8) and the 20-m-spacing bands of Sentinel-2 (Spectral band 5, 6, 7, 8a, 11 and 12). This model processes the two inputs jointly and outputs a land cover map at the lowest resolution, i.e. 20-m-spacing. The 20-m-spacing image patches have a size of 8 × 8 and the 10-m-spacing image a size of 16 × 16. Note that we could have different patch sizes, but we want our model inputs to be the same physical area in both resolutions. *Figure 8.1* summarizes the implemented deep net.