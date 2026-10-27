
CRC Press
Taylor & Francis Group
6000 Broken Sound Parkway NW, Suite 300
Boca Raton, FL 33487-2742

© 2017 by Taylor & Francis Group, LLC
CRC Press is an imprint of Taylor & Francis Group, an Informa business

No claim to original U.S. Government works

Printed on acid-free paper
Version Date: 20160404

International Standard Book Number-13: 978-1-4987-3859-0 (Ancillary)

本书包含来自真实且备受推崇的来源的信息。已做出合理努力以发表可靠的数据和信息，但作者和出版商不能承担所有材料有效性或其使用后果的责任。作者和出版商已尝试追溯本出版物中转载材料的版权持有者，并在未获得以此形式出版许可的情况下向版权持有者道歉。如果有任何版权材料未得到承认，请撰写信函告知我们，以便我们在今后的再版中予以纠正。

除美国版权法允许的情况外，未经出版商书面许可，本书的任何部分不得以任何电子、机械或其他方式，包括复印、缩微胶片和录音，或以任何信息存储或检索系统的方式，以印刷、复制、传输或利用的形式重新印刷、复制、传输或使用，无论是现在已知还是以后发明的，包括复印、缩微拍摄和录音。

如需获得复印或以电子方式使用本作品材料的许可，请访问 www.copyright.com (http://www.copyright.com/) 或联系 Copyright Clearance Center, Inc. (CCC)，地址为 222 Rosewood Drive, Danvers, MA 01923，电话 978-750-8400。CCC 是一个非营利组织，为各类用户提供许可和注册服务。对于已获得 CCC 复印许可的组织，已安排了单独的付款系统。

商标声明：产品或公司名称可能是商标或注册商标，仅用于识别和说明目的，无侵权意图。

访问 Taylor & Francis 网站 http://www.taylorandfrancis.com 和 CRC Press 网站 http://www.crcpress.com

## Chapter 1

### EX 1.1

\(w_0\) 的一个较大正值和 \(w_1\) 的一个较小负值。这些反映了 \(t\) 轴上的高截距（对应于 \(x = 0\) 时的理论获胜时间）以及随时间推移获胜时间的小幅下降。

### EX 1.2

以下方法即可实现：

```matlab
% Attributes are stored in Nx1 vector x
% Targets are stored in Nx1 vector t
xb = mean(x);
tb = mean(t);
x2b = mean(x.*x);
xtb = mean(x.*t);
w1 = (xtb - xb*tb) / (x2b-xb^2);
w0 = tb-w1*xb;
% Plot the data
plot(x,t,'b.','markersize',25);
% Plot the model
hold on;
plot(x,w0+w1*x,'r','linewidth',2);
```

### EX 1.3

我们需要求 \(\mathbf{w}^{\mathrm{T}}\mathbf{X}^{\mathrm{T}}\mathbf{X}\mathbf{w}\)。我们从 \(\mathbf{X}^{\mathrm{T}}\mathbf{X}\) 开始。将 \(\mathbf{X}^{\mathrm{T}}\) 与 \(\mathbf{X}\) 相乘得到：

\[
\mathbf{X}^{\mathrm{T}}\mathbf{X} =
\begin{bmatrix}
\sum_{n=1}^{N} x_{n1}^{2} & \sum_{n=1}^{N} x_{n1} x_{n2} \\
\sum_{n=1}^{N} x_{n2} x_{n1} & \sum_{n=1}^{N} x_{n2}^{2}
\end{bmatrix}
\]

将此结果与 \(\mathbf{w}\) 相乘得到：

\[
\mathbf{X}^{\mathrm{T}}\mathbf{X}\mathbf{w} =
\begin{bmatrix}
w_0 \sum_{n=1}^{N} x_{n1}^{2} + w_1 \sum_{n=1}^{N} x_{n1} x_{n2} \\
w_0 \sum_{n=1}^{N} x_{n2} x_{n1} + w_1 \sum_{n=1}^{N} x_{n2}^{2}
\end{bmatrix}
\]

最后，用 \(\mathbf{w}^{\mathrm{T}}\) 左乘得到：

\[
\mathbf{w}^{\mathrm{T}}\mathbf{X}^{\mathrm{T}}\mathbf{X}\mathbf{w}
=
w_0\left(w_0\sum_{n=1}^{N}x_{n1}^{2}+w_1\sum_{n=1}^{N}x_{n1}x_{n2}\right)
+
w_1\left(w_0\sum_{n=1}^{N}x_{n2}x_{n1}+w_1\sum_{n=1}^{N}x_{n2}^{2}\right)
\]

\[
=
w_0^2\sum_{n=1}^{N}x_{n1}^{2}
+
2w_0w_1\sum_{n=1}^{N}x_{n1}x_{n2}
+
w_1^2\sum_{n=1}^{N}x_{n2}^{2}
\]

如所需。

### EX 1.4

让我们先计算 \(\mathbf{X}\mathbf{w}\)：

\[
\mathbf{X}\mathbf{w}
=
\begin{bmatrix}
w_0x_{11}+w_1x_{12} \\
w_0x_{21}+w_1x_{22} \\
\vdots \\
w_0x_{N1}+w_1x_{N2}
\end{bmatrix}
\]

因此

\[
(\mathbf{X}\mathbf{w})^{\mathrm{T}}
=
[
w_0x_{11}+w_1x_{12},\;
w_0x_{21}+w_1x_{22},\;
\ldots,\;
w_0x_{N1}+w_1x_{N2}
]
\]

最后，计算 \(\mathbf{w}^{\mathrm{T}}\mathbf{X}^{\mathrm{T}}\)：

\[
\mathbf{w}^{\mathrm{T}}\mathbf{X}^{\mathrm{T}}
=
[
w_0x_{11}+w_1x_{12},\;
w_0x_{21}+w_1x_{22},\;
\ldots,\;
w_0x_{N1}+w_1x_{N2}
]
\]

如所需。

### EX 1.5

从 \(\sum_n \mathbf{x}_n t_n\) 开始。其结果是一个与 \(\mathbf{x}\) 相同大小的列向量（2 × 1）。现在，利用 \(\mathbf{X}\) 的定义，

\[
\mathbf{X}^{\mathrm{T}}
=
\begin{bmatrix}
x_{11},x_{21},\ldots,x_{N1} \\
x_{12},x_{22},\ldots,x_{N2}
\end{bmatrix}
\]

这是一个 2 × \(N\) 矩阵。将它与 \(\mathbf{t}\) 相乘得到一个 2 × 1 向量，看起来如下：

\[
\mathbf{X}^{\mathrm{T}}\mathbf{t}
=
\begin{bmatrix}
\sum_{n=1}^{N}x_{n1}t_n \\
\sum_{n=1}^{N}x_{n2}t_n
\end{bmatrix}
\]

这就是 \(\sum_n\mathbf{x}_n t_n\) 如所需。第二种情况，\(\mathbf{X}^{\mathrm{T}}\mathbf{X}\mathbf{w}\)。我们已经知道 \(\mathbf{X}^{\mathrm{T}}\mathbf{X}\mathbf{w}\) 是什么（练习 1.3）

\[
\mathbf{X}^{\mathrm{T}}\mathbf{X}\mathbf{w}
=
\begin{bmatrix}
w_0\sum_{n=1}^{N}x_{n1}^{2}+w_1\sum_{n=1}^{N}x_{n1}x_{n2} \\
w_0\sum_{n=1}^{N}x_{n2}x_{n1}+w_1\sum_{n=1}^{N}x_{n2}^{2}
\end{bmatrix}
\]

现在，\(\mathbf{x}_n\mathbf{x}_n^{\mathrm{T}}\) 是以下矩阵：

\[
\mathbf{x}_n\mathbf{x}_n^{\mathrm{T}}
=
\begin{bmatrix}
x_{n1}^{2} & x_{n1}x_{n2} \\
x_{n2}x_{n1} & x_{n2}^{2}
\end{bmatrix}
\]

将它与 \(\mathbf{w}\) 相乘得到：

\[
\mathbf{x}_n\mathbf{x}_n^{\mathrm{T}}\mathbf{w}
=
\begin{bmatrix}
w_0x_{n1}^{2}+w_1x_{n1}x_{n2} \\
w_0x_{n2}x_{n1}+w_1x_{n2}^{2}
\end{bmatrix}
\]

对 \(N\) 项求和就得到我们之前推导的矩阵。

### EX 1.6

代码如下：

```matlab
%% Women's 100m data
% Load all Olympic data
load olympics;
% Copy the necessary variables
x = female100(:,1); % Olympic year
t = female100(:,2); % Winning time
% Augment x
X = [repmat(1,size(x)) x];
% Get solution
w = inv(X'*X)*X'*t;
```

拟合模型为：

\[
t=40.9242-0.0151x
\]

### EX 1.7

将 2012 年和 2016 年代入上述表达式，得到的获胜时间分别为 10.5997 和 10.5394。

### EX 1.8

男子模型为：

\[
t=36.4165-0.0133x
\]

女子模型为：

\[
t=40.9242-0.0151x
\]

女子的用时下降速度快于男子。因此，在使获胜时间相同的 \(x\) 之后的第一个奥运会上，女子将更快：

\[
\begin{aligned}
40.9242-0.0151x &= 36.4165-0.0133x \\
x &= 2589
\end{aligned}
\]

2589 之后的下一个奥运年份（假设每四年举办一次）是 2592 年。获胜时间是不切实际的快速，女子为 1.8580 秒，男子为 1.8628 秒。

### EX 1.9

代码如下（synthdata_cv.m）：

```matlab
clear all;close all;
load synthdata

% Augment x
X = repmat(1,size(x));
for k = 1:4
    X = [X x.^k];
end

% Fit the model
w = inv(X'*X)*X'*t;

% Randomise the data order
N = size(X,1);
order = randperm(N);
sizes = repmat(floor(N/10),1,10);
sizes(end) = sizes(end) + N-sum(sizes);
sizes = [0 cumsum(sizes)];

X = repmat(1,size(x));

loss = zeros(4,10);
for poly_order = 1:4
    % Augment x
    X = [X x.^poly_order];
    for k = 1:10 % 10-fold CV
        % Extract the train and test data
        traindata = X(order,:);
        traint = t(order);
        testdata = X(order(sizes(k)+1:sizes(k+1)),:);
        testt = t(order(sizes(k)+1:sizes(k+1)));
        traindata(sizes(k)+1:sizes(k+1),:) = [];
        traint(sizes(k)+1:sizes(k+1)) = [];
        
        % Fit the model
        w = inv(traindata'*traindata)*traindata'*traint;
        
        % Compute loss on test data
        predictions = testdata*w;
        loss(poly_order,k) = sum((predictions - testt).^2);
    end
end

% Plot the loss
plot([1:4],mean(loss,2));
```

### EX 1.10

总损失为

\[
\mathcal{L} = \sum_{n=1}^{N} (t_n - \mathbf{w}^T \mathbf{x}_n)^2.
\]

以矩阵形式写出、求导并求解得到：

\[
\mathcal{L} = (\mathbf{t} - \mathbf{X}\mathbf{w})^T (\mathbf{t} - \mathbf{X}\mathbf{w})
= \mathbf{t}^T \mathbf{t} - 2 \mathbf{w}^T \mathbf{X}^T \mathbf{t} + \mathbf{w}^T \mathbf{X}^T \mathbf{X} \mathbf{w}
\]

\[
\frac{\partial \mathcal{L}}{\partial \mathbf{w}} = -2 \mathbf{X}^T \mathbf{t} + 2 \mathbf{X}^T \mathbf{X} \mathbf{w} = 0
\]

\[
\mathbf{w} = (\mathbf{X}^T \mathbf{X})^{-1} \mathbf{X}^T \mathbf{t}.
\]

这与平均损失得到的 \(\mathbf{w}\) 值相同。这并不令人惊讶，因为我们所做的只是将损失乘以一个常数，这不会改变 \(\mathbf{w}\) 在最小值处的值。
