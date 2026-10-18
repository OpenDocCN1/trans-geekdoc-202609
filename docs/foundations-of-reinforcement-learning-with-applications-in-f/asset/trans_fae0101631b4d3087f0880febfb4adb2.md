

为了近似动态规划（Approximate Dynamic Programming）和强化学习（Reinforcement Learning）的目的，函数近似（function approximation）的预测 `𝔼[y|x]` 对任何状态的值函数（Value Function）提供了估计（`x` 扮演 `State` 的角色，`y` 扮演该状态之后的 `Return` 的角色）。在针对（随机）策略（policies）的函数近似中，`x` 扮演 `State` 的角色，`y` 扮演该策略的 `Action` 的角色，而 `f(x; w)` 提供了状态 `x` 的动作概率分布（对应于该策略）。还值得指出的是，函数近似的更广泛理论涵盖了多维 `y` 的情况（其中 `y` 是实值向量，而非标量）——这使我们既能解决分类问题，也能解决回归问题。然而，为了便于阐述并充分覆盖本书中函数近似的应用，我们仅涵盖标量 `y` 的情况。

现在让我们编写一些捕捉此框架的代码。我们编写一个抽象基类 `FunctionApprox`，由 `X` 类型参数化（以允许任意数据类型 `𝒳`），代表 `f(x; w)`，并包含以下 3 个关键方法，每个方法都将处理通用可迭代类型（Iterable）的输入（`Iterable` 是我们可以遍历的任何数据类型，例如序列类型或迭代器类型）：

1. `@abstractmethod solve`：接收 `(x, y)` 对的可迭代对象作为输入，并求解最小化输入数据的 `(x, y) 对` 的经验概率分布与模型概率分布 `f(x; w)` 之间交叉熵的最优内部参数 `w*`。`solve` 的某些实现是迭代数值方法，需要额外输入 `error_tolerance` 来指定最佳拟合参数 `w*` 所需的精度。当 `solve` 的实现是不需要误差容差的解析解时，我们将输入 `error_tolerance` 指定为 `None`。`solve` 的输出是 `FunctionApprox f(x; w*)`（即对应于求解得到的参数 `w*`）。

2. `update`：接收 `(x, y)` 对的可迭代对象作为输入，并更新定义 `f(x; w)` 的参数 `w`。`update` 的目的是在当前迭代中，根据输入的 `(x, y)` 对数据，对参数 `w` 进行增量（迭代）改进。`update` 的输出是对应于更新后参数的 `FunctionApprox`。请注意，我们应当能够基于一系列适当的增量更新（直到指定的 `error_tolerance`）来求解。

3. `@abstractmethod evaluate`：接收 `x` 值的可迭代对象作为输入，并为每个输入的 `x` 值计算 `𝔼[M][y|x] = 𝔼[f(x; w)][y]`，并以 `numpy.ndarray` 的形式输出这些期望值。

正如我们所解释的，对参数 `w` 的增量更新涉及计算梯度，然后使用梯度来调整参数 `w`。因此，方法 `update` 由以下两个抽象方法支持。

* `@abstractmethod objective_gradient`：计算 `FunctionApprox` 的目标函数（称其为 `Obj(x, y)`）相对于 `FunctionApprox` 内部表示中的参数 `w` 的梯度。梯度以 `Gradient` 类型的形式输出。`objective_gradient` 方法的第二个参数 `obj_deriv_out_fun` 表示 `Obj` 相对于适当模型计算值（称其为 `Out(x)`）的偏导数，即 `∂Obj(x,y)/∂Out(x)`，在一系列 `x` 值和一系列 `y` 值（将从 `objective_gradient` 方法的第一个参数 `xy_vals_seq` 中获得）处求值。

* `@abstractmethod update_with_gradient`：接收一个 `Gradient` 作为输入，并使用梯度值更新内部参数（例如，对参数进行梯度下降更新），并返回更新后的 `FunctionApprox`。

`update` 方法的编写方式如下，对每个训练数据点 `(x[i], y[i])`，定义 `∂Obj(x_i,y_i)/∂Out(x_i)` 如下：

```
∂Obj(x_i,y_i)/∂Out(x_i) = E_M[y|x_i] - y_i
```

事实证明，对于我们想要实现的每个具体函数近似，如果目标 `Obj(x[i], y[i])` 是交叉熵损失函数，我们可以识别一个模型计算值 `Out(x[i])`（模型的输出或模型的中间计算），使得 `∂Obj(x_i,y_i)/∂Out(x_i)` 等于每个训练数据点 `(x[i], y[i])` 的预测误差 `𝔼[M][y|x[i]] − y[i]`，并且我们可以提出一个数值算法来计算 `∇[w]Out(x[i])`，这样通过链式法则，我们就有所需的梯度：

```
∇_w Obj(x_i,y_i) = ∂Obj(x_i,y_i)/∂Out(x_i) · ∇_w Out(x_i) = (𝔼_M[y|x_i] - y_i) · ∇_w Out(x_i)
```

`update` 方法实现了这种链式法则计算，将 `obj_deriv_out_fun` 设置为预测误差 `𝔼[M][y|x[i]] − y[i]`，并将 `∇[w]Out(x[i])` 的计算委托给抽象方法 `objective_gradient` 的具体实现。

请注意，`Gradient` 类包含一个类型为 `FunctionApprox` 的单个属性，以便 `Gradient` 对象可以以 `FunctionApprox` 属性的内部参数形式表示梯度值（因为每个梯度值只是相对于内部参数的偏导数）。

我们使用 `TypeVarF` 来指代将实现 `FunctionApprox` 抽象接口的具体类。

![](images/comp06_1.jpg)

当实现 `FunctionApprox` 的具体类使用 `update` 方法来编写 `solve` 方法时，它们需要检查新更新的 `FunctionApprox` 是否与之前的 `FunctionApprox` “足够接近”。因此，它们都需要实现自己的版本：“两个 `FunctionApprox` 实例是否在某个 `error_tolerance` 之内？”。因此，我们需要在以下位置添加抽象方法：

![](images/comp06_2.jpg)

任何实现此抽象类 `FunctionApprox` 的具体类都需要根据该具体类对 `f` 所做的特定假设，实现 `FunctionApprox` 的这五个抽象方法。

接下来，我们编写一些对继承自 `FunctionApprox` 的类有用的方法。首先，我们编写一个名为 `iterate_updates` 的方法，它接收一个流（`Iterator`）的 `(x, y)` 对的可迭代对象作为输入，并对参数 `w` 执行一系列增量更新（每个使用 `update` 方法），每个更新都针对输入流 `xy_seq: Iterator[Iterable[Tuple[X, float]]]` 中的每个 `(x, y)` 对的可迭代对象进行。`iterate_updates` 返回一个 `FunctionApprox` 的 `Iterator`，表示由于重复调用 `update` 而依次更新的 `FunctionApprox` 实例。请注意使用 `rl.iterate.accumulate` 函数（`itertools.accumulate` 的包装版本），它根据提供的函数在 `Iterable` 上计算累积结果（包括中间结果）。在下面的代码中，`Iterable` 是输入流 `xy_seq_stream`，控制累积的函数是 `FunctionApprox` 的 `update` 方法。

![](images/comp06_3.jpg)

接下来，我们编写一个名为 `rmse` 的方法，用于计算 `x` 的预测（使用 `evaluate`）相对于相关的（监督）` y` 的均方根误差（Root-Mean-Squared-Error），输入为 `(x, y)` 对的可迭代对象。此方法在测试 `FunctionApprox` 估计的优劣时将很有用。

![](images/comp06_4.jpg)

