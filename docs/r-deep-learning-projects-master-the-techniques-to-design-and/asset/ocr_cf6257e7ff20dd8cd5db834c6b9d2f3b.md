Now, we can visualize the activations for the first and second convolutional layer and ReLu layer, as well as the first pooling layer.

Let's start with the ReLu activations for the first 16 filters in the first convolutional layer, which are called activation15_output in our case (again, the name may vary). For the first sample, (a "1"), we run the following scripts:

```
> par(mfrow=c(4,4), mar=c(0.1,0.1,0.1,0.1))
> for (i in 1:16) {
+ outputData <- as.array
(executor$ref.outputs$activation15_output)[,,i,1]
+ image(outputData, xaxs='n', yaxs='n',
col=grey.colors(255)
+ )
+ }
```

Similarly, for the second sample, (a "0"), we run:

```
> par(mfrow=c(4,4), mar=c(0.1,0.1,0.1,0.1))
> for (i in 1:16) {
+ outputData <- as.array
(executor$ref.outputs$activation15_output)[,,i,2]
+ image(outputData, xaxs='n', yaxs='n',
col=grey.colors(255)
+ )
+ }
```

We plot the activations of the first convolutional layer for a 1 (left) and a 0 (right) input image, respectively:

![](bbox=[0.276, 0.612, 0.723, 0.781])

We can observe that each feature map effectively extracts the edges, curves and strikes of the digits.