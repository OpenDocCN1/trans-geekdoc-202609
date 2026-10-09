

观察数据的概率。使用 sympy 符号化求解似然函数。将 SymPy 表示转换为基于 Numpy 的纯函数可调用表达式。在 $50$ 次成功试验（共 $100$ 次）下评估似然函数，此时 $\theta=0.5$。

2. 先验分布：贝塔分布。使用 sympy 符号化定义将作为我们**先验**分布的贝塔分布。将 SymPy 表示转换为基于 Numpy 的纯函数可调用表达式。在 $\theta=0.5, a: 2, b: 7$ 时评估贝塔分布。

3. 使用基于 Numpy 的函数绘制贝塔分布。

4. 后验分布：使用 sympy 将贝塔先验与二项似然相乘，符号化求解**后验**分布。将 SymPy 表示转换为基于 Numpy 的纯函数可调用表达式。在 $\theta:0.5$，$a:2, b:7$ 时评估后验分布。

5. 使用基于 Numpy 的函数绘制后验分布。

6. 证明后验分布对 $\theta$ 具有与先验分布相同的功能依赖性，并且它只是**另一个贝塔分布**。

7. 已知：
   - **先验分布**：Beta($\theta \ |a=2, b=7)=56\theta\left(-\theta+1\right)^{6}$ 以及：
   - **似然函数**：Bin($r=3|n=6, \theta ~$)$=19600 \theta^{3}\left(-\theta+1\right)^{47}$

   求出结果的后验分布并绘制其图像。

## 5.3 解答

### 5.3.1 自动微分，梯度下降
### 5.3.2 数值微分

**SOL-100 CH.SOL- 5.1.**

1. 公式为：

$$f^{\prime}(x)\approx\frac{f(x+h)-f(x)}{h} . \tag { 5 . 2 7 }$$

2. *该公式的主要问题是当 $h$ 值较小时会出现数值不稳定现象。*

3. *在某些数值软件系统中，数值 $\sqrt{2}$ 可能被表示为浮点数 $\approx 1.414213562$。因此，以下结果：*

$float(\sqrt{(\sqrt{2})}) * float(\sqrt{(\sqrt{2})})$ 可能等于 $\sim 2.000000446$。

# **SOL-101** ✏ **CH.SOL- 5.2.**

1. *瞬时变化率等于：*

$\underset{h \to 0}{\lim} \frac{f(a + h) - f(a)}{a + h - a}$. (5.28)

2. *$f(x)$ 在 $a$ 处的瞬时变化率通常也被称为 $f(x)$ 在 $a$ 处的切线。*

3. *给定函数 $f(x)$ 和点 $a$，$f(x)$ 在 $a$ 处的切线（图 5.12）为：一条与 $f(a)$ 接触但不穿过 $f(x)$（在 $a$ 附近足够范围内）的直线。*

![](img/574135cb1d7125b50cf484d943cdd676_165_0.png)

![](img/574135cb1d7125b50cf484d943cdd676_166_0.png)

## **5.3.3 有向无环图**

**SOL-102 ✍️ CH.SOL- 5.3.**

1. 定义为：

$$ f'(c) = \lim_{h \to 0} \frac{f(c + h) - f(c)}{h}. $$

2. 如果我们从左到右遍历图 5.3，我们推导出以下函数：

$$ g(x) = \frac{1}{\sqrt{x}}. \tag{5.29} $$

$$\begin{aligned} f'(9) &= \lim_{h \to 0} \frac{1 / \sqrt{9 + h} - 1 / \sqrt{9}}{h} \\ &= \lim_{h \to 0} \frac{\sqrt{9} - \sqrt{9 + h}}{\sqrt{9} \cdot \sqrt{9 + h} \cdot h} \\ &= \lim_{h \to 0} \frac{(3 - \sqrt{9 + h})(3 + \sqrt{9 + h})}{3 \sqrt{9 + h} \cdot (3 + \sqrt{9 + h}) \cdot h} \\ &= \lim_{h \to 0} \frac{9 - (9 + h)}{9 \sqrt{9 + h} \cdot h + 3 \cdot (9 + h) \cdot h} \\ &= \frac{1}{-9 \cdot 3 + 3 \cdot 9} \\ &= -\frac{1}{54} \end{aligned}$$

