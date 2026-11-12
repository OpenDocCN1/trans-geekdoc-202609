# # Discriminator network

```
class Discriminator(nn.Module):
    def __init__(self, n_gpu):
        super(Discriminator, self).__init__()
        self.n_gpu = n_gpu
        self.main = nn.Sequential(
        # input is (n_channel) x 64 x 64
        nn.Conv2d(n_channel, dis_fmap, 4, 2, 1, bias=False),
        nn.LeakyReLU(0.2, inplace=True),
        # state size. (dis_fmap) x 32 x 32
        nn.Conv2d(dis_fmap, dis_fmap*2, 4, 2, 1, bias=False),
        nn.BatchNorm2d(dis_fmap * 2),
        nn.LeakyReLU(0.2, inplace=True),
        # state size. (dis_fmap*2) x 16 x 16
        nn.Conv2d(dis_fmap * 2, dis_fmap * 4, 4, 2, 1, bias=
        False),
        nn.BatchNorm2d(dis_fmap*4),
        nn.LeakyReLU(0.2, inplace=True),
        # state size. (dis_fmap*4) x 8 x 8
        nn.Conv2d(dis_fmap * 4, dis_fmap * 8, 4, 2, 1, bias=
        False),
        nn.BatchNorm2d(dis_fmap * 8),
        nn.LeakyReLU(0.2, inplace=True),
        # state size. (dis_fmap*8) x 4 x 4
        nn.Conv2d(dis_fmap * 8, 1, 4, 1, 0, bias=False),
        nn.Sigmoid()
        )
    def forward(self, input):
        return self.main(input)
```

The discriminator is basically a binary classification convolutional network, which classifies between _real(1)_ and _fake(0)_ images by taking images as input and giving a scalar probability, that is, 0 or 1. As mentioned in the DCGAN paper, the discriminator consists of a series of **Conv2d**, **leakyReLU**, and **BatchNorm2d** layers and, finally, the sigmoid activation function to produce the final probability.

As done in the case of the generator network, the discriminator is created, initialized with the random values through the weight **init()** function, and finally, printed to see the structure of the discriminator object.