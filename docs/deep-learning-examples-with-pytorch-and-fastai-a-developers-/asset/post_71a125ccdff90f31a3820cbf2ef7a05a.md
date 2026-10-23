
```
file_name = 'style.png'
```

We can now build the pipeline to transform our image into a Tensor which can be used later on by our loss-function. Let’s build the DataSet:

```python
bs = 1
dataset = Datasets(file_name, tfms=[PILImage.create])
dataloaders = dataset.dataloaders(
    after_item=[ToTensor()],
    after_batch=[IntToFloatTensor(), Normalize.from_stats(*imagenet_stats)],
    bs=bs
)
dataloaders.show_batch()
```

![](img/d5454da46c702784893ef8b0b539e5b9_162_0.png)

The filename of our style-image is passed into the dataloader. The dataloader applies the PILImage.create transform onto the image.

With the dataloader we add a ToTensor transform before the batch is created and an IntToFloatTensor as well as a Normalize transform for batch creation.

So, it looks good. We have created the dataset, initialized the dataloaders and the batch contains the image we had previously downloaded.

Now we need the raw values of the image. We run one_batch on the dataloader because we have just one item and we grab the x value.

```python
style_img = dataloaders.one_batch()[0]
style_img.shape
```

```python
torch.Size([1, 3, 1464, 3112])
```

Everything went fine. We have got a Tensor with 3 layers (for coloured images) and a batch size of 1 because there is just one image inside the batch.

As we want to build a style-transfer library we can condense our work into one function that extracts the raw values for any given image-url.

```python
#export
def get_style(url: str, filename: str ='style.png'):
    download_url(url, filename)
    dataset = Datasets(filename, tfms=[PILImage.create])
    dataloaders = dataset.dataloaders(
        after_item=[ToTensor()],
        after_batch=[IntToFloatTensor(), Normalize.from_stats(*imagenet_stats)],
        bs=bs
    )
    return dataloaders.one_batch()[0]
```

Now we want to extract the features from the image. We can use the function we have built before.

```python
img_features = features(style_img)
```

Next we can transfer the features into a channel-basis.

```python
#export
def gram(x:Tensor):
    """Transpose a tensor based on c,w,h"""
    n, c, h, w = x.shape
    x = x.view(n, c, -1)
    return (x @ x.transpose(1, 2))/(c*w*h)
```

```python
img_grams = [gram(f) for f in img_features]
```

Let’s compare the sizes to clarify what we have done so far.

First show the sizes of the extracted image-features:

```python
for f in img_features:
    print(f.shape)
```

```python
torch.Size([1, 64, 1464, 3112])
torch.Size([1, 128, 732, 1556])
torch.Size([1, 256, 366, 778])
torch.Size([1, 512, 183, 389])
torch.Size([1, 512, 91, 194])
torch.Size([1, 512, 183, 389])
```

... and now compare them to the Gram values for the image:

```python
for f in img_grams:
    print(f.shape)
```

```python
torch.Size([1, 64, 64])
torch.Size([1, 128, 128])
torch.Size([1, 256, 256])
torch.Size([1, 512, 512])
torch.Size([1, 512, 512])
torch.Size([1, 512, 512])
```

We can see that now we are relying only on the channel sizes for the different layers and are not concerned with the image resolution.

Now we want to grab everything except for the first layer.

```python
#export
def get_styles_features(fs): return fs[:-1]
```

By now we can summarize why we did all these steps. We are on our way to implementing the loss-function. Our loss function will take three different items into consideration:

- the extracted features from the encoder,
- the style loss, and
- the activation loss.

For the **style loss** we have the input and output values and calculate *mean squared error* for all of them. You could say we compare how the generated outputs look in comparison to the original style-image.

```python
#export
def style_loss(inp:Tensor, out_feat:Tensor):
    """Calculate style loss, assumes we have `im_grams`"""
    # Get batch size
    bs = inp[0].shape[0]
    loss = []
    # For every item in our inputs
    for y, f in zip(*map(get_styles_features, [img_grams, inp])):
        # Calculate MSE
        loss.append(F.mse_loss(y.repeat(bs, 1, 1), gram(f)))
    # Multiply their sum by 30000
    return 3e5 * sum(loss)
```

Now we have to implement our individual loss-function in a way the fastai library accepts it.

