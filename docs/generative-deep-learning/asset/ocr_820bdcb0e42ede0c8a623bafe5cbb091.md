![](bbox=[0.24, 0.09, 0.73, 0.38])

Figure 8-11. The DownBlock and corresponding UpBlock in the U-Net

We can code the DownBlock and UpBlock using Keras as illustrated in Example 8-9.

# Example 8-9. Code for the DownBlock and UpBlock in the U-Net model

```
```python
def DownBlock(width, block_depth):
    def apply(x):
        x, skips = x
        for _ in range(block_depth):
            x = ResidualBlock(width)(x) ①
            skips.append(x) ②
        x = layers.AveragePooling2D(pool_size=2)(x) ③
        return x

    return apply

def UpBlock(width, block_depth):
    def apply(x):
        x, skips = x
        x = layers.UpSampling2D(size=2, interpolation="bilinear")(x) ④
        for _ in range(block_depth):
            x = layers.Concatenate()([x, skips.pop()]) ⑤
            x = ResidualBlock(width)(x) ⑥
        return x

    return apply
```
```