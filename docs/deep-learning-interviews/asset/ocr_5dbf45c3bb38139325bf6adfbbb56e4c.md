# **SOL-186 ✎ CH.SOL- 8.10.**

1 True. These operations have two key features: they are shift invariant, and they are linear. Shift invariance means that we perform the same operation at every point in the image. Linearity means that this operation is linear, that is, we replace every pixel with a linear combination of its neighbours

2 True. See for instance Eq. (8.3).

3 True.

# The correlation operator

# **SOL-187 ✎ CH.SOL- 8.11.**

1 True.

2 True.

# **SOL-188 ✎ CH.SOL- 8.12.**

A convolution operation is just like correlation, except that we flip over the filter both horizontally and vertically before correlating.

```
$$f(x,y)\otimes h(x,y)=\sum_{m=0}^{M-1}\sum_{n=0}^{N-1} f^{*}(m,n) h(x+m,y+n)$$

(8.44)
```

# Padding and stride

Recommended reading : “A guide to convolution arithmetic for deep learning by Vincent Dumoulin and Francesco Visin (2016)” [22].