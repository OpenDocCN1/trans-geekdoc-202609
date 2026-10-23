```
conv2(1, 8),
ResBlock(8),
conv2(8, 16),
ResBlock(16),
conv2(16, 32),
ResBlock(32),
conv2(32, 16),
ResBlock(16),
conv2(16, 10),
Flatten()
)
model
Sequential( (0): ConvLayer( (0): Conv2d(1, 8, kernel_size=(3, 3), stride=(2, 2), padding=(1, 1), bias=False) (1): BatchNorm2d(8, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True) (2): ReLU() ) (1): ResBlock( (conv1): ConvLayer( (0): Conv2d(8, 8, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False) (1): BatchNorm2d(8, eps=1e05, momentum=0.1, affine=True, track_running_stats=True) (2): ReLU() ) (conv2): ConvLayer( (0): Conv2d(8, 8, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False) (1): BatchNorm2d(8, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True) (2): ReLU() ) ) (2): ConvLayer( (0): Conv2d(8, padding=(1, 1), bias=False) (1): 16, kernel_size=(3, 3), stride=(2, 2), BatchNorm2d(16, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True) (2): ReLU() ) (3): ResBlock( (conv1): ConvLayer( (0): Conv2d(16, 16, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False) (1): BatchNorm2d(16, eps=1e05, momentum=0.1, affine=True, track_running_stats=True) (2): ReLU() ) (conv2): ConvLayer( (0): Conv2d(16, 16, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False) (1): BatchNorm2d(16, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True) (2): ReLU() ) ) (4): ConvLayer( (0): Conv2d(16, 32, kernel_size=(3, 3), stride=(2, 2), padding=(1, 1), bias=False) (1): BatchNorm2d(32, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True) (2): ReLU() ) (5): ResBlock( (conv1): ConvLayer(
```