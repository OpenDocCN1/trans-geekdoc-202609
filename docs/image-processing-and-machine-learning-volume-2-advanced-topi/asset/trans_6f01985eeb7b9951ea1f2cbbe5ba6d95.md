


![](img/fa2d7e8bd88af7122f764c748b0a3723_223_0.png)

**图 6.2**
通过 SVD 分解截断进行过程近似。

## 6.4 用于图像压缩的 SVD

具有 SVD 分解的数据集的近似特性可用于压缩图像 [4]。这一特性表明，大型数据集保持一致的模式，仅凭这些模式的存在即可近似整个数据集。图像是具有固有模式和冗余信息的大型数据集。灰度图像可以被视为一个实值矩阵 \(\mathbf{X} \in \mathbb{R}^{m \times n}\)，其中 \(n\) 和 \(m\) 分别表示行数和列数。

假设图 6.3 所示的图像。该图像的分辨率为 960x1208 像素。为观察压缩效果，图像将被分解为其 SVD 分量。为此，假设图像存储在 MATLAB 变量 I1 中，将执行以下 MATLAB 命令：

```
X=I1;
[U, S, V]=svd(X);
```

一旦图像被分解为 U、S 和 V 分量，图像就通过对这些矩阵在不同级别进行截断来近似。为观察压缩级别，将选择 r = 15、50、100。为查看近似结果，应执行程序 6.1 的 MATLAB 代码。

程序 6.1 中有两个重要元素必须予以说明。第一个也是非常重要的一点是，将表示图像像素的值转换为浮点数。图像通常

### 程序 6.1 使用 SVD 分解进行图像压缩

```
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%
%% Program to calculate the SVD decomposition
%% for image compression proposes.
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%
%%
%% Erik Cuevas, Alma Rodríguez
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%
%%Acquire the image
Im=imread('I1.jpeg');
%%Convert the image to grayscale
I1=rgb2gray(Im);
%%Convert image to floating point
X=double(I1);
%%Get SVD components
[U,S,V]=svd(X);
%%The truncation point is defined
r=15;
%%The approximate data matrix is obtained with only r=15
elements
Xapprox15 = U(:,1:r)*S(1:r,1:r)*V(:,1:r)';
%%Converts the data array to integer
IR15=mat2gray(Xapprox15);
%%The image is shown
imshow(IR15)
r=50;
%%The approximate data matrix is obtained with only r=50
elements
Xapprox50 = U(:,1:r)*S(1:r,1:r)*V(:,1:r)';
%%Converts the data array to integer
IR50=mat2gray(Xapprox50);
figure;
%%The image is shown
imshow(IR50)
r=100;
%%The approximate data matrix is obtained with only r=100
elements
Xapprox100 = U(:,1:r)*S(1:r,1:r)*V(:,1:r)';
%%Converts the data array to integer
IR100=mat2gray(Xapprox100);
figure;
%%The image is shown
imshow(IR100)
```

![](img/fa2d7e8bd88af7122f764c748b0a3723_225_0.png)

原图

![](img/fa2d7e8bd88af7122f764c748b0a3723_225_1.png)

r = 15

![](img/fa2d7e8bd88af7122f764c748b0a3723_225_2.png)

r = 50

![](img/fa2d7e8bd88af7122f764c748b0a3723_225_3.png)

r = 100

图 6.3 返回不同截断值 r 的近似矩阵。

以数值格式表示，允许每个像素赋予 0 到 255 之间的值。该数值范围对应于整数。正因为如此，图像值被定义为整数。然而，为了将数据数组分解为其 SVD 分量，有必要将数组中的信息作为浮点元素进行操作。为执行此过程，使用 MATLAB 函数 double。另一方面，一旦构建了矩阵，给出了考虑截断级别 r 的近似数据 X̂，就有必要将数据转换为允许图像表示的整数数值类型。此过程由 MATLAB 函数 mat2gray 执行。

图 6.3 显示了不同截断值 r 的近似矩阵。在 r = 15 的情况下，很明显重建中使用的信息非常少。结果，图像中的对象几乎难以感知。在 r = 50 的情况下，虽然只考虑了 50 个元素，但似乎足以区分图像中存在的对象和字符。最后，在 r = 100 的情况下，图像实际上已经是原图。

## 6.5 主成分分析

降维问题代表了多元分析中最重要的方法之一 [5]。概括地说，可以将其表述如下：是否可以用少于观测变量数量的变量来描述某些数据中包含的信息？

