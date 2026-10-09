![](bbox=[0.32, 0.05, 0.73, 0.64])

图 7.19：根据近红外 (NIR) 光谱值绘制的燃料样本在不同波长下的分布。

我们可以将算法 20 转换为三行 R 代码：

```
```r
### marginal regression
> phi <- cor(nir, octane)/apply(nir, 2, sd)
> v <- nir%%phi
> fwd <- glm(octane ~ v)
```
```