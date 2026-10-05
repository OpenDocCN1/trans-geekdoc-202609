

我们可以通过将 `Probit` 模型的估计系数乘以 `0.391` 来获得连续变量在 X 的均值处的估计边际效应。

因此，多受一年教育会使参与劳动力市场的概率增加 `0.131x0.391 = 0.05`。年龄增加一年会使参与概率下降 `0.02`（`-0.053x0.391=-0.021`）。随着经验增加一年，参与概率的变化为 `[0.124-(2x0.0019xexper)]x0.391`。其他收入增加一个单位会导致参与概率下降 `0.005`（`-0.012x0.391 = -0.05`）。

我们也可以计算离散变量变化的估计效应。例如，对于 `kidslt6`，从有 0 个到有 1 个（6 岁以下）孩子对工作概率的影响是减少 `0.336`，因为 `Ф = 正态分布函数 (0.1)`：

![image](d2d_images/image116.png)

而从 1 个到 2 个（6 岁以下）孩子对女性工作概率的影响将减少 `0.231`，因为：

![image](d2d_images/image687.png)

现在我们将使用 `Logit` 模型进行估计。为此，选择 `Quick→ Estimate Equation`，在 `Specification` 选项卡的 `Equation Specification` 字段中输入拟合模型的方程，在 `Method` 字段中选择 `BINARY-Binary choice (logit, probit, extreme value)`，在 `Binary estimation method` 字段中选择 `Logit` 以拟合 `Probit` 模型（图 4-18）并点击 `OK`。

图 4-19 中的结果显示估计参数具有良好的个体显著性（除常数和 `kidsge6` 外），与 `Probit` 模型的情况相同。联合显著性非常高，因为似然比统计量的 p 值非常小。McFadden's Pseudo R² 不太接近 1（`0.219`）。信息准则（`Akaike`、`Schwarz` 和 `Hannan-Quinn`）的值是合适的。

![image](d2d_images/image435.png)![image](d2d_images/image314.png)

图 4-18      图 4-19

对于对数函数：

![image](d2d_images/image623.png)

（`λ` 是对数密度函数，`Λ` 是对数分布函数）

并且通过将估计系数乘以 `0.227` 计算变量的平均边际效应，得出的结果与 `Probit` 模型相同。

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 4.2 EViews 中的计数模型：泊松、负二项和指数模型

![image](d2d_images/chapter_title_below.png)

作为示例，我们考虑文件 `arrests.wf1`，其中包含变量 `narr86` 的信息，该变量表示某人在 1986 年被逮捕的次数，我们希望用变量 `pcnv`（此前逮捕中被定罪的比例）、`avgsen`（刑期平均长度，月）、`totttime`（监狱时间，月）、`ptime86`（1986 年监狱时间，月）、`qemp86`（1986 年就业季度，以百美元计）、`black`（fic86） （1986 年合法收入，以百美元计）、`black`（fic86） （fic86） （fic86） （fic86）、`ptime86`（1986 年监狱时间，月）、`qemp86`（就业季度）、`inc86`（1986 年合法收入，以百美元计）、`black`（黑人被捕者虚拟变量，取值为 1）、`hispan`（西班牙裔被捕者虚拟变量，取值为 1）和 `born60`（被捕者出生于 1960 年的虚拟变量，取值为 1）来解释。由于被解释变量在大量情况下取值为 0，且仅在 8 种情况下取值大于 5，因此可以使用计数数据模型。我们将使用 Poissson、指数和负二项计数数据模型研究解释变量对被解释变量的影响。

我们首先使用泊松计数模型估计模型。为此，选择 `Quick→ Estimate Equation`，在 `Specification` 选项卡的 `Equation Specification` 字段中输入拟合模型的方程，在 `Method` 字段中选择 `COUNT-Integer count data`，在 `Count estimation method` 字段中标记 `Poisson (ML and QML)` 以通过泊松计数数据模型拟合（图 4-20）并点击 `OK`。图 4-21 中的结果显示估计参数具有良好的个体和联合显著性（除 `avgsen`、`totttime`、`ptime86` 和 `born60` 外）。伪 R² 非常小，信息准则的值相当可接受。与之前情况类似的拟合参数也被观察到。使用 `View → Representations`（图 4-22）可获得拟合模型方程（图 4-23）。

![image](d2d_images/image164.png)![image](d2d_images/image025.png)

图 4-20      图 4-21

![image](d2d_images/image056.png)![image](d2d_images/image004.png)

图 4-22    图 4-23

由于调整现在为 ![image](d2d_images/image113.png)，在解释结果时我们看到，如果个人在 1986 年多就业一个季度（其他因素固定），当年预期逮捕次数将减少 3.8%（不显著）。在其他条件相同的情况下，黑人男性的预期逮捕次数比白人高 66%，西班牙裔比白人高 50%。其他参数的解释类似。

如果在 `Equation Estimation` 屏幕中点击 `Options` 选项卡并选择 `Robust Covariances-GLM`（图 4-24），点击 `OK` 后，我们将获得在 `V(Y|X)=σ² E(Y|X)` 下计算 GLM 标准误差的泊松计数模型估计，如图 4-25 所示。可以看出，结果与之前情况差异不大，参数估计值非常相似。注意方差估计为：

––––––––

![image](d2d_images/scene_break.png)

![image](d2d_images/image555.png)

由于 `σ² >1`，我们相对于泊松方差存在过度离散的情况。使用 `View → Representations`（图 4-26）我们获得拟合模型（图 4-27）。

![image](d2d_images/image134.png)![image](d2d_images/image337.png)

图 4-24      图 4-25

![image](d2d_images/image323.png)![image](d2d_images/image439.png)

图 4-26      图 4-27

我们现在使用负二项计数模型（拟似然估计）估计模型。为此，选择 `Quick→ Estimate Equation`，在 `Specification` 选项卡的 `Equation Specification` 字段中输入拟合模型的方程，在 `Method` 字段中选择 `COUNT-Integer count data`，在 `Count estimation method` 字段中选择 `Negative Binomial (QML)` 以拟合二次最大似然的负二项计数数据模型（图 4-28）并点击 `OK`。

图 4-29 中的结果显示估计参数具有良好的个体和联合显著性（除 `avgsen`、`totttime` 和 `born60` 外）。伪 R² 非常小，信息准则的值相当可接受。此外，还观察到与之前方法非常相似的结果。通过 `View → Representations`（图 4-30）获得拟合模型的方程（图 4-31）。

![image](d2d_images/image712.png)![image](d2d_images/image358.png)

图 4-28      图 4-29

![image](d2d_images/image269.png)![image](d2d_images/image372.png)

图 4-30      图 4-31

最后，我们现在使用指数计数模型（拟最大似然）估计模型。为此，选择 `Quick→ Estimate Equation`，在 `Specification` 选项卡的 `Equation Specification` 字段中输入拟合模型的方程，在 `Method` 字段中选择 `COUNT-Integer count data`，在 `Count estimation method` 字段中选择 `Exponential (QML)` 以拟合二次最大似然的指数计数数据模型（图 4-32）并点击 `OK`。图 4-33 中的结果被获得。`View → Representations`（图 4-34）给出拟合模型的方程（图 4-35）。

![image](d2d_images/image055.png)![image](d2d_images/image028.png)

图 4-32      图 4-33

