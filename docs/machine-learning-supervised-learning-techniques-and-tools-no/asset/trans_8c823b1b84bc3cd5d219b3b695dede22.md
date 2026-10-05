

![Diagrama 自动生成的描述](d2d_images/image606.png)

对变量 ![image](d2d_images/image573.png) 对工资的边际效应将按如下方式计算：

![Texto 自动生成的描述](d2d_images/image115.png)

接下来我们考虑文件 `married.wf1`，其中包含1975年753名已婚女性的数据，其中428人在当年某个时间参与了劳动力市场（`inlf=1`），325人未参与（`inlf=0`）。劳动力市场参与（`inlf`）被发现取决于其他收入来源（`nwifeinc`）、受教育年限（`educ`）、工作经验年限（`exper` 和 `exper²`）、年龄、6岁以下儿童数量（`kidslt6`）和6至18岁儿童数量（`kidsg6`）。

基于上述信息，使用截断Tobit模型，我们将利用 Heckman 两阶段法估计工资方程，使女性的工资对数取决于其教育水平、工作经验以及后者的平方变量。

与前一种情况一样，这是一个具有附带截断的Tobit模型，因为劳动力市场参与取决于劳动力供给。

### 第一阶段

在第一阶段，我们估计 `Inlf` 对常数项和所有解释变量的 Probit 模型。模型为：

![image](d2d_images/image491.png)

为此，选择 `Quick→ Estimate Equation`，在 Specification 选项卡的 Equation Specification 字段中输入拟合模型的方程，在 Method 字段中选择 `BINARY-Binary chice (logit, probit, extreme value)`，在 Binary estimation method 字段中选择 `Probit` 以使用 Probit 模型进行拟合（图 4-44），然后单击 OK。图 4-45 中得到的结果显示估计参数具有良好的个体显著性（常数项和 `kidsge6` 除外）。联合显著性非常高，因为似然比统计量的 p 值非常小。McFadden 的伪 R² 不太接近 1（0.22）。信息准则（Akaike、Schwarz 和 Hannan-Quinn）的值是合适的，因为它们较低且非常接近。

![image](d2d_images/image701.png)![image](d2d_images/image694.png)

图 4-44    图 4-45

接下来我们通过新拟合的 Probit 模型的广义残差计算 Mills 比的倒数。为此，在 Probit 窗口中选择 `Procs → Make residual series` 并选择 `Generalized`（图 4-46）。得到新变量 `resid01 =`![image](d2d_images/image619.png) 等同于 Mills 比（图 4-47）。

![image](d2d_images/image512.png)![image](d2d_images/image347.png)

图 4-46    图 4-47

### 第二阶段

在第二阶段，我们通过 OLS 估计工资方程，将广义 Probit 残差作为额外的回归变量。待估计的模型为：

![image](d2d_images/image166.png)

为此，选择 `Quick→ Estimate Equation`，在 Specification 选项卡的 Equation Specification 字段中输入拟合模型的方程，在 Method 字段中选择 `LS-Two stage Least Squares (NLS and ARMA)` 以进行最小二乘拟合（图 4-48），然后单击 OK。结果显示在图 4-49 中。

![image](d2d_images/image668.png)![image](d2d_images/image015.png)

图 4-48    图 4-49

我们观察到估计系数的显著性非常好，无论是单独还是联合，信息准则的值良好，且 Durbin Watson 统计量非常接近 2，表明不会存在序列自相关问题。

## Exercise 4-1

在房地产市场的一项研究中，我们拥有家庭收入水平的信息（`INCOME`）、家庭子女数量（`CHILDREN`）、一个二元变量（`SUB`），如果房屋为补贴则取值为 1，否则为 0，以及离散变量 `HOUSE`，指可供买家购买的房屋的平方米数，其值取决于面积如下：

![Interfaz de usuario gráfica, Texto 自动生成的描述](d2d_images/image184.png)

目的是分析家庭根据其自身特征（收入和子女）以及房屋特征（是否补贴）购买何种类型的住房，使用多响应模型 ![image](d2d_images/image306.png] 并假设分布函数 `F` 可以是正态（0,1）或逻辑分布，哪种方法更好？

由于因变量的值可以根据其面积从小到大排序，可以指定类型为 ![image](d2d_images/image605.png] 的有序多响应模型，其中：

![Imagen que contiene Esquemático 自动生成的描述](d2d_images/image099.png)

通过将分布函数 `F` 视为正态（多维 Probit 模型）或逻辑（多维 Logit 模型）来呈现不同的模型。

要估计有序多项 Probit 模型，选择 `Quick→ Estimate Equation`，在 Specification 选项卡的 Equation Specification 字段中输入拟合模型的方程，在 Method 字段中选择 `ORDERED-Ordered choice`，在 Error ditribution 字段中选择 `Normal` 以拟合多项 Probit 模型（图 4-50），然后单击 OK。图 4-51 中得到的结果显示估计参数具有良好的个体显著性（也许 `SUB` 除外，其显著性约为 85%）。联合显著性非常高，因为似然比统计量的 p 值非常小。伪 R² 接近 60%。信息准则（Akaike、Schwarz 和 Hannan-Quinn）的值是合适的。

![image](d2d_images/image666.png)![image](d2d_images/image138.png)

图 4-50      图 4-51

要估计有序多项 Logit 模型，选择 `Quick→ Estimate Equation`，在 Specification 选项卡的 Equation Specification 字段中输入拟合模型的方程，在 Method 字段中选择 `ORDERED-Ordered choice`，在 Error distribution 字段中选择 `Logistic` 以拟合多项 Logit 模型（图 4-52），然后单击 OK。图 4-53 中得到的结果显示估计参数具有良好的个体显著性（也许 `SUB` 除外，其显著性约为 85%）。联合显著性非常高，因为似然比统计量的 p 值非常小。伪 R² 接近 60%。信息准则（Akaike、Schwarz 和 Hannan-Quinn）的值是合适的。可以观察到拟合优度统计量的结果与 Probit 模型的情况非常相似。

![image](d2d_images/image312.png)![image](d2d_images/image165.png)

图 4-52      图 4-53

最有效的估计方法将是 Akaike、Schwarz 和 Hannan-Quinn 信息准则值最低且似然函数值最高的方法。汇总如下：

![image](d2d_images/image107.png)

信息准则值最低且似然函数值最高的方法是 Probit 模型。因此，最佳拟合由有序多项 Probit 模型提供。

## Exercise 4-2

在西班牙家庭电视拥有情况的一项研究中，对 940 个家庭进行了调查，询问家庭中的电视数量（`TV`）、年收入（以百万货币单位计，`FI`）以及家庭户主的教育水平（`NI`）。变量 `TV` 可以取 1、2 或 3，取决于家庭拥有 1 台、2 台和 3 台或更多电视机。家庭户主的教育水平已通过四个等级编码（Básica、Bachillerato superior、Universitaria media 和 Universitaria superior），其整数值分别为 1 至 4。利用包含在文件 `7-8.wf1` 中的指定数据，我们被要求拟合一个 logit 模型，用来解释家庭拥有给定数量电视机的概率如何取决于上述定义的其余变量。

