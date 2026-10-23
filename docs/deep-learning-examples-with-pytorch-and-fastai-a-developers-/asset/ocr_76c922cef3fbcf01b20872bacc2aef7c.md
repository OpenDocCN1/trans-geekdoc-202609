```
self.res5 = ResidualBlock(128)
# Upsampling Layers
self.deconv1 = UpsampleConvolutionLayer(128, 64, ks=3, stride=1,
upsample=2) self.in4 = nn.InstanceNorm2d(64, affine=True) self.deconv2 =
UpsampleConvolutionLayer(64, 32, ks=3, stride=1, upsample=2) self.in5 =
nn.InstanceNorm2d(32, affine=True) self.deconv3 = ReflectionLayer(32, 3,
ks=9, stride=1) # Non-linearities
self.relu = nn.ReLU()

def forward(self, X):
y = self.relu(self.in1(self.conv1(X))) y = self.relu(self.in2(self.conv2(y))) y =
self.relu(self.in3(self.conv3(y))) y = self.res1(y)
y = self.res2(y)
y = self.res3(y)
y = self.res4(y)
y = self.res5(y)
y = self.relu(self.in4(self.deconv1(y))) y = self.relu(self.in5(self.deconv2(y)))
y = self.deconv3(y)
return y

net = TransformerNet()
```

# 11.4 DataLoaders and Learners

To test our model architecture we will use the COCO_SAMPLE-dataset. Let’s first look at the datablock we use. We pass in an ImageBlock and get out an ImageBlock. The only transforms we are applying are resizing to 224x224 and normalizing to the imagenet stats.

We do not pass in any y-values because our Xs are also our y-values. If we do not pass in any y-values, the fastai library assumes that our Xs should be used as y-values.

```
path = untar_data(URLs.COCO_SAMPLE)
datablock = DataBlock(blocks=(ImageBlock, ImageBlock),
get_items=get_image_files,
splitter=RandomSplitter(0.1, seed=123456), item_tfms=[Resize(224)],
```