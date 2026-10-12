
#### 3. 多分类交叉熵损失函数在输出端的梯度

对于多分类问题，神经网络通过最后的 softmax 函数将上一层的输出转化为具有直观含义的概率，表示样本属于各个类别的概率。由于 softmax 神经元不包含任何模型参数，有时 softmax 不作为神经网络的最后一层，而是将上一层作为神经网络的最后输出层。无论采用哪种方案，通常都在最后计算 softmax 回归中的多分类交叉熵损失。通常采用后一种方案，即假设输出层输出分数而非概率。该输出层的神经元为线性回归神经元，直接输出其输入的加权和作为激活值，即 `f[i] = a[i]^(L) = z[i]^(L)`（假设这是一个 L 层神经网络，该输出层的序号为 L）。

设输出层的输出 `zz` 经 softmax 函数产生输出 `ff`，再与目标值 `yy` 计算交叉熵损失 `L(ff, yy)`。

对于多个样本，输出层的输出可写为矩阵 `ZZ = (zz[1], ⋯, zz[i], ⋯, zz[m])^T`，经 softmax 函数产生的输出也为表示概率的矩阵 `FF = (ff, ⋯, ff[i], ⋯, ff[m])^T`。根据第 3.6 节，若每个目标值 `yy[i]` 使用独热向量表示，则 `YY` 也是一个矩阵。此时，多分类交叉熵损失 `L(F, Y)` 关于 `ZZ` 的梯度为：$\frac{1}{m}(FF - YY)$。

若每个目标值 `yy[i]` 为整数，表示样本所属类别的下标，则多分类交叉熵损失 `L(F, Y)` 关于 `ZZ` 的梯度为：$\frac{1}{m}(FF - I_i I_i)$。其中 `I[i]I[i]` 的每一行为独热向量，即将样本对应的整数转换为独热向量，因此 `I[i]I[i]` 由 `I[i]I[i]` 组成，与上述独热向量 $\pmb{Y}$ 相同。

以下 Python 代码将整数值的目标向量转换为独热向量矩阵：

```python
I_i = np.zeros_like(Z)
I_i[np.arange(len(Z)), Y] = 1
```

可以看出，回归的欧氏损失、二分类的交叉熵损失函数、多分类的交叉熵损失，关于输出层 `ZZ` 的梯度惊人地一致。均为 $\frac{1}{m}(FF - YY)$。

给定多样本输出层加权和 Z 和目标值 Y，以下代码计算多分类交叉熵关于 Z 的梯度（见第 3.6 节）：

```python
def softmax(x):   
    a = np.max(x, axis=-1, keepdims=True)  
    e_x = np.exp(x - a)
    return e_x / np.sum(e_x, axis=-1, keepdims=True)

def cross_entropy_grad(Z, Y, onehot=False, softmax_out=False):  
    if softmax_out:
        F = Z
    else:
        F = softmax(Z)
    if onehot:
        dZ = (F - Y) / len(Z)
    else:
        m = len(Y)
        dZ = F.copy()
        dZ[np.arange(m), Y] -= 1
        dZ /= m
        # I_i = np.zeros_like(Z)
        # I_i[np.arange(len(Z)), Y] = 1    
        # return (F - I_i) / len(Z)  # Z.shape[0]
    return dZ
```

### 4.2.4 两层神经网络反向传播的推导

#### 1. 单样本的逆向推导

反向传播推导算法根据神经网络前向传播的逆向计算，计算损失函数关于每一层相关变量的梯度。输出层加权和关于损失函数的梯度 $\frac{\partial\mathcal{L}}{\partial z^{[L]} z^{[L]}}$ 之前已经得到，现在讨论如何根据层加权和 $z^{[l]}z^{[l]}$ 的梯度，求出损失在该层变量 $W^{[l]}W^{[l]}$、$b^{[l]}b^{[l]}$、$a^{[l-1]}a^{[l-1]}$ 上的梯度 $\frac{\partial\mathcal{L}}{\partial z^{[l]} z^{[l]}}$。

对于两层神经网络，如何求得 $\frac{\partial\mathcal{L}}{\partial W^{[2]} W^{[2]}},\frac{\partial\mathcal{L}}{\partial b^{[2]} b^{[2]}},\frac{\partial\mathcal{L}}{\partial a^{[1]} a^{[1]}}$？

$\mathcal{L}$ 是 $z^{[2]}z^{[2]}$ = ($z_1^{[2]}$, $z_2^{[2]}$, $z_3^{[2]}$) 的函数，且 $z^{[2]}z^{[2]}$ = $a^{[1]}a^{[1]}$$W^{[2]}$$W^{[2]}$ + $b$$b^{[2]}$，即 $z^{[2]}z^{[2]}$ 是 $a^{[1]}a^{[1]}$、$W^{[2]}$$W^{[2]}$、$b^{[2]}$ 的函数。

