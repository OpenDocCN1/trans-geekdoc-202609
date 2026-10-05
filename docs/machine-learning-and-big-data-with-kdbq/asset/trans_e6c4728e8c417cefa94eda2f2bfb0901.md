

# 410
# 机器学习

```qql
bucket[`path`]:path;
bucket[`continue`]:continue;
// 返回 bucket
:bucket;
};
```

让我们一起运行 LAR 算法。我们首先需要用所有变量初始化 bucket：

```qql
// 设置步长
step:0.0001;
// 因变量
y:tabData first cols tabData;
// 不含常数的自变量
S:(),tabData1_cols tabData;
// 创建带 beta 的空向量
beta:(count flip tabData)-2)@0.0;
// 给定迭代中的向量
betaDir:(count flip tabData)-2)@0.0;
// 已使用的自变量；
betaUsed:(count flip tabData)-2)@0b;
// 要求 y，返回 meanY
y-meanY=avg y;
// 定义残差变量
r:
// 包含整个路径的表
path:[] step:0;beta:enlist beta);
```

并将所有单独变量合并到字典中：

```qql
bucket: ((`beta`betaUsed`betadir`y`xS`r`path`continue`step)!(beta,betaUsed;
--betadir;y;xS;r;path;step));
```

由于变量中包含 `continue` 标志，我们可以使用迭代来运行算法，直到数据中的所有依赖关系被挖掘：

```qql
bucketExample:(quantQ.reg.oneStepLAR/)[[{continue}]];bucket;
```

可以查看 LAR 算法的结果。首先，因变量的均值在 `meanY` 变量中：

meanY
1.949716

其次，估计的 βs 为：

```qql
bucketExample[`beta`];
```

1.115732 -0.9479582 0.0677094

## 带有正则化的线性回归

这些参数在视觉上与标准 OLS 获得的参数数量级。我们可以通过计算到真实解的 $L_2$ 距离来确认这一点：

```qql
sqrt {x*x} each (1; -1.2;0.2;2)-raze (bucketExample[`beta`];meanY)
```

0.3113651

结果与 OLS 情况相比有所提高。为了方便起见，我们创建一个带有估计路径的表，该表将由 `arcLength` 索引。这代表到目前为止迭代过程中执行的 `bucket[`step`]` 的累积和。我们从路径表中提取内容：

```qql
pathLAR: update beta1:`beta[0]`,beta2:`beta[1]`,beta3:`beta[2]` from
  bucketExample[`path`]; pathLAR;
```

然后添加 `arcLength`：

```qql
pathLAR: update arcLength: sums abs[deltas[beta1]]+abs[deltas[beta2]]+abs[
  deltas[beta3]] from pathLAR;