主成分分析（PCA）从一个 n 行 p 列的（中心化）数据矩阵开始，该矩阵可被视为维度为 p 的随机向量的大小为 n 的样本，

```
\(\mathbf{X} = \left( X_1, ..., X_p \right)' .\) (6.7)
```

将其视为 X 的线性（一元）组合，

```
\(\mathbf{y} = \mathbf{X}'\mathbf{t},\) (6.8)
```

其中 t 是维度为 p 的权重向量。第一个主成分作为在归一化条件 t't = 1 下最大化 Y 方差的向量 t 的问题的解出现。换句话说，作为权重 t 函数的表达式 var(Y) 构成一个变分问题，其解是第一个主成分。这个问题等价于寻找 X 协方差矩阵的特征值和特征向量。因此，连续的主成分是通过 X 协方差矩阵的对角化得到的，

```
\(\mathbf{S} = \mathbf{T}\mathbf{\Lambda}\mathbf{T}',\) (6.9)
```

其中 T 是一个 p×p 正交矩阵，其列为主成分的系数。

## 6.6 通过协方差求主成分

为举例说明这些概念，假设以下协方差矩阵：

```
\(\mathbf{\Sigma} = \left( \begin{array}{ c c c } 3 & 1 & 1 \\ 1 & 3 & 1 \\ 1 & 1 & 5 \end{array} \right)\) (6.10)
```

该矩阵对应于均值为零的随机向量 X = (X1, X2, X3)'。

要在 MATLAB 中计算 \(\Sigma\) 的特征值和特征向量，可以使用 `eig` 函数来计算矩阵的特征值。

```
A = [3 1 1; 1 3 1; 1 1 5];
eig_values = eig(A) ;
```

\(\Sigma\) 的特征值，按从高到低排序，为 \(\lambda_1 = 6\)、\(\lambda_2 = 3\) 和 \(\lambda_3 = 2\)。相应的归一化特征向量为 \(\mathbf{e}_1 = (1,1,2)'/\sqrt{6}\)、\(\mathbf{e}_2 = (1,1,-1)'/\sqrt{3}\)、\(\mathbf{e}_3 = (1,-1,0)'/\sqrt{2}\)。

说明各成分解释的总方差比例的向量为 \(\mathbf{Y} = (Y_1, Y_2, Y_3)'\)。其主成分如下：

- \(Y_1 = \mathbf{e_1}'\mathbf{X} = \frac{1}{\sqrt{6}}(X_1 + X_2 + 2X_3)\)
- \(Y_2 = \mathbf{e_2}'\mathbf{X} = \frac{1}{\sqrt{3}}(X_1 + X_2 - X_3)\) (6.11)
- \(Y_3 = \mathbf{e_3}'\mathbf{X} = \frac{1}{\sqrt{2}}(X_1 - X_2)\)

总方差由以下确定：

\(VT(\Sigma) = \text{tr}(\Sigma) = 11\) (6.12)

第一个主成分解释的 \(VT(\Sigma)\) 比例定义为：

\(\frac{\text{var}(Y_1)}{VT(\Sigma)} = \frac{\lambda_1}{11} \simeq 54.5\%.\) (6.13)

同样，\(Y_2\) 和 \(Y_3\) 解释的比例分别为 \(27.3\%\) 和 \(18.2\%\)。

将原始向量 \(\mathbf{X}\) 的数据在前两个主成分平面上的表示，特别是在观测值 \(\mathbf{x} = (2,2,1)'\) 中。要在 \(Y_1\) 和 \(Y_2\) 的平面上表示 \(\mathbf{X}\)，必须沿 \(\mathbf{e}_1\) 和 \(\mathbf{e}_2\) 给定的方向对 \(\mathbf{X}\) 进行标量积运算。对于 \(\mathbf{x}\)，结果是点 \((y_1, y_2) = (\sqrt{6}, \sqrt{3})\)

根据表 6.1 中的数据，考虑变量 \(X_1 =\) 抵押贷款期限和 \(X_2 =\) 价格，并用 \(\mathbf{X}\) 表示向量 \((X_1, X_2)'\)。

在 MATLAB 中，可以使用 `cov()` 函数来计算一组数据的协方差矩阵。该函数有两个输入：数据，应为 \(n \times p\) 矩阵形式，其中 \(n\) 是观测数，\(p\) 是变量数；以及一个可选参数，用于指定数据的缩放方式（默认为 ‘unbiased’）。

