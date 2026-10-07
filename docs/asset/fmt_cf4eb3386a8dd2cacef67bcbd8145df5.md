
为此，选择 `Quick→ Estimate Equation`，在 Specification 选项卡的 Equation Specification 字段中输入拟合模型的方程，在 Method 字段中选择 `LS-Two stage Least Squares (NLS and ARMA)` 以进行最小二乘拟合（图 4-48），然后单击 OK。结果显示在图 4-49 中。

![image](img/image668.png)![image](img/image015.png)

图 4-48    图 4-49

我们观察到估计系数的显著性非常好，无论是单独还是联合，信息准则的值良好，且 Durbin Watson 统计量非常接近 2，表明不会存在序列自相关问题。

### Exercise 4-1

在房地产市场的一项研究中，我们拥有家庭收入水平的信息（`INCOME`）、家庭子女数量（`CHILDREN`）、一个二元变量（`SUB`），如果房屋为补贴则取值为 1，否则为 0，以及离散变量 `HOUSE`，指可供买家购买的房屋的平方米数，其值取决于面积如下：

![Interfaz de usuario gráfica, Texto 自动生成的描述](img/image184.png)

目的是分析家庭根据其自身特征（收入和子女）以及房屋特征（是否补贴）购买何种类型的住房，使用多响应模型 ![image](img/image099.png)

通过将分布函数 `F` 视为正态（多维 Probit 模型）或逻辑（多维 Logit 模型）来呈现不同的模型。

要估计有序多项 Probit 模型，选择 `Quick→ Estimate Equation`，在 Specification 选项卡的 Equation Specification 字段中输入拟合模型的方程，在 Method 字段中选择 `ORDERED-Ordered choice`，在 Error ditribution 字段中选择 `Normal` 以拟合多项 Probit 模型（图 4-50），然后单击 OK。图 4-51 中得到的结果显示估计参数具有良好的个体显著性（也许 `SUB` 除外，其显著性约为 85%）。联合显著性非常高，因为似然比统计量的 p 值非常小。伪 R² 接近 60%。信息准则（Akaike、Schwarz 和 Hannan-Quinn）的值是合适的。

![image](img/image666.png)![image](img/image138.png)

图 4-50      图 4-51

要估计有序多项 Logit 模型，选择 `Quick→ Estimate Equation`，在 Specification 选项卡的 Equation Specification 字段中输入拟合模型的方程，在 Method 字段中选择 `ORDERED-Ordered choice`，在 Error distribution 字段中选择 `Logistic` 以拟合多项 Logit 模型（图 4-52），然后单击 OK。图 4-53 中得到的结果显示估计参数具有良好的个体显著性（也许 `SUB` 除外，其显著性约为 85%）。联合显著性非常高，因为似然比统计量的 p 值非常小。伪 R² 接近 60%。信息准则（Akaike、Schwarz 和 Hannan-Quinn）的值是合适的。可以观察到拟合优度统计量的结果与 Probit 模型的情况非常相似。

![image](img/image312.png)![image](img/image165.png)

图 4-52      图 4-53

最有效的估计方法将是 Akaike、Schwarz 和 Hannan-Quinn 信息准则值最低且似然函数值最高的方法。汇总如下：

![image](img/image107.png)

信息准则值最低且似然函数值最高的方法是 Probit 模型。因此，最佳拟合由有序多项 Probit 模型提供。

### Exercise 4-2

在西班牙家庭电视拥有情况的一项研究中，对 940 个家庭进行了调查，询问家庭中的电视数量（`TV`）、年收入（以百万货币单位计，`FI`）以及家庭户主的教育水平（`NI`）。变量 `TV` 可以取 1、2 或 3，取决于家庭拥有 1 台、2 台和 3 台或更多电视机。家庭户主的教育水平已通过四个等级编码（Básica、Bachillerato superior、Universitaria media 和 Universitaria superior），其整数值分别为 1 至 4。利用包含在文件 `7-8.wf1` 中的指定数据，我们被要求拟合一个 logit 模型，用来解释家庭拥有给定数量电视机的概率如何取决于上述定义的其余变量。

对于户主受教育程度为基础水平（`NI=1`）且年收入为三百万货币单位（`IF=3`）的家庭，求其仅拥有一台电视机的概率。还计算该家庭拥有 2 台电视机的概率。此外，计算该家庭拥有三台或以上电视机的概率。

计算对于年收入为四百万货币单位且户主受教育程度为基础水平的家庭拥有两台电视机的边际效应，与户主受教育程度为高中时的情况相比。数据可在文件 `4-2.wf1` 中找到。

由于响应变量具有多于两个且可排序的类别，因此这是一个有序多项式 Logit 模型：

![image](img/image148.png)

要估计有序多项式 Logit 模型，选择 `Quick→ Estimate Equation`，在 Specification 标签的 Equation Specification 字段中输入拟合模型的方程，在 Method 字段中选择 `ORDERED-Ordered choice`，在 Error ditribution 字段中选择 Logistic 以拟合多项式 Logit 模型（图 4-54）并点击 OK。图 4-55 中的结果显示估计参数具有良好的个体显著性。联合显著性非常高，因为似然比统计量的 p 值非常小。Pseudo R² 非常接近 1（0.88）。信息准则（Akaike、Schwarz 和 Hannan-Quinn）的值是合适的。

