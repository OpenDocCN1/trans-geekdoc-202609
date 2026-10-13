
由于 `![image](images/ch08_si160.gif)`、`![image](images/ch08_si161.gif)` 和 `![image](images/ch08_si162.gif)` 均为正交矩阵，因此该不等式成立。因此，当 `![image](images/ch08_si163.gif)` 时迹最大化，从而得到

```
![image](images/ch08_si432.gif)
```

为了优化 `![image](images/ch08_si164.gif)`，令 `![image](images/ch08_si165.gif)`，其中 `![image](images/ch08_si166.gif)` 是 (8.7) 的代价函数，最佳缩放因子可通过以下方式获得

```
![image](images/ch08_si433.gif)
```

### 8.4.2 量化

`![image](images/ch08_si167.gif)` 是一个已知的正交变换矩阵，`![image](images/ch08_si168.gif)` 是一个给定的实值优化投影矩阵，寻找其最近的布尔矩阵的问题可表述为

```
![image](images/ch08_si434.gif)
```

显然，(8.12) 的解为

```
![image](images/ch08_si435.gif)
```

这可以视为布尔量化。量化误差可定义为

```
![image](images/ch08_si436.gif)
```

在理想情况下，误差为零，这意味着对优化的实值投影矩阵 `![image](images/ch08_si170.gif)` 进行正交变换 `![image](images/ch08_si169.gif)` 可找到一个精确的布尔矩阵 `![image](images/ch08_si171.gif)`。因此，由 `![image](images/ch08_si173.gif)` 引起的失真 `![image](images/ch08_si172.gif)` 将与 `![image](images/ch08_si174.gif)` 相同。利用 `![image](images/ch08_si175.gif)`，可推断出 `![image](images/ch08_si176.gif)`。为了减小量化误差，增加量化电平是一个内在的想法。考虑一个修正后的问题表述

```
![image](images/ch08_si437.gif)
```

其中矩阵 `![image](images/ch08_si177.gif)` 的每个元素均归一化在区间 `![image](images/ch08_si178.gif)` 内。保持矩阵为布尔矩阵非常重要，以便其能高效映射到 ReRAM 交叉阵列结构；因此，要求矩阵 `![image](images/ch08_si179.gif)` 可分解为两个布尔矩阵 `![image](images/ch08_si180.gif)`，其中 `![image](images/ch08_si181.gif)` 和 `![image](images/ch08_si182.gif)`。采用布尔量化，仅需一个投影 ReRAM 交叉阵列。三电平量化情况需要两个 ReRAM 交叉阵列，这是在误差与硬件复杂度之间权衡的结果。

### 8.4.3 整体优化算法

启发式优化过程总结在算法 8.1 中。给定 `![image](images/ch08_si183.gif)` 的某个初始猜测，算法 8.1 的内层循环尝试通过迭代改进 `![image](images/ch08_si184.gif)` 来寻找局部近似最优解。在每次迭代中，(8.6) 和 (8.12) 分别通过奇异向量分解和量化求解，如 (8.10) 和 (8.15) 所述。当 `![image](images/ch08_si185.gif)` 停止改进并收敛时，迭代终止。

**算法 8.1：** IH 布尔采样矩阵优化算法

**输入**：实值嵌入矩阵 `![image](images/ch08_si186.gif)`、搜索宽度和量化电平

**输出**：优化的布尔嵌入矩阵 `![image](images/ch08_si187.gif)` 初始化 `![image](images/ch08_si188.gif)` `![image](images/ch08_si189.gif)` 随机 `![image](images/ch08_si190.gif)` 伯努利矩阵

1: **当** 未达到搜索宽度限制 **时**

2: seed ← 随机 m × m 矩阵

3: U, S, V ← seed 的 SVD

4: T ← U

5: **当** 未收敛 **时**

6: `![image](images/ch08_si195.gif)` ← `![image](images/ch08_si197.gif)` 的量化

7: U, S, V ← `![image](images/ch08_si198.gif)` `![image](images/ch08_si199.gif)` 的 SVD

8: T ← UV

9: `![image](images/ch08_si201.gif)`

10: **如果** `![image](images/ch08_si202.gif)` **则**

11: `![image](images/ch08_si203.gif)` `![image](images/ch08_si204.gif)` `![image](images/ch08_si205.gif)`

12: **结束如果**

13: **结束当**

14: **结束当**

由于整数约束和正交约束均为非凸，局部最优在大多数情况下并非全局最优。换句话说，解强烈依赖于通向局部近似最优的初始猜测。因此，算法 8.1 的外层循环通过生成散布在正交矩阵空间内的大量初始猜测来增加搜索宽度。对于每个初始猜测，它将逐渐收敛到一个局部最优；因此，搜索宽度的增加将比较大量局部最优解并逼近全局最优。

### 8.5 行生成算法

(8.5) 中表述的问题是一个混合整数非线性规划 (MINLP) 问题，因为它同时具有非线性正交约束 `![image](images/ch08_si206.gif)` 和整数约束 `![image](images/ch08_si207.gif)`。虽然此类 MINLP 问题可通过现有算法（如遗传算法 [295]）求解，但其效率低下，且仅能处理小规模问题。对于压缩感知中的嵌入矩阵，变换矩阵 `![image](images/ch08_si208.gif)` 可能有数十行，而矩阵 `![image](images/ch08_si209.gif)` 可能包含数千个布尔变量，因此当前求解器可能无法处理如此规模。在本节中，我们提出了一种行生成算法，也能高效解决该问题。

#### 8.5.1 范数等式约束的消除

(8.5) 中 `![image](images/ch08_si210.gif)` 的正交性意味着两个特定约束：`![image](images/ch08_si211.gif)` 的行正交性，即

```
![image](images/ch08_si438.gif)
```

以及范数相等性，即

```
![image](images/ch08_si439.gif)
```

其中 `![image](images/ch08_si212.gif)` 是 `![image](images/ch08_si214.gif)` 的第 `![image](images/ch08_si213.gif)` 行。两者均意味着大量二次等式约束（非凸），因此难以同时处理。`![image](images/ch08_si215.gif)` 的行的非凸二次范数等式约束表明在满足正交性后对行进行归一化。下文将展示如何在不影响 (8.5) 中问题求解精度的情况下消除范数等式约束。

假设我们仅对 `![image](images/ch08_si216.gif)` 施加正交约束，而非更严格的标准正交约束，则原问题可松弛为

```
![image](images/ch08_si440.gif)
```

其中 `![image](images/ch08_si217.gif)` 是一个对角矩阵，`![image](images/ch08_si218.gif)` 是 `![image](images/ch08_si220.gif)` 第 `![image](images/ch08_si219.gif)` 行的范数。也就是说，在感知阶段引入了额外的行缩放操作

```
![image](images/ch08_si441.gif)
```

其中 `![image](images/ch08_si221.gif)` 是可在硬件中高效实现的优化布尔嵌入矩阵，`![image](images/ch08_si222.gif)` 是原始信号的标准正交稀疏基，`![image](images/ch08_si223.gif)` 是稀疏系数。

事实上，信号采集期间的行缩放操作是不必要的，如果执行隐式感知，可将其转移到恢复阶段，

```
![image](images/ch08_si442.gif)
```

相应的信号重构为

```
![image](images/ch08_si443.gif)
```

其中 `![image](images/ch08_si224.gif)` 是采样信号数据 `![image](images/ch08_si225.gif)` 上噪声的容限。因此，在压缩感知信号采集前端硬件复杂度保持不变且恢复质量不受影响的情况下，消除了范数等式约束。

#### 8.5.2 正交约束的凸松弛
