
假设输入和权重的均值为 0，即 `E[x[i]] = E[w[i]] = 0`，则：

$$
\begin{matrix} 
Var(z) & = \sum\limits_{i}^{n} Var(x_{i}) Var(w_{i}) \\ 
& = (n Var(w)) Var(x) \\ 
\end{matrix}
$$

输出值的方差 `Var(z)` 不仅与输入值的方差 `Var(x)` 和权重的方差 `Var(w)` 成正比，还与输入值 `x[i]` 的数量 `n` 成正比。

当输出方差等于输入方差时，即 `Var(z) = Var(x)`，也就是说输入数据 `x` 通过神经元后，输出方差不会变大或变小，从而使神经元的输入和输出保持稳定。

为了使 `Var(z) = Var(x)`，`Var(w)` 应为 $\frac{1}{n}$。根据 `Var(aX) = a^2 Var(X)`，如果 `w` 从标准正态分布采样，则 `Var(w) = 1`，将 `w` 乘以常数 $a = \frac{1}{\sqrt{n}}$，则 `Var(aw) = a^2 Var(w) = 1`。因此，权重可以用以下代码初始化：

```
w = np.random.randn(n) * sqrt(1.0/n) 
```

根据类似的分析，一些论文提出了其他不同的参数方法，例如 Glorot 将标准正态分布的权重参数 `w` 乘以 $\sqrt{2/(n_{in} + n_{out})}$，使得 `Var(w) = 2/(n[in] + n[out])`，其中 `n[in]`、`n[out]` 分别是网络层的输入和输出向量。其目的是使梯度在反向传播过程中方差不变。当然，这两项的结合会相互影响，导致正向和反向推导的方差实际上都会发生变化。

权重也可以服从均匀分布：$w \sim U\lbrack - \frac{\sqrt{6}}{\sqrt{n_{in} + n_{out}}}, \frac{\sqrt{6}}{\sqrt{n_{in} + n_{out}}}\rbrack$，et al. 提出的这种权重初始化方法称为 **Xavier 初始化**，其代码实现如下：

```
import numpy as np
import math

def calculate_fan_in_and_fan_out(tensor):
    if len(tensor.shape) < 2:
        raise ValueError("tensor with fewer than 2 dimensions")
    if len(tensor.shape) == 2:
        fan_in, fan_out = tensor.shape
    else:  # F, C, kH, kW
        num_input_fmaps = tensor.shape[1]   # size(1)  F, C, H, W
        num_output_fmaps = tensor.shape[0]  # size(0)
        receptive_field_size = tensor[0][0].size
        fan_in = num_input_fmaps * receptive_field_size
        fan_out = num_output_fmaps * receptive_field_size   
    return fan_in, fan_out

def xavier_uniform(tensor, gain=1.):    
    fan_in, fan_out = calculate_fan_in_and_fan_out(tensor)
    std = gain * math.sqrt(2.0 / float(fan_in + fan_out))
    bound = math.sqrt(3.0) * std  
    tensor[:] = np.random.uniform(-bound, bound, tensor.shape)

def xavier_normal(tensor, gain=1.):
    fan_in, fan_out = calculate_fan_in_and_fan_out(tensor)
    std = gain * math.sqrt(2.0 / float(fan_in + fan_out))
    tensor[:] = np.random.normal(0, std, tensor.shape)
```

其中，函数 `calculate_fan_in_and_fan_out()` 用于计算网络层（神经元）的输入特征数和输出特征数，`gain` 是权重的可选缩放因子，默认为 1。

对于使用 ReLU 作为激活函数的神经元，目前更常用 Kaiming He 的权重初始化方法，即将标准正态分布采样的权重乘以 $\sqrt{2/n}$，代码如下：

```
w = np.random.randn(n) * sqrt(2.0/n) 
```

对于使用 ReLU 激活函数的网络层，其偏置参数 `b` 建议设置为非零常数（如 0.01），这可以使该激活函数在训练开始时影响梯度，但将偏置设置为非零值是否真的能提高算法性能尚无定论。

以下是 Kaiming 方法的实现代码：

