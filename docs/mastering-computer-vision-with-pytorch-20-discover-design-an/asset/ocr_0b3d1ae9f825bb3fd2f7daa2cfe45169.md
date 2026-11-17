```
```python
if stride != 1 or self.in_channels != out_channels *
block.expansion:
    downsample = nn.Sequential(
    nn.Conv2d(self.in_channels, out_channels *
    block.expansion, kernel_size=1, stride=stride,
    bias=False),
    nn.BatchNorm2d(out_channels * block.expansion),
    )

# The first block in the layer
layers = [block(self.in_channels, out_channels, stride,
downsample)]
self.in_channels = out_channels * block.expansion
# Remaining blocks in the layer
for _ in range(1, blocks):
    layers.append(block(self.in_channels, out_channels))

return nn.Sequential(*layers)

# The forward pass
def forward(self, x):
    x = self.conv1(x)
    x = self.bn1(x)
    x = self.relu(x)
    x = self.maxpool(x)

# Passing input through the layers
x = self.layer1(x)
x = self.layer2(x)
x = self.layer3(x)
x = self.layer4(x)

# Pooling and classification
x = self.avgpool(x)
x = torch.flatten(x, 1)
x = self.fc(x)

return x
```
```