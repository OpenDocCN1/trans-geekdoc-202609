

$L(\Theta,\mathbf{b},\mathbf{c}) = \frac{1}{N}\sum\limits_{n = 1}^{N}\ln P(\mathbf{v}_{n};\Theta,\mathbf{b},\mathbf{c}) = \frac{1}{N}\sum\limits_{n = 1}^{N}\ln\left( \frac{1}{Z}\sum\limits_{\mathbf{h}}\exp\left( - E(\mathbf{v}_{n},\mathbf{h};\Theta,\mathbf{b},\mathbf{c}) \right) \right) = \frac{1}{N}\sum\limits_{n = 1}^{N}\ln\left( \sum\limits_{\mathbf{h}}\exp\left( - E(\mathbf{v}_{n},\mathbf{h};\Theta,\mathbf{b},\mathbf{c}) \right) \right) - \ln\sum\limits_{\mathbf{v}}\sum\limits_{\mathbf{h}}\exp\left( - E(\mathbf{v},\mathbf{h}) \right),$

其中，能量函数中的索引 $n$ 指的是可见节点被钳制到的相应观测值，并且 $\Theta,\mathbf{b},\mathbf{c}$ 已显式地引入符号表示中。

对 $L(\Theta,\mathbf{b},\mathbf{c})$ 关于 $\theta[i j]$ 求导（关于 $b[i]$ 和 $c[j]$ 的导数情况类似）并应用导数的标准性质，不难证明（[问题 19.1](#Chp019_997-1102_B9780443292385000251.xhtml#o0045)）可得

![Equation](images/B9780443292385000251/fx001.jpg) (19.4)

其中用到了以下内容：

