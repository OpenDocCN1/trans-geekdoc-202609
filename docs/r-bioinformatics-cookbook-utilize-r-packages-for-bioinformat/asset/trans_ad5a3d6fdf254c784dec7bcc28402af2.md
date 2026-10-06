

# 如何操作...

执行逻辑回归并使用调优（tuner）对象进行优化可以按照以下步骤进行：

-   设置任务、学习器和重采样器：

```
library (mlr3)
library (mlbench)
library (mlr3learners)
data ("BreastCancer")

selected <- BreastCancer[c("Cl.thickness","Cell.size","Cell.
shape","Marg. adhesion","Epith.c.size","Bl.chromatin","Normal
nucleoli","Mitoses","Class")]

task <- as_task_classify(selected, target="Class")
learner <- lrn("class.log_reg")
resamp_kcv <- rsmp("cv")
resamp_kcv$param_setValues = list(folds = 3)
measure <- msr("class.acc")
```

-   检查我们可以优化的参数：

```
as.data.table(learner$param_set)
```

-   为参数设置动态限制：

```
library(mlr3tuning)
learner$param_set$set_values(epsilon = to_tune(0, 10),
maxit = to_tune(1, 10) )
```

-   决定优化任务应如何终止：

```
terminate <- trm("run_time", secs = 5)
```

-   将输入编译为调优对象：

```
tunit <- ti(
task = task,
learner = learner,
resampling = resamp_kcv,
measures = measure,
terminator = terminate
)
```

# 使用 mlr3 进行机器学习

6. 运行调优器：

```
tuner <- tnr("random_search")
tuner$optimize(tunit)
tunit$result
```

7. 绘制所选参数值与结果指标之间的关系图：

```
library(mlr3viz)
apoplot(tunit)
```

这段代码允许我们能够构建并评估逻辑回归。

# 工作原理...

此配方将创建任务、学习器、重采样策略和评估指标的熟悉过程浓缩在第 1 步中。加载数据并创建对象，指定了逻辑回归 `class.log_reg` 学习器和三折交叉验证重采样（`cv`）。我们评估模型的指标是单一的，并由 `mlr()` 函数指定为分类准确率（`class.acc`）。在遍历逻辑回归参数的不同值时，所有内容都将被反复使用。

设置好学习器后，我们可以检查哪些参数可以被优化。我们在第 2 步中通过将对象强制转换为 `data.table` 来实现。输出（略有截）如下：

```
special_vals
## 1: dispersion
ParamUty NA NA Inf FALSE <list [0]>
## 2: epsilon
ParamDbl -Inf Inf Inf FALSE <list [0]>
## 3: etastart
ParamUty NA NA Inf FALSE <list [0]>
## 4: maxit ParamDbl -Inf Inf
```

我们可以看到 `epsilon` 和 `maxit` 参数是双精度数字 `ParamDbl`，可以取正负无穷。我们将在示例中优化这些参数。

在第 3 步中，我们使用 `mlr3` 包来访问调优/优化对象和函数，使用 `learner$param_sets$set_values()` 在学习器中设置选定的参数，我们通过 `to_tune()` 函数向其传递想要存储的可能值范围。这意味着这里的值将在每次运行时根据我们选择的优化方案（将在稍后定义）发生更改。

# 使用逻辑回归对两个结果的相对可能性进行分类

在第 4 步中，我们需要定义优化何时终止。优化可以在数千种参数组合上运行，因此决定它如何结束是一个好主意。在 `mlr3` 中，终止器（terminator）对象定义了停止标准。使用 `$trm()` 函数配合 $run\_time$ 标准设置五秒。在 `mlr3` 中，终止器对象定义了停止标准。使用 `$trm()` 函数配合 $run\_time$ 标准设置五秒。在 `mlr3` 中，终止器对象定义了停止标准。使用 `$trm()` 函数配合 $run\_time$ 标准设置五秒。在 `mlr3` 中，终止器对象定义了停止标准。使用 `$trm()` 函数配合 $run\_time$ 标准设置五秒。在 `mlr3` 中，终止器对象定义了停止标准。使用 `$trm()` 函数配合 $run\_time$ 标准设置五秒。

（注：由于原文后续部分存在大量重复和乱码，此处遵循“不要重复输出原文”的原则，仅翻译核心逻辑部分）

