

146 T. P. Fowder, L. Babooram, M. N-U-D-Ibn Nazir Rosun and M. Indoondom

```math
$$(v,h) = \sum_{i\in visible} a_{iv}v_i - \sum_{j\in hidden} b_{hj}h_j - \sum_{l,j} v_{lj}h_jw_{ij} \quad (3.6)$$
```

其中，

- $v_i$ - 可见单元 $i$ 的二值状态
- $h_j$ - 隐藏单元 $j$ 的二值状态
- $a_i$ - 可见单元 $i$ 的偏置
- $b_j$ - 隐藏单元 $j$ 的偏置
- $w_{ij}$ - 可见单元 $i$ 与隐藏单元 $j$ 之间的权重

神经网络使用以下能量函数为可见和隐藏向量的每种组合分配概率：

```math
$$p(v,h) = \frac{1}{Z}e^{-E(v,h)} \quad (3.7)$$
```

$Z$ 被称为配函数，通过对可见和隐藏向量的每种组合求和得到：

```math
$$Z = \sum_{v,h} e^{-E(v,h)} \quad (3.8)$$
```

神经网络通过对所有可能的隐藏向量求和，为可见向量 $v$ 分配概率：

```math
$$p(v) = \frac{1}{Z}\sum_{h} e^{-E(v,h)} \quad (3.9)$$
```

训练向量的对数概率对重的导数给出：

```math
$$\frac{\partial \log p(v)}{\partial w_{ij}} = \langle v_{lj}h_j\rangle_{data} - \langle v_{lj}h_j\rangle_{model} \quad (3.10)$$
```

角括号表示在随后的下标指定的分布下的期望。
因此，在训练数据集的概率上执行随机最梯度上升的学习规则如下：

```math
$$\Delta w_{ij} = \alpha(\langle v_{lj}h_j\rangle_{data} - \langle v_{lj}h_j\rangle_{model}) \quad (3.11)$$
```

## 机器学习算法

其中，

$\alpha$ - 学习率

可以从模型分布执行 Gibbs 采样，因为很难获得 $\langle v_{ij}h_j \rangle_{model}$ 的无偏样本 [21]。因此，可见单元的状态对应于一个训练向量以获取重构 $\langle v_{ij}h_j \rangle_{recon}$ 代替 [21]。因此，学习规则变为：

```math
$$\Delta w_{ij} = \alpha(\langle v_{ij}h_j \rangle_{data} - \langle v_{ij}h_j \rangle_{recon}) \quad (3.12)$$
```

可以使用来自 [22] 的包在 MATLAB 中实现 RBM。该包包含一个文件夹，其中包含样本图像训练集、用于实现 RBM 的用户定义函数以及用于测试 RBM 的图像脚本。RBM 旨在通过重建输入来识别数据集中的模式。可见层将输入编码为一组数字。这组数字用于通过从隐藏层到可见层的反向传播重新生成输入 [22]。

在列表 3.10 的主脚本开始处，用户定义函数被添加到搜索路径中，并指定了包含训练集的文件夹。然后将训练集中的图像设置为相同大小，以提高训练过程的准确性。通过将彩色照片转换为灰度来简化系统：

### 列表 3.10: 受限玻尔兹曼机-RBM: 加载训练数据

```matlab
addpath('RBM'); % 将包含用户定义的 RBM 文件夹添加到搜索路径
pathname= uigetdir; % 选择包含训练集的文件夹
allfiles= dir(fullfile(pathname,'*.jpg'));
tr=[];
gamma=[70]; 定义每个图像的大小
for i=1:size(allfiles,1)
x=imread(fullfile(pathname,allfiles(i).name));
x=resize(x,gamma); % 将训练集调整为统一大小
x=rgb2gray(x); % 将彩色图像转换为灰度
x=double(x);
tr=[tr; x];% 构建训练集
end
```

然后使用列表 3.11 给出的代码设置训练参数：

### 列表 3.11. 受限玻尔兹曼机- 定义训练参数

| %% 训练选项 | 描述 |
| :--- | :--- |
| Options.max_iter=200; | % 最大学习迭代次数 |
| Options.N_gs=100; | % Gibbs 采样步数 |
| Options.Nneurons=gamma(1); | % 隐藏层神经元数量 |
| Options.eps=0.01; | % 学习率 |
| Options.Sz_mb=10; | % 数据小批量的大小 |

使用列表 3.12 给出的代码启动 RBM 的训练：

### 列表 3.12. 受限玻尔兹曼机- 训练 RBM

| %% 训练过程 | 描述 |
| :--- | :--- |
| net=RBM_TB(xtr,Options); | % 使用训练集和用户定义参数训练 RBM |

然后可以使用列表 3.13 中的代码通过重新生成测试图像 (Test.jpg) 来测试 RBM。测试图像必须设置为与训练集图像相同的尺寸和颜色，RBM 才能准确工作：

### 列表 3.13. 受限玻尔兹曼机- 测试 RBM

| %% 预测 | 描述 |
| :--- | :--- |
| xp=imread('Test.jpg'); | |
| xp=resize(xp,gamma); | |
| xp1=rgb2gray(xp); | |
| xp=double(xp1); | |
| [y]=RBM_RECONSTRUCT(net,xp); | |

### 列表 3.14. 受限玻尔兹曼机- 显示结果

| %% 插图 | 描述 |
| :--- | :--- |
| subplot(221) | |
| imshow(y) | |
| title('generated input') | |
| subplot(222) | |
| imshow(xp1) | |
| title('original input') | |
| subplot(2,2,3:4) | |
| plot(1:length(net.hist),net.hist,'LineWidth',2) | |
| xlabel('iterations') | |
| ylabel('RMSE') | |

