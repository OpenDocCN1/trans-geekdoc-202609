

# 带正则化的线性回归

![](img/97f7581128bd0bdf85683d4c69d94242_439_0.png)

**图 20.3** 在 LAR 算法中经过样本外测试的 RMSE 关于弧长度 arcLength 的函数

```
// 对每个 fold 运行评估
outCV: (./)[{[f:nflag] show first nflag; eval (!;f[last nflag]);();)Ob;
-- enlist {fold}!enlist first nflag) ][.quantQ.reg.LARInOut([{ } y'),
-- flip ("$x","string) each til count[x]!xS;step;]) each flip
-- (til count foldFlag);foldFlag;
// 使用 step 和 folds 创建 frame（避免由于 arcLength 为浮点数导致的舍入误差）
frame: flip ('arcLength fold)'!flip exec arcLength*step from select
-- distinct "j$arcLength%step from (til count foldFlag
->);
// 别别地对每个 fold 调整 outCV
fullCV: (./)[{frame;outCVn] aj[arcLength]; arcLength select from
frame where fold;select RMSE from outCV where fold=
) [frame:outCV]; peach (til count foldFlag);
// 返回平均折的 RMSE 作为关于 arcLength 的函数
: select by RMSE from fullCV;
```

这里有几点需要说明。首先，对于每个验证折（validation fold），正则化路径的长度可能不同。为了聚合不同的折，我们使用最后一个值将正则化路径扩展到最后一个估计点之外。这种近似考虑了这样：arcLength 值越大，正则化越少，且正则化路径的最后一点等于普通的 OLS 模型。OLS 充当渐近模型的角色。在 q 中，这可以通过 `fills` 实现。此外，arcLength 的值是数值。这可能会导致来自不同 fold 的值之间产生数值差异。因此，在使用 `select ... by arcLength` 功能之前，我们显式地按照步精度对 arcLength 进行舍入。最后，计算各折按 arcLength 的平均 RMSE 值并填充到正则化路径中。

![](img/97f7581128bd0bdf85683d4c69d94242_440_0.png)

**图 20.4** 使用 12 折交叉验证的 LAR 算法中 RMSE 关于 arcLength 的函数

让我们用 12 折交叉验证来计算该示例：

```
exLARCV1 : quantQ_reg_LARCV[tabData;0.0001;12];
```

图 20.4 展示了完整的正则化路径。该路径捕捉了平均 RMSE 作为关于 arcLength 的函数，该函数是基于 12 折交叉验证方案计算的。图 20.5 缩放了正则化路径的末端。可以看到一个明显的最小值。交叉验证方案表明，最优线性回归是具有正则正则化的那一个，这与我们在岭回归得出的结论一致，即最优线性回归是正则化较小的那个。

最优 arcLength 的值可以恢复为：

| arcLength | RMSE |
| :--- | :--- |
| 2.1224 | 1.003023 |
| 2.1223 | 1.003023 |
| 2.1222 | 1.003023 |
| 2.1221 | 1.003023 |
| 2.122 | 1.003023 |
| 2.1219 | 1.003023 |
| 2.1218 | 1.003023 |
| 2.1217 | 1.003023 |
| 2.1216 | 1.003023 |
| 2.1215 | 1.003023 |

![](img/97f7581128bd0bdf85683d4c69d94242_441_0.png)

**图 20.5** 使用 12 折交叉验证的算法中 RMSE 关于 arcLength 的函数，重点关注最小值附近

# 第 21 章 最近邻

最近邻算法在数据探索和模式识别中非常流行。在本章中，我们将涵盖邻域技术的基础，并介绍三种特定的算法。这些方法从定义上来说是无模型的（model-free）。我们只需要对数据施加轻微——不——任何假设。结果完全源于数据集本身。这不可避免的后果是模型的黑箱性质。如果不查看原始数据，我们几乎无法为独立变量和因变量之间的关系引入叙述。

基于最近邻的算法在分类中非常成功。它们可以用于回归，但最近邻算法的效果在分类中那么好。特别是，高维问题对最近邻具有挑战性。在本节中，我们介绍了基于邻域原理的特定算法，并在 q 中实现了它们：

- 基于邻域的 k-最近邻 分类器
- 邻域聚类

## 21.1 最近邻分类器

基于最近邻的方法是无参数的。对于分类，我们使用基于邻域的多数投票；对于回归，我们使用基于邻域的期望值。

