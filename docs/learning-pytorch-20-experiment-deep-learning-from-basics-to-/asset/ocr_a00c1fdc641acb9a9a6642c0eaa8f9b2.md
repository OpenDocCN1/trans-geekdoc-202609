Define the network architecture: The architecture of a CNN model in PyTorch can be defined by subclassing the nn.Module class.

The following is an example of a simple CNN for image classification:

```
class CNN(nn.Module):

def __init__(self):
    super(CNN, self).__init__()

    self.conv1 = nn.Conv2d(1, 6, 5) # 1 input image channel, 6 output channels, 5x5 square convolution kernel

    self.pool = nn.MaxPool2d(2, 2) # Max pooling over a (2, 2) window

    self.conv2 = nn.Conv2d(6, 16, 5) # 6 input image channel, 16 output channels, 5x5 square convolution kernel
```