$$

\begin{matrix} 

z^{[2]} & {= (z_1^{[2]},z_2^{[2]},z_3^{[2]}) = (a_1^{[1]},a_2^{[1]},a_3^{[1]},a_4^{[1]})\begin{bmatrix} W_{11}^{(2)} & W_{12}^{(2)} & W_{13}^{(2)} \\ W_{21}^{(2)} & W_{22}^{(2)} & W_{23}^{(2)} \\ W_{31}^{(2)} & W_{32}^{(2)} & W_{34}^{(2)} \\ W_{41}^{(2)} & W_{42}^{(2)} & W_{44}^{(2)} \\ \end{bmatrix} + (b_1^{[2]},b_2^{[2]},b_3^{[2]})} \\ 

& {= (a_1^{[1]}W_{11}^{(2)} + a_2^{[1]}W_{21}^{(2)} + a_3^{[1]}W_{31}^{(2)} + a_4^{[1]}W_{41}^{(2)} + b_1^{[2]},} \\ 

& {\quad a_1^{[1]}W_{12}^{(2)} + a_2^{[1]}W_{22}^{(2)} + a_3^{[1]}W_{32}^{(2)} + a_4^{[1]}W_{42}^{(2)} + b_1^{[2]}} \\ 

& {\quad a_1^{[1]}W_{13}^{(2)} + a_2^{[1]}W_{23}^{(2)} + a_3^{[1]}W_{33}^{(2)} + a_4^{[1]}W_{43}^{(2)} + b_1^{[2]})} \\ 

\end{matrix}

$$

根据链式求导法则，有：

$$

\frac{\partial\mathcal{L}}{\partial a_1^{[1]}} = \frac{\partial\mathcal{L}}{\partial z_1^{[2]}}\frac{\partial z_1^{[2]}}{\partial a_1^{[1]}} + \frac{\partial\mathcal{L}}{\partial z_2^{[2]}}\frac{\partial z_2^{[2]}}{\partial a_1^{[1]}} + \frac{\partial\mathcal{L}}{\partial z_3^{[2]}}\frac{\partial z_3^{[2]}}{\partial a_1^{[1]}} = \frac{\partial\mathcal{L}}{\partial z_1^{[2]}}W_{11}^{[2]} + \frac{\partial\mathcal{L}}{\partial z_2^{[2]}}W_{12}^{[2]} + \frac{\partial\mathcal{L}}{\partial z_2^{[2]}}W_{13}^{[2]}

$$

$$

\frac{\partial\mathcal{L}}{\partial a_2^{[1]}} = \frac{\partial\mathcal{L}}{\partial z_1^{[2]}}\frac{\partial z_1^{[2]}}{\partial a_2^{[1]}} + \frac{\partial\mathcal{L}}{\partial z_2^{[2]}}\frac{\partial z_2^{[2]}}{\partial a_2^{[1]}} + \frac{\partial\mathcal{L}}{\partial z_3^{[2]}}\frac{\partial z_3^{[2]}}{\partial a_2^{[1]}} = \frac{\partial\mathcal{L}}{\partial z_1^{[2]}}W_{21}^{[2]} + \frac{\partial\mathcal{L}}{\partial z_2^{[2]}}W_{22}^{[2]} + \frac{\partial\mathcal{L}}{\partial z_2^{[2]}}W_{23}^{[2]}

$$

$$

\frac{\partial\mathcal{L}}{\partial a_3^{[1]}} = \frac{\partial\mathcal{L}}{\partial z_1^{[2]}}\frac{\partial z_1^{[2]}}{\partial a_3^{[1]}} + \frac{\partial\mathcal{L}}{\partial z_2^{[2]}}\frac{\partial z_2^{[2]}}{\partial a_3^{[1]}} + \frac{\partial\mathcal{L}}{\partial z_3^{[2]}}\frac{\partial z_3^{[2]}}{\partial a_3^{[1]}} = \frac{\partial\mathcal{L}}{\partial z_1^{[2]}}W_{31}^{[2]} + \frac{\partial\mathcal{L}}{\partial z_2^{[2]}}W_{32}^{[2]} + \frac{\partial\mathcal{L}}{\partial z_2^{[2]}}W_{33}^{[2]}

$$

$$

\frac{\partial\mathcal{L}}{\partial a_4^{[1]}} = \frac{\partial\mathcal{L}}{\partial z_1^{[2]}}\frac{\partial z_1^{[2]}}{\partial a_4^{[1]}} + \frac{\partial\mathcal{L}}{\partial z_2^{[2]}}\frac{\partial z_2^{[2]}}{\partial a_4^{[1]}} + \frac{\partial\mathcal{L}}{\partial z_3^{[2]}}\frac{\partial z_3^{[2]}}{\partial a_4^{[1]}} = \frac{\partial\mathcal{L}}{\partial z_1^{[2]}}W_{41}^{[2]} + \frac{\partial\mathcal{L}}{\partial z_2^{[2]}}W_{42}^{[2]} + \frac{\partial\mathcal{L}}{\partial z_2^{[2]}}W_{43}^{[2]}

