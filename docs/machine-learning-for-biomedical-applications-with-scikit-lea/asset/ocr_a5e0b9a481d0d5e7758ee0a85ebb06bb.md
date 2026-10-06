244 Machine Learning for Biomedical Applications

```
nn.Linear(n, 128),
n.ReLU(),
nn.Linear(128,10),
nn.ReLU()
output3=fc_block(output2.view(-1,n))
print(output3.shape)
>>> torch.Size([1, 10])
```

#  11.2.7 CNN model

Finally, we are ready to implement the whole network (nn.Module): in Fig. 11.3.

```
class CNNModel(nn.Module):
    def __init__(self):
        super(CNNModel, self).__init__(

        self.conv_block1 = nn.Sequential(
            nn.Conv2d(1,8,5,padding=2),
            nn.BatchNorm2d(8),
            nn.ReLU(),
            nn.MaxPool2d(kernel_size=2,stride=2)))
        self.conv_block2 = nn.Sequential(
            nn.Conv2d(8,16,5,padding=2),
            nn.BatchNorm2d(16),
            nn.ReLU(),
            nn.MaxPool2d(kernel_size=2,stride=2)))
        self.fc_block = nn.Sequential(
            nn.Linear(16*16*16, 128),
            nn.ReLU(),
            nn.Linear(128,10),
            nn.ReLU())

    def forward(self, x):
        x = self.conv_block1(x)
        x = self.conv_block2(x)
        x = x.view(-1, 16*16)
        x = self.fc_block(x)
        return x
```

We can now create an instance of this network and perform the forward pass:

```
net = CNNModel()
```