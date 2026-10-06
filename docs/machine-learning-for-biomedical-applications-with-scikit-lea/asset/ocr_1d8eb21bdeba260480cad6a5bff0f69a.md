```
enc1 = ReLU(conv1_down(im))
enc1.shape
>>> torch.Size([1, 8, 256, 256])
```

The encoder activations in the following blocks are obtained by downsampling using averaging pooling, followed by a convolution to increase the number of features (red arrows). The second level activation maps enc2, obtained using the following code, 16 channels and reduced spatial resolution 128 × 128:

```
down = nn.AvgPool2d(kernel_size=2)
conv2_down = nn.Conv2d(8,16,3,padding=1)
enc2=down(enc1)
enc2=ReLU(conv2_down(enc2))
enc2.shape
>>> torch.Size([1, 16, 128, 128])
```

Obtaining the third-level encoder activation maps enc3 is analogous to the second level, resulting in 32 channels and resolution 64 × 64:

```
conv3_down = nn.Conv2d(16,32,3,padding=1)
enc3=down(enc2)
enc3=ReLU(conv3_down(enc3))
enc3.shape
>>> torch.Size([1, 32, 64, 64])
```

For the fourth-level encoder activation maps, we opt not to increase the number of channels to keep the network small, enc4 with 32 channels with spatial resolutions 32 × 32:

```
conv4 = nn.Conv2d(32,32,3,padding=1)
enc4=down(enc3)
enc4=ReLU(conv4(enc4))
enc4.shape
>>> torch.Size([1, 32, 32, 32])
```

# Decoder

The decoder block (green arrow) consists of three steps: upsampling the activation maps using bilinear interpolation, concatenating the encoder activation maps from the same resolution level (skip connection, grey arrow); and convolution that decreases the number of feature maps:

```
up = nn.UpsamplingBilinear2d(scale_factor=2)
conv3_up = nn.Conv2d(32+32,16,3,padding=1)
```