$$

因此：

$$

\begin{matrix} 

{\frac{\partial\mathcal{L}}{\partial a^{[1]}} = (\frac{\partial\mathcal{L}}{\partial a_1^{[1]}},\frac{\partial\mathcal{L}}{\partial a_2^{[1]}},\frac{\partial\mathcal{L}}{\partial a_3^{[1]}},\frac{\partial\mathcal{L}}{\partial a_3^{[1]}}) = (\frac{\partial\mathcal{L}}{\partial z_1^{[2]}},\frac{\partial\mathcal{L}}{\partial z_2^{[2]}},\frac{\partial\mathcal{L}}{\partial z_3^{[2]}})\begin{bmatrix} W_{11}^{(2)} & W_{21}^{(2)} & W_{31}^{(2)} & W_{41}^{(2)} \\ W_{12}^{(2)} & W_{22}^{(2)} & W_{32}^{(2)} & W_{42}^{(2)} \\ W_{13}^{(2)} & W_{23}^{(2)} & W_{33}^{(2)} & W_{43}^{(2)} \\ \end{bmatrix} = \frac{\partial\mathcal{L}}{\partial z^{[2]}}W^{[2]^T}} \\ 

\end{matrix}

$$

同理：

##### 反向传播梯度推导

###### 输出层（第 2 层）权重梯度

$$

\frac{\partial\mathcal{L}}{\partial W_{11}^{[2]}} = \frac{\partial\mathcal{L}}{\partial z_{1}^{[2]}}\frac{\partial z_{1}^{[2]}}{\partial W_{11}^{[2]}} + \frac{\partial\mathcal{L}}{\partial z_{2}^{[2]}}\frac{\partial z_{2}^{[2]}}{\partial W_{11}^{[2]}} + \frac{\partial\mathcal{L}}{\partial z_{3}^{[2]}}\frac{\partial z_{3}^{[2]}}{\partial W_{11}^{[2]}} = \frac{\partial\mathcal{L}}{\partial z_{1}^{[2]}}\frac{\partial z_{1}^{[2]}}{\partial W_{11}^{[2]}} + 0 + 0 = \frac{\partial\mathcal{L}}{\partial z_{1}^{[2]}}\frac{\partial z_{1}^{[2]}}{\partial W_{11}^{[2]}} = \frac{\partial\mathcal{L}}{\partial z_{1}^{[2]}}a_{1}^{[1]}

$$

这是因为 `W[11]^[2]` 仅与 `z[1]^[2]` 相关，`z[2]^[2]` 和 `z[3]^[2]` 不依赖于 `W[11]^[2]`，所以后两个偏导数均为 0。因为 `W^[2]` 的第 i 列仅贡献给 `z[i]^[2]`（即只有 `z[i]^[2]` 依赖于 `W^[2]` 的第 i 列），所以：

$$

\frac{\partial\mathcal{L}}{\partial W_{i1}^{[2]}} = \frac{\partial\mathcal{L}}{\partial z_{1}^{[2]}}a_{i}^{[1]}

$$

$$

\frac{\partial\mathcal{L}}{\partial W_{i2}^{[2]}} = \frac{\partial\mathcal{L}}{\partial z_{2}^{[2]}}a_{i}^{[1]}

$$

$$

\frac{\partial\mathcal{L}}{\partial W_{i3}^{[2]}} = \frac{\partial\mathcal{L}}{\partial z_{3}^{[2]}}a_{i}^{[1]}

$$

###### 矩阵形式

$$

\frac{\partial\mathcal{L}}{\partial W^{[2]}} =

\begin{bmatrix}

\frac{\partial\mathcal{L}}{\partial W_{11}^{[2]}} & \frac{\partial\mathcal{L}}{\partial W_{12}^{[2]}} & \frac{\partial\mathcal{L}}{\partial W_{13}^{[2]}} \\

\frac{\partial\mathcal{L}}{\partial W_{21}^{[2]}} & \frac{\partial\mathcal{L}}{\partial W_{22}^{[2]}} & \frac{\partial\mathcal{L}}{\partial W_{23}^{[2]}} \\

\frac{\partial\mathcal{L}}{\partial W_{31}^{[2]}} & \frac{\partial\mathcal{L}}{\partial W_{32}^{[2]}} & \frac{\partial\mathcal{L}}{\partial W_{33}^{[2]}} \\

\frac{\partial\mathcal{L}}{\partial W_{41}^{[2]}} & \frac{\partial\mathcal{L}}{\partial W_{42}^{[2]}} & \frac{\partial\mathcal{L}}{\partial W_{43}^{[2]}}

\end{bmatrix}

=

\begin{bmatrix}
