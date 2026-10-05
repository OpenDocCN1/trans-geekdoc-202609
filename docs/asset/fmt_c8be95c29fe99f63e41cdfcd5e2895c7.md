
**图 18.9** 带虚警、检测失败和飞机退出的目标跟踪 OUPM。飞机进入场景的速率为 $\lambda_a$，而每个时间步的概率为 $\alpha_e$。虚假光点（即不是由飞机产生的）以每个时间步 $\lambda_b$ 的速率均匀出现。飞机被检测到（即出现光点）的概率取决于其当前位置。

光点的起始点为一架飞机和一个时间步。因此，现在暂时省略先验分布，模型看起来如下：

```
guaranteed Aircraft $\lambda_a, A_b

X(a,t) ~ if t=0 then InitX($\mathcal{N}(FX(a,t-1), \Sigma_s)$)

#Blip(Source=a, Time=t) = 1

Z(b) ~ $\mathcal{N}(HX(Source(b), Time(b)), \Sigma_s)$
```

其中 $F$ 和 $\Sigma$ 是描述线性转移模型和转移噪声方差的矩阵，而 $H$ 和 $\Sigma$ 是传感器模型对应的矩阵。（见第 501 页。）

该模型与标准卡尔曼滤波的区别在于，有两个物体产生传感器读数。这意味着在任何时间步，对于哪个传感器产生了哪条读数都存在不确定性。该模型中的每个可能世界都包括飞机——由所有时间步的 $Source(b)$ 变量值定义——飞机和光点。图 18-b(c) 显示了两个关联假设。通常，对于 $n$ 个物体 $\mathcal{T}$ 个时间步，将光点分配给飞机的方法有 $(n!)^\mathcal{T}$ 种——这是一个巨大的数字。

描述的场景涉及 $n$ 架飞机在每个时间步产生 $n$ 个观测值。上述场景涉及存在虚警、检测失败和轨迹启动/终止的情况，这些现象在图 18.8(d) 中给出。OUPM 见图 18.9。

- 虚警
- 杂波
- 检测失败

# 第 18.3节 跟踪复杂世界

![](img/e36752d03ef5263fc4a8dddbd735be2d_658_0.png)

**图 18.10** 来自加利福尼亚州萨克拉门99号公路上相距两英里的 (a) 上游和 (b) 下监控摄像头的图像。框中的车辆在两个摄像头上都被识别出来。

## 18.3.2 示例：交通监控

图 18.10 显示了来自加州高速公路上两个相隔较远的摄像头的图像。在这一应用中，我们关注两个目标：估计在当前交通状况下从高速公路系统的某处到另一处所需的时间；以及衡量*需求*——即在每天的特定时间和特定几天，系统中任意两点之间行驶的车辆数量。这两个目标都需要在具有许多摄像头和每小时数千辆车辆的大范围内解决数据关联问题。

在视觉监控中，误报是由移动的影子、节节车辆、水洼中的反射等引起的；检测失败是由遮挡、雾、黑暗和缺乏视觉对比度引起的；而且车辆不断从可能未被监控的点进入和离开高速公路系统。此外，任何车辆的外观都会根据天气、光照条件以及图像中车辆的位置而发生剧变，且转移模型会随着交通拥堵的发生而变化。最后，在摄像头相距较远的密密交通中，汽车从一个位置行驶到下一个位置的转移模型中的预测误差远大于车辆之间的典型间距。尽管存在这些问题，现代数据关联算法已成功在真实场景中估计了交通参数。

数据关联是跟踪复杂世界的基础基础，因为没有它，就无法合并对任何给定对象的多次观测。当世界中的对象在其他复杂活动中相互作用时，理解世界需要将数据关联与第 18.2 节中的关系模型和开放宇宙概率模型相结合。这目前是一个活跃的研究领域。

# 第 18 章 概率编程

```
function GENERATE-IMAGE() returns an image with some letters

letters← GENERATE-LETTERS(10)

return RENDER-NOISY-IMAGE(letters, 328)
```

```
function GENERATE-LETTERS(λ) returns a vector of letters

n ~ Poisson(λ)

letters←

for i = 1 to n do

  letters[i] ~ UniformChoice({a,b,c,...})

return letters
```

```
function RENDER-NOISY-IMAGE(letters, width, height) returns a noisy image of the letters

clean_image← RENDER(letters, width, height, top=10, left=10)

noisy_image←

noise_variance ~ UniformReal(0.1, 1)

for row = 1 to width do

  noisy_image[row,col] ~ N(clean_image[row,col], noise_variance)

return noisy_image
```
