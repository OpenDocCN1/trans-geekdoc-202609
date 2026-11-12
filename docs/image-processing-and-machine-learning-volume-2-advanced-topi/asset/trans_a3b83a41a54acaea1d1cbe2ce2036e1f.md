
d_3 = m_3^R + D(x, y+1)
d_4 = m_4^R + D(x-1, y+1)
D(x,y) = min(d_1, d_2, d_3, d_4, D(x,y))
end
end
4: 返回 D 的值。

使用曼哈顿距离的 Chamfer 算法使用定义如下的掩模：

![](img/fa2d7e8bd88af7122f764c748b0a3723_178_0.png)

同样，如果使用欧氏距离，则掩模定义如下：

![](img/fa2d7e8bd88af7122f764c748b0a3723_178_1.png)

使用这些掩模，可以明显地通过点到点欧氏距离获得真实距离的近似值。然而，与对应于欧氏距离的掩模相比，比为曼哈顿距离定义的掩模获得了更准确的估计。图 4.15 显示了使用每个掩模的结果。

## 4.3.2.1 距离变换的实现

本节展示了如何使用算法 4.2 中定义的 Chamfer 方法实现距离变换。程序 4.8 显示了该算法在 MATLAB 中的实现。

![](img/fa2d7e8bd88af7122f764c748b0a3723_179_0.png)

FIGURE 4.15
使用 Chamfer 算法的距离变换。(a) 原始图像，(b) 使用曼哈顿距离掩模的距离变换，(c) 使用欧氏距离掩模的距离变换。

```matlab
PROGRAM 4.8 MATLAB PROGRAM TO CALCULATE THE DISTANCE TRANSFORMATION USING THE CHAMFER ALGORITHM. IN THE ALGORITHM, THE MANHATTAN APPROACH IS CONSIDERED A FUNCTION OF DISTANCE
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% Program to calculate the distance transformation
% of a binary image using the algorithm
% Chamfer
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% Erik Cuevas, Alma Rodríguez
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% Gets the size of the binary image
[m n]=size(Ib);
% The distance matrix D is defined
D=zeros(size(Ib));
%Step 1: Initialization
for re=1:m
for co=1:n
if (Ib(re,co))
D(re,co)=0;
else
D(re,co)=300;
end
end
end
%The mask MI is defined, considering the
%Manhattan distance
mI1=1;
mI2=2;
mI3=1;
mI4=2;
%Step 2. The image with the mask is processed
% from left to right and from top to bottom.
for re=2:m
    for co=2:n-1
        if(D(re,co)>0)
            d1=mI1+D(re,co-1) ;
            d2=mI2+D(re-1,co-1) ;
            d3=mI3+D(re-1,co) ;
            d4=mI4+D(re-1,co+1) ;
            Dis= [d1 d2 d3 d4] ;
            D(re,co)=min(Dis) ;
        end
    end
end
%The MD mask is defined, considering the
%Manhattan distance
mD1=1;
mD2=2;
mD3=1;
mD4=2;
%Step 3. The image with the mask is processed
% right to left and bottom to top.
for re=m-1:-1:1
    for co=n-1:-1:2
        if(D(re,co)>0)
            d1=mD1+D(re,co+1) ;
            d2=mD2+D(re+1,co+1) ;
            d3=mD3+D(re+1,co) ;
            d4=mD4+D(re+1,co-1) ;
            Dis=[d1 d2 d3 d4 D(re,co)] ;
            D(re,co)=min(Dis) ;
        end
    end
end
% The results are displayed
F=mat2gray(D) ;
imshow(F)
```

## 4.4 Chamfer 索引关系

一旦通过 Chamfer 解释了距离变换，就可以将其用作二进制图像之间的比较索引。Chamfer 比率索引 Q(r,s) 使用距离变换来定位二进制图像和二进制参考模式具有最大相似性的点。

在 Chamfer 关系索引方法中，相似性标准基于与参考模式相比较的图像段中每个像素的距离值之和。由此，计算移动图像段所需的总距离，以找到最大相似性。

在该方法中，二进制参考模式 Rb(i,j) 在图像 Ib(r,s) 上位移。然后，在 Rb(i,j) 邻域内的每个像素处，计算图像 Ib(r,s) 中像素的距离之和。该公式可定义如下：

$$Q(x,y) = \frac{1}{K} \sum_{(i,j) \in FG(R)} D(r+i, s+j)$$ (4.21)

其中 K = |FG(R)| 对应于模式 Rb(i,j) 中值为 1 的像素数量。

计算 Chamfer 比率索引 Q(r,s) 的完整过程在算法 4.3 中总结。如果在 Ib(r,s) 的某个位置，模式 Rb(i,j) 中所有值为 1 的像素都与图像 Ib(r,s) 被覆盖部分的像素重合，则距离之和为零，这表示两个元素之间的完美相似性。模式 Rb(i,j) 中值为 1 的像素与图像 Ib(r,s) 中像素不相符越多，距离之和的值就越大，这意味着 Ib(r,s) 和 Rb(i,j) 之间的信息内容差异更大。当 Q(r,s) 取最小值时，达到最佳相似性索引。这可以表述为如下：

