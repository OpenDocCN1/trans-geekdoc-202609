
其中 **z**[*n*]^(*T*) := [*z*[*n*1], …, *z*[*n**l*]] 是公式 [(20.8)](#Chp020_1103-1179_B9780443292385000263.xhtml#deq8) 右侧 *l* × *N* 矩阵的第 *n* 列。也就是说，根据定义，$z_{n1} = {\sqrt{\lambda}}_{1}v_{1n}$，以此类推。公式 [(20.9)](#Chp020_1103-1179_B9780443292385000263.xhtml#deq9) 中的求和已被拆分为两项，其中 *m* 可以是满足 1 ≤ *m* ≤ *l* 的任意值。注意，由于 **u**[*i*] 的标准正交性，

*z*[*n**i*] = **u**[*i*]^(*T*)**x**[*n*], *i* = 1, 2, …, *l*, *n* = 1, 2, …, *N*。

从第 [6.4](#Chp006_249-291_B9780443292385000123.xhtml) 节（公式 [(6.22)](#Chp006_249-291_B9780443292385000123.xhtml)）可知，在 Frobenius 范数意义上，*X* 的最佳 *m* 秩矩阵近似由下式给出：

```
$\widehat{X} = \underset{l \times m}{\underset{︸}{[\mathbf{u}_{1},\ldots,\mathbf{u}_{m}]}}\underset{m \times N}{\underset{︸}{\begin{bmatrix} {\sqrt{\lambda}}_{1}\mathbf{v}_{1}^{T} \\ \vdots \\ {\sqrt{\lambda_{m}}}\mathbf{v}_{m}^{T} \\ \end{bmatrix}}},$
```

```
$= \sum\limits_{i = 1}^{m}\sqrt{\lambda_{i}}\mathbf{u}_{i}\mathbf{v}_{i}^{T}.$
```

回顾 *z*[*n**i*] 的先前定义，*X̂* 的第 *n* 列向量现在可以写为