对于户主受教育程度为基础水平（`NI=1`）且年收入为三百万货币单位（`IF=3`）的家庭，其仅拥有一台电视机的概率为

![image](img/image418.png)

对于上述家庭，其拥有两台电视机的概率为：

![Texto, Carta Descripción generada automáticamente](img/image460.png)

对于上述家庭，其拥有三台或以上电视机的概率为：

![image](img/image595.png)

![image](img/image593.png)![image](img/image472.png)

图 4-54      图 4-55

要计算对于年收入为四百万货币单位且户主受教育程度为基础水平的家庭拥有两台电视机的边际效应，与户主受教育程度为高中时的情况相比，必须分别计算每种情况的概率并求其差值。我们有：

![Texto, Carta Descripción generada automáticamente](img/image684.png)

![Texto, Carta Descripción generada automáticamente](img/image309.png)

有序的边际效应被获得为上述两个概率之间的差值：

![image](img/image074.png)

### 练习 4-3

文件 `4-3.wf1` 包含 1445 名囚犯的数据，关于囚犯获释后被重新逮捕前的月数（`durat`）。认为 `log(durat)` 取决于囚犯是否参与了监狱就业项目（`workprg`）、之前的定罪次数（`priors`）、在监狱中服刑的月数（`tserved`）、囚犯是否使用酒精（`alcohol`）、囚犯是否使用毒品（`drugs`）、所犯的罪行是否严重（`felon`）、囚犯是否为黑人（`black`）、囚犯是否已婚（`married`）、囚犯的教育水平（`educ`）和囚犯的年龄（`age`）。还已知在 1445 名囚犯中，有 893 人在被跟踪期间未被逮捕。我们还拥有一个指示每个观测值是否被删失的虚拟变量（`cens`）。

基于上述信息，使用 Tobit 模型，估计并解释 `log(durat)` 变量与剩余解释变量之间的关系，并解释结果。

由于有囚犯在最后一次获释后未被重新逮捕，我们处理的是右删失的 Tobit 模型，删失由充当删失指示变量的删失变量定义。

我们将通过最大似然法估计右删失 Tobit 模型。为此，选择 `Quick→ Estimate Equation`，在 Specification 标签的 Equation Specification 字段中写出拟合模型的方程，在 Method 字段中选择 `CENSORED-Censored or truncated data (Tobit)`，将删失变量放在 Right 字段中并标记 Zero/One indicator of censoring，因为 Tobit 模型在右侧删失且删失指示变量为删失变量，选择 Normal 因为我们考虑正态分布模型（图 4-56）并点击 Accept。图 4-57 中的结果显示估计参数具有良好的个体显著性（`workprg` 和 `educ` 除外）。信息准则的值不是太高且彼此相当一致。

![image](img/image109.png)![image](img/image011.png)

图 4-56    图 4-57

变量 `priors` 和 `tserved` 被发现具有负效应。刑期多一次的囚犯会使重新逮捕的时间减少 14%。多服刑一个月会使重新逮捕的时间减少 1.9%。使用毒品的个人（`drugs = 1`）重新逮捕所需时间大约减少 29.8%![image](img/image348.png)。

黑人个人被重新逮捕所需时间比白人个人大约少 54.3%![image](img/image434.png)。

观察到如果我们通过 OLS 估计模型而不考虑 1445 个观测值中有 893 个被删失，我们会得到不同的结果。为此，选择 `Quick→ Estimate Equation`，在 Specification 标签的 Equation Specification 字段中输入拟合模型的方程，在 Method 字段中选择 `LS-Two stage Least Squares (NLS and ARMA)` 以进行最小二乘拟合（图 4-58）并点击 OK。

图 4-59 中的结果显示估计参数具有良好的个体显著性（`workprg` 和 `educ` 除外）以及联合显著性。信息准则的值不是太高且彼此相当一致。Durbin Watson 统计量非常接近 2，表明不会存在序列自相关的問題。拟合与删失 Tobit 模型的拟合不一致。尽管参数估计值差异不大，其中一个参数的符号发生了变化（`workprg`），这正是其中一个个体不显著的变量。

![image](img/image396.png)![image](img/image429.png)

图 4-58    图 4-59

––––––––

![image](img/scene_break.png)

### 练习 4-4

这是研究两种止痛药对头痛的效果。患者被分为两组，使每组接受不同类型的止痛药（`TYPE`），并记录每位患者在服用止痛药后头痛缓解所需的时间（`MINUT`）。由于在观察期结束时仍可能有患者头痛，这是一种右删失数据的情况。删失变量（`CENS`）对于删失数据为 1，对于未删失数据为零。数据收集在文件 `4-4.wf1` 中。

拟合适当的模型来解释头痛缓解时间作为患者组函数的模型，以便比较两种止痛药。假设正态、逻辑和极值分布拟合模型。比较三个模型。

