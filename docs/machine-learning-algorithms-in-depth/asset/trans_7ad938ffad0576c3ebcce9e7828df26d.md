
![](img/325742126d3ff007c6c385f4ffb5c3be_226_0.png)

**图 9.7** 图 Lasso 估计的精度矩阵（左）和股票聚类（右）

图 9.7 中精度矩阵中的边值大于阈值对应于连通分量，我们可以据此计算股票聚类，如图所示的右侧所示。在下一节中，我们将学习一种称为模拟退火的能量最小化算法。

## 9.4 模拟退火

*模拟退火 (SA)* 是一种启发式搜索方法，允许偶尔向较不利的状态转换以逃离局部最优。我们可以将 SA 形式化为具有温度参数 *T* 的能量最小化问题，如下所示。

$$\alpha = \exp\left\{\frac{E_{old}-E_{new}}{T}\right\}$$

$$p = \min(1,\alpha) \tag{9.19}$$

当我们转换到新状态时，我们希望新状态的能量更低——在这种情况下，α > 1 且 p = 1——意味着我们以概率 p = 1 接受状态转换。另一方面，如果新状态的能量更高，这将导致 α < 1，在这种情况下，我们以概率 p = α 接受转换。换句话说，我们以与状态间能量差成正比且与温度参数 T 成反比的概率接受不利转换。最初，温度 T 较高，允许进行许多随机转换。随着温度降低（根据冷却计划），能量差异变得更加明显。公式 9.19 中的表述使模拟退火能够逃离局部最优。我们现在准备查看图 9.8 中的伪代码。

### 图 9.8 模拟退火伪代码

simulated_annealing 类包含主要的 run 函数。我们首先初始化退火温度 T 并在初始位置评估我们的目标函数。回想一下，我们感兴趣的是在目标函数表示的复杂能量景观中找到一个最小点。我们从提议分布中采样以获得一组新的坐标并评估提议坐标的能量。我们检查收敛性以决定是否跳出循环或继续。接下来，我们计算模拟退火转移概率 alpha，即旧能量状态与新能量状态之差除以温度 T。在 r > 1 的情况下，我们以概率 1 接受低能量状态，而在 0 < r < 1 的情况下（即新状态的能量更高），我们以概率 r = α 接受转换。最后，我们根据冷却计划调整温度，并在收敛后返回最优坐标（即模拟退火找到的最小能量所对应的坐标）。我们现在准备从头开始实现模拟退火算法，如下所示。

### 列表 9.5 模拟退火

```
import numpy as np
import matplotlib.pyplot as plt

np.random.seed(42)
```

```python
class simulated_annealing():
    def __init__(self):
        self.max_iter = 1000
        self.conv_thresh = 1e-4
        self.conv_window = 10

        self.samples = np.zeros((self.max_iter, 2))
        self.energies = np.zeros(self.max_iter)
        self.temperatures = np.zeros(self.max_iter)

    def target(self, x, y):
        z = 3*(1-x)**2 * np.exp(-x**2 - (y+1)**2) \
            - 10*(x/5 - x**3 - y**5) * np.exp(-x**2 - y**2) \
            - (1/3)*np.exp(-(x+1)**2 - y**2)
        return z

    def proposal(self, x, y):
        mean = np.array([x, y])
        cov = 1.1 * np.eye(2)
        x_new, y_new = np.random.multivariate_normal(mean, cov)
        return x_new, y_new

    def temperature_schedule(self, T, iter):
        return 0.9 * T

    def run(self, x_init, y_init):

        converged = False
        T = 1
        self.temperatures[0] = T
        num_accepted = 0
        x_old, y_old = x_init, y_init
        energy_old = self.target(x_init, y_init)

        iter = 1
        while not converged:
            print("iter: {:4d}, temp: {:.4f}, energy = {:.6f}".format(iter,
                  T, energy_old))
            x_new, y_new = self.proposal(x_old, y_old)
            energy_new = self.target(x_new, y_new)

            if iter > 2*self.conv_window:
                vals = self.energies[iter-self.conv_window : iter-1]
                if (np.std(vals) < self.conv_thresh):
                    converged = True
                #end if
            #end if

            alpha = np.exp((energy_old - energy_new)/T)
            r = np.min([1, alpha])
            u = np.random.uniform(0, 1)
            if u < r:
                x_old, y_old = x_new, y_new
                num_accepted += 1
```