```
def calculate_gain(nonlinearity, param=None):   
    linear_fns = ['linear', 'conv1d', 'conv2d', 'conv3d', 'conv_transpose1d', 'conv_transpose2d', 'conv_transpose3d']
    if nonlinearity in linear_fns or nonlinearity == 'sigmoid':
        return 1
    elif nonlinearity == 'tanh':
        return 5.0 / 3
    elif nonlinearity == 'relu':
        return math.sqrt(2.0)
    elif nonlinearity == 'leaky_relu':
        if param is None:
            negative_slope = 0.01
        elif not isinstance(param, bool) and (isinstance(param, int) or isinstance(param, float)):           
            negative_slope = param
        else:
            raise ValueError("negative_slope {} not a valid number".format(param))
        return math.sqrt(2.0 / (1 + negative_slope ** 2))
    else:
        raise ValueError("Unsupported nonlinearity {}".format(nonlinearity))
        
def kaiming_uniform(tensor, a=0, mode='fan_in', nonlinearity='leaky_relu'):
    fan_in, fan_out = calculate_fan_in_and_fan_out(tensor)
    if mode == 'fan_in':       
        fan = fan_in
    else: 
        fan = fan_out
        
    gain = calculate_gain(nonlinearity, a)
    std = gain / math.sqrt(fan)
    bound = math.sqrt(3.0) * std  
    tensor[:] = np.random.uniform(-bound, bound, tensor.shape)

def kaiming_normal(tensor, a=0, mode='fan_in', nonlinearity='leaky_relu'):
    fan_in, fan_out = calculate_fan_in_and_fan_out(tensor)
    if mode == 'fan_in':     
        fan = fan_in
    else: 
        fan = fan_out
    
    gain = calculate_gain(nonlinearity, a)
    std = gain / math.sqrt(fan)
    bound = math.sqrt(3.0) * std  # Calculate uniform bounds from standard deviation    
    tensor[:] = np.random.normal(0, std, tensor.shape)
```

`calculate_gain()` 用于 Kaiming He 方法（也称 Kaiming 方法或 He 方法）中的某个系数。例如，ReLU 的值为 $\sqrt{2}$，tanh 的值为 5.0/3。`kaiming_uniform()` 和 `kaiming_normal()` 分别使用均匀分布和高斯分布随机值的 Kaiming 方法。

以下函数 `kaiming()` 根据参数选择 `kaiming_uniform()` 或 `kaiming_normal()` 方法：

```
def kaiming(tensor, method_params=None):
    method_type, a, mode, nonlinearity = 'uniform', 0, 'fan_in', 'leaky_relu'
    if method_params:
        method_type = method_params.get('type', "uniform")
        a = method_params.get('a', 0)
        mode = method_params.get('mode', 'fan_in')
        nonlinearity = method_params.get('nonlinearity', 'leaky_relu')
    if method_type == "uniform":
        kaiming_uniform(tensor, a, mode, nonlinearity)
    else:
        kaiming_normal(tensor, a, mode, nonlinearity)   
```

以下代码测试上述参数初始化方法：

```
w = np.empty((2, 3))
print(w)

xavier_uniform(w)
print("xavier_uniform:", w)
xavier_normal(w)
print("xavier_normal:", w)

kaiming_uniform(w)
print("kaiming_uniform:", w)
kaiming_normal(w)
print("kaiming_normal:", w)
```

输出：

```
[[17.2 17.2 17.2]
 [17.2 17.2 24.2]]
xavier_uniform: [[ 0.026289 -1.09114298 -0.48792212]
 [-0.3313437 -0.47333989 -0.90713322]]
xavier_normal: [[ 0.93298795 0.07044394 -0.00270454]
 [ 0.44167298 -1.01942638 0.45699115]]
kaiming_uniform: [[-1.21534711 -1.27523387 0.80492134]
 [0.81222595 -1.11076413 -0.29943563]]
kaiming_normal: [[-0.98492851 0.24745387 0.53676485]
 [ 1.27654978 1.52143405 0.87124828]]
```

此外，还可以向 `NeuralNetwork` 类添加辅助函数 `apply(self, init_params_fn)` 以初始化其所有层参数，这可以方便地对神经网络的多层进行初始化，例如使用 `kaiming_normal()` 方法初始化所有层的参数。

```
def apply(self, init_params_fn):
    for layer in self._layers:            
        init_params_fn(layer)
```

### 5.2.2 优化参数