$$p_{opt} = (r_{opt}, s_{opt}) = \min(Q(r,s))$$ (4.22)

如果将图 4.16a 所示的二进制图像作为示例，并将图 4.16b 作为参考模式，则 Chamfer 比率索引 Q(r,s) 的计算将由图 4.16c 表示，而图 4.16d 表示 Q(r,s) 的曲面。

在图 4.16c 和 d 中，可以观察到 Chamfer 关系索引值的计算给出了一个平滑变化的相似性指标。红点显示了

### ALGORITHM 4.3 计算 Chamfer 比率索引的算法

Chamfer 比率索引 ($I_b(r,s), R_b(i,j)$)

$I_b(r,s)$ 维度为 $an_l \times al_l$ 的二进制图像

$R_b(i,j)$ 维度为 $an_R \times al_R$ 的二进制参考模式

- 1: **步骤 1**。从图像 $I_b(r,s)$ 获得距离变换 $D(r,s)$（参见算法 4.2）

- 2: 获得模式 $R_b(i,j)$ 中值等于 1 的像素数量 $K$。

- 3: **步骤 2**。计算 Chamfer 比率索引 $Q(r,s)$ 的值。

- 4: for $r \leftarrow 1,2,\dots,al_l - al_R$ do
    for $s \leftarrow 1,2,\dots,an_l - an_R$ do
    计算 $Q(r,s)$ 的值。
    sumadis=0
    for $i \leftarrow 1,2,\dots,al_R$ do
        for $j \leftarrow 1,2,\dots,an_R$ do
        if($R_b(i,j) = 1$) do
        sumadis=sumadis+$D(r+i,s+j)$
        end
        end
    end
    $Q(r,s) = $ sumadis/K
    end
end

- 5: 返回 $Q$ 的值。

图像 $I_b(r,s)$ 和参考模式 $R_b(i,j)$。这个索引的一个明显问题是它变化非常平滑，这至少在可见地阻碍了全局极小值的识别。然而，如果只考虑那些级别最小的点，如图 4.17 所示，这些点将对应于与参考模式显示更好相似性的图形。

![](img/fa2d7e8bd88af7122f764c748b0a3723_183_0.png)

![](img/fa2d7e8bd88af7122f764c748b0a3723_183_1.png)

![](img/fa2d7e8bd88af7122f764c748b0a3723_183_2.png)

![](img/fa2d7e8bd88af7122f764c748b0a3723_183_3.png)

FIGURE 4.16
Chamfer 比率索引的计算。(a) 二进制图像，(b) 参考模式，(c) Chamfer 比率索引 Q(r, s) 的值，(d) Q(r, s) 的曲面。

![](img/fa2d7e8bd88af7122f764c748b0a3723_183_4.png)

FIGURE 4.17
Chamfer 比率索引作为最小值等值线的表示。

在图 4.17 中可以看到，与本章其他算法一样，最大相似性点表示与参考模式具有相同维度的窗口的左上角。

二进制图像比较的 Chamfer 关系索引方法不能被视为一种能够识别几乎任何二进制模式的神奇方法，但在特定应用的某些限制条件下工作良好。当要识别的模式被缩放、旋转或具有某种失真时，该方法会出现问题。

由于 Chamfer 比率索引方法基于值为 1 的像素的距离，其结果对图像中包含的噪声和随机伪影非常敏感。减少此问题的一个可能解决方案是，使用生成的距离值的均方根，而不是距离的线性和（方程 4.21）。该模型可由以下方程定义：

$$
Q_{rms}(r,s) = \sqrt{\frac{1}{K} \sum_{(i,j)\in FG(R)} (D(r+i, s+j))^2} \tag{4.23}
$$

### 4.4.1 Chamfer 关系索引的实现

本节展示了如何实现算法 4.3 中定义的 Chamfer 关系索引。程序 4.9 显示了如何在 MATLAB 中实现算法 4.3。

```
PROGRAM 4.9 MATLAB PROGRAM FOR
CALCULATING THE CHAMFER RATIO INDEX
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% Program to calculate the Chamfer ratio index
% Q(r,s) from a binary image and a pattern.
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% Erik Cuevas, Alma Rodríguez
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%Get the size of the binary image
[m n]=size(BW) ;
%The size of the reference pattern is obtained
[mt nt]=size(T) ;
%It is obtained the number of ones within
%the reference pattern
[dx dy]=find(T) ;
[K l]=size(dx) ;
%Se inicializan variables
suma=0;
Q=zeros (m-mt,n-nt) ;
```