```

当我们从表中选择一个子集时，得到了完整的估计路径：

```qql
select arcLength, beta1, beta2, beta3 from pathLAR
```

图 20.2 描述了针对 tabData 的 LAR 算法的整个路径。表 pathLAR。使用的颜色约定如下：浅灰色

![](img/97f7581128bd0bdf85683d4c69d94242_435_0.png)

图 20.2 tabData 的 LAR 算法整个路径的图。浅灰色对应 beta1，深灰色对应 beta2，黑色对应 beta3。

对应 beta1 系数，深灰色对应 beta2 系数，黑色对应 beta3 系数。

此时，我们鼓励读者使用大步长运行 `oneStepLAR` 函数，并观察估计性能。`oneStepLAR` 函数的一个可能的缺点是函数可以采取的步数没有限制。在极端情况下，该函数可能会无限运行。修改函数以添加一个安全功能来防止这种情况是明智的。

我们将算法封装进函数中。该函数将有两个参数：表数据，其中第一列是因变量，其余列捕获待估计线性关系中的特征。第二个参数是步长大小。除了归一化，在每次迭代中都有 `arcLength` 算法移动：

```qql
// quant.reg.LAR:[tab;step]
// 带有数据的表 (y,xS)
// LAR 算法的步长
// 因变量 - tab 的第一列
y:tab first cols tab;
// 自变量 - 剩余列
xS:(),tab1_cols tab;
// 创建带 beta 的空向量
beta:((count flip tab)-1)*0.0;
// 给定迭代中带 beta 的向量
betaDir:((count flip tab)-1)*0.0;
// 已使用的自变量
tailed:((count flip tab)-1)*0b;
// 去均值化 y。返回 meanY
y:y-mean=avg y;
// 定义残差变量
r:
// 包含整个路径的表
path:(step[0];beta:elist);
// 定义 bucket
bucket: ((beta`betaUsedbetaDir;y`xS`path`continue`step)!(beta,
-> betaUsed;betaDir;y;xS;r;path;step);
// 运行算法
bucketResult:(quant.reg.oneStepLAR/[x[continue]]);
// 结果是重排后的路径
pathTab:bucketResult[path];
// 创建 arcLength; 添加 meanY 并返回表
// 分段线性系数轮廓
// 等于从 step 到 step 变化的 L1 范数
// 选择 arcLength: sum each delta, beta0 从
// pathTab);eval(pathTab);0b;{"beta", x each 1+count[x]!(
x));
```

该函数在相同的数据上进行了测试。尽管函数在迭代过程之前执行了去均值化，但我们显式地保留了常数特征：

```qql
pathLAR2::quant.reg.LAR[tabData;0.0001];
```

查看 pathLAR2 的 10 行：

| arcLength | beta0 | beta1 | beta2 | beta3 |
|---|---|---|---|---|
| 2.1305 | 1.49716 | 1.11546 | -0.947515 | 0.067525 |
| 2.1306 | 1.49716 | 1.11546 | -0.947561 | 0.067554 |
| 2.1307 | 1.49716 | 1.11517 | -0.947607 | 0.067526 |
| 2.1308 | 1.49716 | 1.11548 | -0.947664 | 0.067591 |
| 2.1309 | 1.49716 | 1.11579 | -0.947710 | 0.067617 |
| 2.1310 | 1.49716 | 1.11569 | -0.947759 | 0.067632 |
| 2.1311 | 1.49716 | 1.11564 | -0.947803 | 0.067658 |
| 2.1312 | 1.49716 | 1.11571 | -0.947859 | 0.067703 |
| 2.1313 | 1.49716 | 1.11501 | -0.947906 | 0.067699 |
| 2.1314 | 1.49716 | 1.11532 | -0.947952 | 0.067709 |

我们得到了相同的结果。常数项系数为 0，这意味着对去均值时间序列的操作没有给常数特征分配任何值。这可以忽略无关特征。这表明尽管实际上不需要常数特征，算法仍然良好。

按照前面的章节，我们开发了一个测试样本外数据正则化有效性的函数。样本内数据执行与 LAR 函数相同的正则化，同时使用样本外数据的 RMSE 评估给定正则化的有效性。该函数的输出是一个带有正则化路径的表，路径的每个点都分配了 RMSE 值。

```qql
quant_reg_LAR(tab;step;inOutFlag)
// 带有数据的表 (y,x)
// LAR 算法的步长
// inOutFlag = 用于形成样本内的原子/数组，i=外
// 因变量 - tab 的第一列
y: tab first cols of tab
// 自变量 - 剩余列
x:(tab1_cols) cols;
whereMissing:=raze(where y!=0; raze (where x!=0) each x);
// 移除缺失值
y:y[(tile count y) except whereMissing];
S:[:where whereMissing] S([tile count x) except whereMissing])
whereMissing:= each x;
// inOutFlag 是原子，样本内是随机选择的比例
if(1<count(inOutFlag));
// 样本划分：外
xOUT:flip ceiling([inOutFlag+count y] flip x;
yOUT:ceiling([inOutFlag+count y] - y;
// 样本划分：内
xS:flip ceiling([inOutFlag+count y])flip xS;
y:ceiling([inOutFlag+count y])
// inOutFlag 是布尔数组，1 为内/0 为外
if([1<count[inOutFlag]]):
inOutFlag:inOutFlag([tile count inOutFlag]) except whereMissing);
```

```qql
// 带交叉验证的 LARS 回归
//quantq.LARCV([[tab;nCV]
// tab -- 带有 (y,xS) 的表
// step -- LAR 算法的步长
// nCV -- 交叉验证折数
// 因变量 - tab 的第一列
y:tab first cols tab;
// 自变量 - 剩余列
xS:(),tab1_cols tab;
whereMissing: raze (where y=0; raze (where x=0) each xS);
// 移除缺失值
y:((til count y) except whereMissing]]
xS:((whereMissing,xS) xS[(til count xS) except whereMissing]]
whereMissing:= each xS;
// 为每个折创建所有标记
foldFlag:(floor til[count y]%nCV)=:til nCV;
```

