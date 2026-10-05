

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 1.5.2 使用 SPSS 进行一般和分段非线性估计

![image](d2d_images/chapter_title_below.png)

当变量之间的非线性模型更为一般，即除多项式项外还包含其他项时，SPSS 使用非线性回归过程进行估计，该过程使用迭代算法执行非线性最小二乘调整以找到解。作为示例，从文件 `cars.sav` 中，我们拟合一个将油耗与加速度的平方 (`acel`)、功率的立方 (`hp`) 和排量的对数 (`engine`) 关联的模型。

要执行非线性回归，请从 `Analyse` 菜单中选择→ `Regression`→ `Non-linear`（图 1-5），并从工作数据文件中的变量列表中选择数值因变量 `consumption`（图 1-6）。要为模型构造表达式，可以在模型表达式字段中输入表达式，或将组件（变量、参数、函数）粘贴到该字段中。通过点击 Parameters 并点击 Add 来定义参数，标识模型表达式中每个参数的名称和初始值（图 1-7）。在 Loss 按钮中选择非线性回归中的损失函数（图 1-8），即算法所最小化的函数。选择 `Sum of squared residuals` 以最小化残差平方和，或选择 `User-defined loss function` 以最小化不同的函数。

Constraints 按钮允许您输入模型变量的约束条件（图 1-9）。约束是对迭代求解过程中参数允许值的限制。

Options 按钮对话框（图 1-10）允许您选择自助法估计的标准误差（需要使用序列二次规划算法），估计方法（`Sequential quadratic programming` 或 `Levenberg-Marquardt`）。序列二次规划方法允许您指定新的最大迭代次数和步长限制值，并且可以更改下拉列表中关于最优性容差、函数精度和无限步长大小的选项。Levenberg-Marquardt 方法允许您指定最大迭代次数，并且可以更改下拉列表中关于平方和收敛和参数收敛的选项。您可以使用 Save 按钮（图 1-11）将多个新变量保存到活动数据文件中。可用的选项有：预测值、残差、导数和损失函数值。这些变量可在后续分析中使用，以检验模型拟合度或识别问题案例。

![image](d2d_images/image070.png)![image](d2d_images/image339.png)

Figure 1-5 Figure 1-6

![image](d2d_images/image526.png)![image](d2d_images/image672.png)

Figure 1-7 Figure 1-8

![image](d2d_images/image238.png)![image](d2d_images/image414.png)

Figure 1-9 Figure 1-10

![image](d2d_images/image692.png)

Figure 1-11

在模型表达式字段中，可以使用条件逻辑表达式在单个模型语句内引入分段模型（在定义域的不同部分采用不同形式的模型）。要在模型表达式或损失函数中使用条件逻辑，必须构造一系列项的和，每个条件对应一项。每项由逻辑表达式（在括号中）乘以该逻辑表达式为真时得到的结果表达式组成。例如，考虑一个分段模型，当 X < = 0 时等于 0，当 0 < X < 1 时等于 X，当 X > = 1 时等于 1。该示例的表达式为：![image](d2d_images/image511.png)所有括号中的逻辑表达式必须可求值为 1（真）或 0（假）。因此：如果 X < = 0，上式简化为 1*0 + 0*X + 0*1 = 0。如果 0 < X < 1，它简化为 0*0 + 1*X + 0*1 = X。如果 X > = 1，它简化为 0*0 + 0*X + 1*1 = 1。更复杂的示例可以通过替换不同的逻辑表达式和结果表达式轻松构造。请记住，双重不等式，如 0 < X < 1，必须写成复合表达式的形式 ![image](d2d_images/image040.png)

可以在逻辑表达式中使用字符串变量：(`city='Madrid'`)*`costliv` + (`city='Guadalajara'`)*0.59*`costliv`。这对于马德里居民得到一个表达式（变量 `costliv` 的值），对于瓜达拉哈拉居民得到另一个表达式（该值的 59%）。字符串常量必须用引号或撇号括起来，如此示例语法所示。

如果选择 `User-defined loss function`，则必须定义损失函数，其总和（在所有情况下）必须通过您选择的參数值最小化。大多数损失函数都包含特殊变量 `resid_`，它表示残差。默认损失函数 `Sum of squared residuals` 可显式输入为 `resid_**2`。如果您需要在损失函数中使用预测值，它等于因变量减去残差。可以使用条件逻辑指定条件损失函数。您可以在用户定义损失函数字段中输入表达式，或将表达式的组件粘贴到该字段中。字符串常量必须用引号或撇号括起来，数值常量必须以美国格式书写，以句点分隔小数部分。

在统计学方面，每次迭代都会获得参数估计值和残差平方和，并且对于每个模型都会获得回归平方和、残差、校正和未校正总和、参数估计值、渐近标准误差以及参数估计值的渐近相关矩阵。

在图 1-6 中按 OK 以获得模型估计。

![image](d2d_images/image630.png)

拟合在 5 次迭代中完成，系数 `R²` 高于 50%，拟合的模型方程如下：

––––––––

![image](d2d_images/scene_break.png)

![image](d2d_images/image159.png)

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 1.6 SAS 与非线性估计。PROC NLIN

![image](d2d_images/chapter_title_below.png)

`NLIN` 过程使用最小二乘法或加权最小二乘法拟合非线性模型。估计方法是迭代的，使用 Newton、梯度、Gass-Newton、Marquardt 或假位（DUD）算法。语法如下：

![image](d2d_images/image581.png)

`BOUNDS` 语句将估计参数限制为指定条件。`BY` 语句指定变量以执行子组。`DER` 语句指定一阶或二阶偏导数。`ID` 语句指定要添加到输出数据集的附加变量。`MODEL` 语句定义因变量与自变量之间拟合的关系。`OUTPUT` 语句创建输出数据集。`PARMS` 语句标识要估计的参数及其初始值。`CONTROL` 语句声明控制变量并指定其值。