能量景观

检查收敛性

```python
energy_old = energy_new
#end if
self.samples[iter, :] = np.array([x_old, y_old])
self.energies[iter] = energy_old

T = self.temperature_schedule(T, iter)
self.temperatures[iter] = T

iter = iter + 1

    if (iter > self.max_iter): converged = True
#end while

niter = iter - 1
acceptance_rate = num_accepted / niter
print("acceptance rate: ", acceptance_rate)

x_opt, y_opt = x_old, y_old

return x_opt, y_opt, self.samples[:niter,:], self.energies[:niter], self.temperatures[:niter]

if __name__ == "__main__":

    SA = simulated_annealing()

    nx, ny = (1000, 1000)
    x = np.linspace(-2, 2, nx)
    y = np.linspace(-2, 2, ny)
    xv, yv = np.meshgrid(x, y)

    z = SA.target(xv, yv)
    plt.figure()
    plt.contourf(x, y, z)
    plt.title("energy landscape")
    plt.show()

    #find global minimum by exhaustive search
    min_search = np.min(z)
    argmin_search = np.argwhere(z == min_search)
    xmin, ymin = argmin_search[0][0], argmin_search[0][1]
    print("global minimum (exhaustive search): ", min_search)
    print("located at (x, y): ", x[xmin], y[ymin])

    #find global minimum by simulated annealing
    x_init, y_init = 0, 0
    x_opt, y_opt, samples, energies, temperatures = SA.run(x_init, y_init)
    print("global minimum (simulated annealing): ", energies[-1])
    print("located at (x, y): ", x_opt, y_opt)

    plt.figure()
    plt.plot(energies)
    plt.title("SA sampled energies")
    plt.show()
```

```
plt.figure()
plt.plot(temperatures)
plt.title("Temperature Schedule")
plt.show()
```

图 9.9 显示了目标能量景观（左）和 SA 采样能量（右）。

![](img/325742126d3ff007c6c385f4ffb5c3be_230_0.png)

**图 9.9** 能量景观（左）和 SA 采样能量（右）

在图 9.9 的示例中，我们能够使用模拟退火找到能量景观的全局最小值，该最小值与穷举搜索得到的全局最小值相匹配。在下一节中，我们将研究一种受进化生物学启发的遗传算法。

## 9.5 遗传算法

遗传算法 (GAs) 受进化生物学的启发并以其为模型。它们由一组（随机初始化的）个体基因组组成，这些基因组根据相对于目标的适应度进行评估。两个个体结合并交叉其基因组以产生后代。此交叉步骤随后进行突变，个体碱基可根据突变率发生变化。这些新个体被添加到种群中并由适应度函数评分，该函数决定个体是否在种群中存活。让我们查看图 9.10 中的伪代码。在此示例中，我们将进化一个随机字符串以匹配字符串目标。

GeneticAlgorithm 类包含以下函数：calculate_fitness、mutate、crossover 和 run。在 calculate_fitness 函数中，我们将适应度分数计算为 1/loss，其中 loss 定义为个体与目标 ASCII 字符串字符之间的距离。在 mutate 函数中，我们根据突变率随机更改个体的字符串字符。在 crossover 函数中，我们随机选择一个索引来交叉父代的基因组，然后在所选索引处执行父代基因组的交叉，产生两个子代。最后，在 run 函数中，我们初始化种群并计算种群适应度。之后