由于在观察期结束时仍可能有患者头痛，这是一种右删失 Tobit 模型的情况，删失由充当删失指示变量的变量 `CENS` 定义。

我们将通过最大似然法估计右删失的 Tobit 模型。为此，选择 `Quick→ Estimate Equation`，在 `Specification` 选项卡的 `Equation Specification` 字段中写出拟合模型的方程，在 `Method` 字段中选择 `CENSORED-Censored or truncated data (Tobit)`，将删失变量放入 `Right` 字段并勾选 `Zero/One indicator of censoring`，因为 Tobit 模型在右侧删失，删失指示变量为 `CENS` 变量，选择 `Normal` 因为我们考虑的是正态分布的模型（图 4-60）并点击 `Accept`。图 4-61 中的结果得到，估计参数具有良好的个体显著性。信息准则的值是可以接受的并且彼此一致。

![image](img/image069.png)![image](img/image471.png)

图 4-60    图 4-61

可以观察到，对于组 1 中的患者（`TYPE = 1`），头痛缓解时间为 `17.317 + 3.666*1 = 20.983` 分钟，而对于组 2 中的患者（`TYPE = 2`）为 `17.317 + 3.666*2 = 24.649` 分钟。可以观察到给予组 1 的止痛药更有效，因为疼痛在比给予组 2 的止痛药更短的时间内消退。

为了拟合假设对数分布的右删失 Tobit 模型，我们在 `Equation Estimation` 屏幕的 `Distribution` 字段中指向 `Logistic`（图 4-62）。点击 `OK` 得到图 4-63 中的结果，估计参数具有良好的个体显著性。信息准则的值是可以接受的并且彼此一致。还观察到与正态分布模型相比差异非常小。

![image](img/image557.png)![image](img/image150.png)

图 4-62    图 4-63

为了拟合假设对数分布的右删失 Tobit 模型，我们在 `Equation Estimation` 屏幕的 `Distribution` 字段中指向 `Extreme value`（图 4-64）。点击 `OK` 得到图 4-65 中的结果，估计参数具有良好的个体显著性。信息准则的值是可以接受的并且彼此一致。还观察到与正态和 Logit 分布模型相比差异很小。

![image](img/image497.png)![image](img/image307.png)

图 4-64    图 4-65

在估计了三种分布的 Tobit 模型后，我们将对它们进行比较以选择最合适的模型。最有效的模型将是 `Schwarz` 和 `Hannan-Quinn` 信息准则值最低且似然函数值最高的模型。汇总如下：

![image](img/image365.png)

信息准则值最低且似然函数值最高的模型是对数分布模型，与正态分布模型相比差异非常小。Weibull 分布（极值）模型在此情况下最不合适。因此，最佳拟合由右删失的对数分布 Tobit 模型提供。

# 第 5 章

| ![image](img/chapter_title_corner_decoration_left.png) ||  || ![image](img/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](img/chapter_title_above.png)

## 面板数据的广义线性模型。非线性面板模型

![image](img/chapter_title_below.png)

| ![image](img/chapter_title_corner_decoration_left.png) ||  || ![image](img/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](img/chapter_title_above.png)

### 5.1 面板数据的介绍：数据结构

![image](img/chapter_title_below.png)

面板数据是一种特殊的样本，其中在一段时间内跟踪了若干经济主体的行为。这样，研究人员就可以利用在某一瞬间考虑所有经济主体时获得的横截面（或截面）数据来执行经济分析并设定模型。这样就可以评估所有研究对象在不同时间点上共同表现出的不同行为模式。或者，可以考虑每个经济主体在样本所有时间段内的演变所给出的时间序列来进行同样的分析。在后一种情况下，可以在样本的整个时间间隔内检查个体行为的个体差异模式。

因此，面板数据结构的一个基本特征是其二维性。一个维度是个体列表，另一个维度是时间点。以西班牙财政研究所编制的个人所得税面板（`IRPF panel`）为例，其目的是建立一个数据库，其中包含同一纳税人逐年的所得税申报表。不同的个体是共同税收领土（不包括巴斯克地区和纳瓦拉自治区）的个人所得税纳税人，目前时间间隔从 1999 年到 2008 年。

在下面的段落中，我们更深入地探讨嵌入面板数据集两个维度的数据结构。一方面是横截面或截面数据，另一方面是时间序列数据。

| ![image](img/chapter_title_corner_decoration_left.png) ||  || ![image](img/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](img/chapter_title_above.png)

#### 5.1.1 横截面数据

![image](img/chapter_title_below.png)

在应用经济学工作中最重要的数据结构中，我们有横截面数据或截面数据。横截面数据集是由在给定时间点收集的个体、家庭、企业、城市、州、国家或其他各种单位组成的样本。一般来说，我们可以假设横截面数据是通过从总体中随机抽样获得的。例如，如果我们通过从在职人口中随机选择 500 人来获得工资、教育、经验和其他特征的信息，我们可以说我们拥有整个在职人口的随机样本。

在我们考虑的个人所得税面板中，我们考虑纳税申报模型中包含的所有变量，并将它们针对某一年度进行分析。考虑到不同的年份，我们将逐年拥有所有横截面。
