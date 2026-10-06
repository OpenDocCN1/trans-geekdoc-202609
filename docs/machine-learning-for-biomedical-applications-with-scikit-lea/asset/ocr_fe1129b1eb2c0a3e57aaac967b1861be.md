# Convolutional neural networks

Let's now apply max-pooling to the output that we created by passing
input_image through a convolutional layer in the previous section. First, let's print out
its shape

```
print(output.shape)
>> torch.Size([1, 8, 64, 64])
```

Now we define the max-pooling operation with kernel size 2 and stride 2 to down-sample the output by factor two

```
maxpool = torch.nn.MaxPool2d(kernel_size=2,stride=2)
downsampled = maxpool(output)
print(downsampled.shape)
>> torch.Size([1, 8, 32, 32])
```

The alternative commonly used pooling operation is average pooling, where instead
taking the maximum of the block, the average value is calculated. In Pytorch this is
implemented by the function

```
torch.nn.AvgPool2d(2,2)
```

# Stiding

Stiding can be used to downsample the image while performing the convolution operation. For example, when applying convolution with a stride 2, we skip every second
pixel in the image, as illustrated in Fig. 11.6.

| 55 | 60 | 65 | 68 | 60 | 60 | 73 |
|---|---|---|---|---|---|---|n| 67 | 65 | 63 | 67 | 70 | 73 | 103 |
| 73 | 64 | 62 | 65 | 80 | 97 | 145 |
| 1 | 0 | -1 | | | | |
| 2 | 0 | -2 | | | | |
| 69 | 65 | 68 | 83 | 133 | 165 | 216 |
| 1 | 0 | -1 | | | | |
| 79 | 89 | 108 | 165 | 195 | 234 |
| 68 | 89 | 105 | 131 | 198 | 220 | 237 |
| 67 | 110 | 146 | 177 | 233 | 245 | 238 |

| | -27 | -144 |
|---|---|---|
| -5 | -224 | -300 |
| -171 | -349 | -152 |

Figure 11.6 Strided convolution.

The following code illustrates how we can perform strided convolutions of the
input_image to reduce its spatial dimension two-fold, by setting the stride to 2:

```
print(input_image.shape)
>> torch.Size([1, 1, 64, 64])
```