**SOL-103 ✍️ CH.SOL- 5.4.**

1. 函数 $g(x) = 2x^2 - x + 1$ 代表图 5.4 中所示的表达式图。

2. 根据定义：

$$f'(x) = \lim _ { h \to 0 } \frac { f ( x + h ) - f ( x ) } { x + h - x }$$

$$ = \lim _ { h \to 0 } \frac { 2 ( x + h ) ^ { 2 } - ( x + h ) + 1 - 2 x ^ { 2 } + x - 1 } { h }$$

$$ = \lim _ { h \to 0 } \frac { 2 ( x ^ { 2 } + 2 x h + h ^ { 2 } ) - x - h + 1 - 2 x ^ { 2 } + x - 1 } { h }$$

$$ = \lim _ { h \to 0 } \frac { 2 x ^ { 2 } + 4 x h + 2 h ^ { 2 } - x - h + 1 - 2 x ^ { 2 } + x - 1 } { h }$$

$$ = \lim _ { h \to 0 } \frac { 4 x h + 2 h ^ { 2 } - h } { h }$$

$$ = \lim _ { h \to 0 } 4 x + 2 h - 1$$

$$ = 4 x - 1 .$$

![](img/574135cb1d7125b50cf484d943cdd676_167_0.png)

![](img/574135cb1d7125b50cf484d943cdd676_167_1.png)

## 5.3.4 链式法则

**SOL-104 CH.SOL- 5.5.**

1. 链式法则指出，$E = E ( x , y )$ 对 $x$ 的偏导数可以通过另一个变量 $y = y ( x )$ 计算，如下所示：

$$\frac { \partial E } { \partial x } = \frac { \partial E } { \partial y } \cdot \frac { \partial y } { \partial x }$$

2. 例如，链式法则 $[ 8 ]$ 应用于神经网络中，用于计算因调整成本函数而导致的权重变化。该导数通过偏导数链（例如激活函数的偏导数）计算得出。

## **5.3.5**      泰勒级数展开

**SOL-105 CH.SOL- 5.6.**

1.

$$\frac {1}{1-x} = \sum _ {n = 0} ^ {\infty} x ^ {n} = 1 + x + x ^ {2} + x ^ {3} \quad (5.32) \, (当 - 1 < x < 1 时)$$

2.

$$e ^ {x} = \sum _ {n = 0} ^ {\infty} \frac {x ^ {n}}{n !} = 1 + x + \frac {x ^ {2}}{2 !} + \frac {x ^ {3}}{3 !} + \cdots$$   (5.33)

3.

$$\sin x = \sum _ {n = 0} ^ {\infty} \frac {(- 1) ^ {n}}{(2n + 1) !} x ^ {2n + 1} = x - \frac {x ^ {3}}{3 !} + \frac {x ^ {5}}{5 !} - \cdots$$  (5.34)

4.

$$\cos x = \sum _ {n = 0} ^ {\infty} \frac {(- 1) ^ {n}}{(2n) !} x ^ {2n} = 1 - \frac {x ^ {2}}{2 !} + \frac {x ^ {4}}{4 !} - \cdots$$  (5.35)

**SOL-106 CH.SOL- 5.7.**

$$\log x = \sum _ {n = 1} ^ {\infty} \frac {(- 1) ^ {n + 1} (x - 1) ^ {n}}{n} = (x - 1) - \frac {(x - 1) ^ {2}}{2} + \frac {(x - 1) ^ {3}}{3} - \frac {(x - 1) ^ {4}}{4} + \cdots$$  (5.36)

**SOL-107 CH.SOL- 5.8.**

*在这种情况下，可以计算所有导数：*

