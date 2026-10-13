
函数 $f(x) = \ln(1 - \exp(-x)), \quad x > 0$ 是凹函数（问题 [16.9](#Chp016_805-853_B9780443292385000226.xhtml#o0085)）。作为凹函数，根据第 [13.8](#Chp013_635-716_B9780443292385000196.xhtml) 节可知，它有一个上界：

$$f(x) \le \xi x - f^*(\xi),$$

其中 $f^*(\xi)$ 是其共轭函数。为了适配公式 [(16.10)](#Chp016_805-853_B9780443292385000226.xhtml#deq19) 的需求，并使用 $\xi_i$ 代替 $\xi$ 以显式表示对节点 $i$ 的依赖，我们得到：

$$P(f_i = 1|\mathbf{d}) \leqslant \exp\left( \xi_i\left( \sum_{j \in \text{Pa}_i}\theta_{ij}d_j \right) - f^*(\xi_i) \right), \tag{16.11}$$

或者写成：

$$P(f_i = 1|\mathbf{d}) \leqslant \exp\left( - f^*(\xi_i) \right)\prod_{j \in \text{Pa}_i}\left( \exp(\xi_i\theta_{ij}) \right)^{d_j}, \tag{16.12}$$

其中（问题 [16.10](#Chp016_805-853_B9780443292385000226.xhtml#o0090)）：

$$f^*(\xi_i) = -\xi_i\ln(\xi_i) + (\xi_i + 1)\ln(\xi_i + 1), \quad \xi_i > 0.$$
