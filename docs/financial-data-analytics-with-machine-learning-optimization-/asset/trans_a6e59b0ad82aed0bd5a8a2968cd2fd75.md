

## FIGURE 5.8

在 CEV 模型（θ = 2）下，路径微分方法的收敛性（通过 Python 生成，由 [程序 5.31](#c05.xhtml#c05-gra-00031) 生成）；蓝色虚线表示精确值。

![FIGURE 5.8](images/c05-i0591.png)

## FIGURE 5.9

在 CEV 模型（θ = 2）下，路径微分方法的收敛性（通过 R 生成，由 [程序 5.32](#c05.xhtml#c05-gra-00032) 生成）；蓝色虚线表示精确值。

![FIGURE 5.9](images/c05f009.png)

## FIGURE 5.10

在 CEV 模型（θ = 1.8）下，路径微分方法的收敛性（通过 Python 生成，由 [程序 5.31](#c05.xhtml#c05-gra-00031) 生成）。

![FIGURE 5.10](images/c05f010.png)

## FIGURE 5.11

在 CEV 模型（θ = 1.8）下，路径微分方法的收敛性（通过 R 生成，由 [程序 5.32](#c05.xhtml#c05-gra-00032) 生成）。

![FIGURE 5.11](images/c05f011.png)

## FIGURE 5.12

在 CEV 模型（θ = 1）下，路径微分方法的收敛性（通过 Python 生成，由 [程序 5.31](#c05.xhtml#c05-gra-00031) 生成）。

![FIGURE 5.12](images/c05f012.png)

## FIGURE 5.13

在 CEV 模型（θ = 1）下，路径微分方法的收敛性（通过 R 生成，由 [程序 5.32](#c05.xhtml#c05-gra-00032) 生成）。

![FIGURE 5.13](images/c05f013.png)

## (III) 概率比法

设 S<sub>T</sub> 的密度函数为 g<sub>θ</sub>，其中 θ 为感兴趣的参数，暂且假设我们知道该表达式作为 θ 的函数。那么，预期折现收益可以表示为：

ψ(y) = ∫<sub>-∞</sub><sup>∞</sup> f(x)g<sub>θ</sub>(x)dx

此外，如果折现收益函数 f(x) 几乎处处连续，且 g<sub>θ</sub>(x) 关于 θ 可微，则预期折现收益关于 θ 的灵敏度可以计算为：

∂ψ(y)/∂θ = ∫<sub>-∞</sub><sup>∞</sup> f(x) ∂g<sub>θ</sub>(x)/∂θ dx = ψ(f(S<sub>T</sub>) ∂ln g<sub>θ</sub>(S<sub>T</sub>)/∂θ)

与路径微分方法类似，我们将价格灵敏度表示为期望，然后可以通过蒙特卡洛方法进行估计。概率比法涉及对 S<sub>T</sub> 的密度函数关于 θ 进行微分，而不是像路径微分方法那样对收益函数进行微分。

作为直接的示例，在 Black–Scholes 框架下，