$$\begin{aligned} & f^{0}(x)=5 x^{2}-11 x+1, \\ & f^{0}(-3)=79, \\ & f^{1}(x)=10 x-11, \\ & f^{1}(-3)=-41, \\ & f^{2}(x)=10, \\ & f^{2}(-3)=10, \\ & f^{n}(x)=0, \forall n \geq 3 .\end{aligned}\tag{5.37}$$

**SOL-108**  CH.SOL- 5.9.

*直接答案是 1。请参考公式 5.35 以验证这一逻辑推论。*

**SOL-109**  CH.SOL- 5.10.

*通过使用公式 5.36，可以将 $x$ 替换为 $3 - x$，并在给定点 $x = 1$ 之前生成依赖于 $x$ 的结果的前 7 项。*

## 5.3.6 极限与连续性

**SOL-110**  CH.SOL- 5.11.

1. 对于不定式 0/0，洛必达法则成立。我们查看

$$\operatorname*{lim}_{x \rightarrow 3} \frac{3 x^{2} e^{x^{3}}}{3} = 9 e^{27},$$

它等于原始极限。

2. 再次得到中间结果 0/0，因此我们查看一阶导数

$$\operatorname*{lim}_{x \rightarrow 0} \frac{2 x e^{x}-1}{-3 \sin x-1}=1 .$$

原始极限也等于 1。

3. 这一次，中间形式是 \(\infty/\infty\)，洛必达法则同样适用。导数的商为

$$\frac{1 - \frac{1}{x}}{0.01x^{-99/100}} = 100(x - 1)x^{1/99}$$

当 \(x \to \infty\) 时，此值趋于 \(\infty\)，因此原始极限也等于 \(\infty\)。

## 5.3.7     偏导数

**SOL-111 \pencilicon CH.SOL- 5.12.**

1. 正确。

2. 通过将 $y$ 视为常数，可以推导出

$$\frac{\partial g}{\partial x} = 2xy + y . \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad (5.38)$$

**SOL-112 \pencilicon CH.SOL- 5.13.**

1.

$$\begin{aligned} \nabla f(x,y) &= \frac{\partial f}{\partial x}\mathbf{i} + \frac{\partial f}{\partial y}\mathbf{j} & \quad (5.39) \\ &= \left(y^{2}+3 x^{2}\right) \mathbf{i}+\left(2 x y-2 y\right) \mathbf{j} \end{aligned}$$

2. 可以证明在 $(-1, 0)$ 处 \(\nabla g(x, y) = (2xy + y^{2}) \mathbf{i} + (x^{2} + 2xy - 1) \mathbf{j}\) 等于 \((0, 0)\)。根据方向导数的定义：

$$\frac{(0,0) \cdot (1,1)}{|(1,1)|} = 0 \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad (5.40)$$

**SOL-113 CH.SOL- 5.14.**

$$\begin{gathered} \frac{\partial f}{\partial x}=6 \sin (x-y) \cos (x-y) \\ \frac{\partial f}{\partial y}=-6 \sin (x-y) \cos (x-y) \end{gathered}$$

(5.41)

**SOL-114 CH.SOL- 5.15.**

$$\begin{gathered} \frac{\partial z}{\partial x}=2 \cos x \sin y \\ \frac{\partial z}{\partial y}=2 \sin x \cos y \end{gathered}$$

(5.42)

## 5.3.8 优化

**SOL-115 CH.SOL- 5.16.**

1. 函数仅在 $x \neq - 2$ 处定义，定义域为：$(-\infty, -2) \cup (-2, +1)$。

2. 通过简单的基于商的推导：

$$f^{\prime}(x)=\frac{2(x+2)(2x-1)}{(x+2)^{4}}.$$

(5.43)

即，除了未定义的 $x = - 2$ 之外，应考虑 $x = 0.5$ 的临界点。对于 $x > 0.5$，导数为正且函数递增，这与 $x < 0.5$ 的情况相反。

3. 请求的坐标是 $(0.5, 0.2)$。

**SOL-116 CH.SOL- 5.17.**