```python
#export
class FeatureLoss(Module):
    """Combines two losses and features into a useable loss function"""
    def __init__(self, feats, style_loss, act_loss):
        store_attr(self, 'feats, style_loss, act_loss')
        self.reset_metrics()

    def forward(self, pred, targ):
        # First get the features of our prediction and target
        pred_feat, targ_feat = self.feats(pred), self.feats(targ)
        # Calculate style and activation loss
        style_loss = self.style_loss(pred_feat, targ_feat)
        act_loss = self.act_loss(pred_feat, targ_feat)
        # Store the loss
        self._add_loss(style_loss, act_loss)
        # Return the sum
        return style_loss + act_loss

    def reset_metrics(self):
        # Generates a blank metric
        self.metrics = dict(style = [], content = [])

    def _add_loss(self, style_loss, act_loss):
        # Add to our metrics
        self.metrics['style'].append(style_loss)
        self.metrics['content'].append(act_loss)
```

With every new image getting into our model, we do NOT want to update the weights of the encoder because we do not want to train the model for the loss-function but the model for doing the style transfer.

The forward-function does exactly the same as the forward-function in our model: it goes through the model, every time we call it. We get the predictions from the feature extractor. Then we calculate the loss and store it away.

The reset_metrics just resets the values for the style and content losses.

```python
#export
def act_loss(inp:Tensor, targ:Tensor):
    """Calculate the MSE loss of the activation layers"""
    return F.mse_loss(inp[-1], targ[-1])
```

Our activation loss just returns a mean-squared-error-loss on itself. Now we can build our loss function (because our loss function is a model itself we have to do a forward pass every time we run it).

```python
loss_fun = FeatureLoss(features, style_loss, act_loss)
```

## 11.3 Create the Model Architecture

To build the model architecture we need some blocks. First we need a ReflectionLayer-block. This just does some reflection padding on the input and then calls Conv2d to create a 2d-convolution.

```python
#export
class ReflectionLayer(Module):
    """A series of Reflection Padding followed by a ConvLayer"""
    def __init__(self, in_channels, out_channels, ks=3, stride=2):
        reflection_padding = ks // 2
        self.reflection_pad = nn.ReflectionPad2d(reflection_padding)
        self.conv2d = nn.Conv2d(in_channels, out_channels, ks, stride)

    def forward(self, x):
        out = self.reflection_pad(x)
        out = self.conv2d(out)
        return out
```

We create a ReflectionLayer-object to check the containing layers:

```python
ReflectionLayer(3, 3)
```

```python
ReflectionLayer(
  (reflection_pad): ReflectionPad2d((1, 1, 1, 1))
  (conv2d): Conv2d(3, 3, kernel_size=(3, 3), stride=(2, 2))
)
```

Next we need a ResidualBlock. A residual block contains two ReflectionLayers. Like any other residual block it creates a result by doing a forward pass through the layers and then adds it to the input itself.

```python
#export
class ResidualBlock(Module):
    """Two reflection layers and an added activation function with residual"""
    def __init__(self, channels):
        self.conv1 = ReflectionLayer(channels, channels, ks=3, stride=1)
        self.in1 = nn.InstanceNorm2d(channels, affine=True)
        self.conv2 = ReflectionLayer(channels, channels, ks=3, stride=1)
        self.in2 = nn.InstanceNorm2d(channels, affine=True)
        self.relu = nn.ReLU()

    def forward(self, x):
        residual = x
        out = self.relu(self.in1(self.conv1(x)))
        out = self.in2(self.conv2(out))
        out = out + residual
        return out
```

```python
ResidualBlock(3)
```

```python
ResidualBlock(
  (conv1): ReflectionLayer(
    (reflection_pad): ReflectionPad2d((1, 1, 1, 1))
    (conv2d): Conv2d(3, 3, kernel_size=(3, 3), stride=(1, 1))
  )
  (in1): InstanceNorm2d(3, eps=1e-05, momentum=0.1, affine=True, track_running_stats=False)
  (conv2): ReflectionLayer(
    (reflection_pad): ReflectionPad2d((1, 1, 1, 1))
    (conv2d): Conv2d(3, 3, kernel_size=(3, 3), stride=(1, 1))
  )
  (in2): InstanceNorm2d(3, eps=1e-05, momentum=0.1, affine=True, track_running_stats=False)
  (relu): ReLU()
)
```

Then we create an UpsampleConvolutionLayer. This is another reflection layer but it also does some upsampling.

```python
#export
class UpsampleConvolutionLayer(Module):
    """Upsample with a ReflectionLayer"""
    def __init__(self, in_channels, out_channels, ks=3, stride=1, upsample=None):
        self.upsample = upsample
```
