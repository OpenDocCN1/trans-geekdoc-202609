```
```
self.math = torch.nn.Sequential(
    torch.nn.Conv2d(3,32,kernel_size=7,padding=2),
    torch.nn.BatchNorm2d(32),
    torch.nn.MaxPool2d(2,2),
    torch.nn.MaxPool2d(2,2),
)

def forward(self,x):

    print(x.data.shape)

    x = self.math(x)

    print(x.data.shape)

    x = x.view(x.size(0),-1)

    print("Final shape: {}",x.data.shape)

    return x
model = MaxPool001()

model.eval()
x = torch.rand(1,3,224,224)
out=model.forward(x)
```
```

CODE 9.1: A CNN in PyTorch

*The architecture is presented in* 9.2 *: