

在上述程序中，数据存储于数组 data 中。随后可以使用 For 语句逐个检查数组的内容。如果当前元素大于最大值，则更新最大值，并同时更新其位置。

最后，使用 MsgBox 函数显示结果，该函数会打印最大值及其位置。要执行上述程序，请将上述代码写入 VBA 编辑器，然后按下 [F5] 键或点击 [运行宏] 按钮。

此程序可用于找出回归分析结果中解释变量的最大 p 值，方法是删除该解释变量并重新执行回归分析，该分析结果已输出到 Excel 工作表中。

## 2.3.5. 使用 Excel VBA 实现变量缩减法

回归分析中描述的变量缩减法通过 VBA 实现。在此实现中，流程是找到 $t$ 值的绝对值中最小的那个值（代替 $p$ 值），然后移除该变量并重复回归分析。在 $p$ 值为 5% 的水平上，$t$ 值的绝对值通常大于或等于 2，并且彼此呈负相关。

假设 Excel 工作表的第一列包含因变量数据，第二列及后续列（共对应解释变量的数量）包含解释变量数据。假设第一行的第二列输入了解释变量的数量，第一列输入了样本量。回归分析的结果（解释变量的系数、$p$ 值和 $t$ 值）应与最后一行数据之间空一行，输出到左上角单元格（标记为 Summary）。

以下是一个将变量缩减法应用于调查结果以缩小显著影响目标函数的目标变量的示例。在此调查中，向 106 名大学一年级学生发放了问卷，要求他们对与大学生满意度和期望水平相关的九个不同项目按区间量表作答。区间量表是一种定量测量量表，它不是顺序量表，两个变量之间的差异是有意义且相等的，而零点的存在是可选的。当您执行变量缩减法的 VBA 程序时，会发现保留了两个基本项目（图 2.20）。

![](img/fa57e7010b16a211d5cf69ebb17e416e_68_0.png)

![](img/fa57e7010b16a211d5cf69ebb17e416e_68_1.png)

图 2.20. 使用变量缩减法分析调查结果的示例。

为了做准备，首先获取执行数据分析工具下的“回归”、删除列并将文本左对齐的宏输出。开启“录制宏”，执行数据分析工具下的“回归”，然后删除列，并执行“左对齐”。正如您将在结果中注意到的那样，需要特定的 Excel 设置来指定行和列。要在 VBA 程序中实现这一点，您需要学习如何操纵字符型数据。我们现在将讨论如何实现这一点。

在此程序实现中，需要四种类型的字符型数据操作。

-   从字符型数据获取字符代码：要将字符型数据 A 的字符代码分配到第一行第三列，请编写以下内容：`Cells(1,3) = Asc("A")`
-   从字符代码转换为字符型数据：要将字符代码为 66 的字符型数据分配到第一行第四列，请编写以下内容：`Cells(1,4)=Chr(66)`
-   将整型数据转换为字符型数据：要将整型数据 NROWS + 4 转换为字符型数据并将其分配到第一行第五列，请编写以下内容：`Cells(1,5)=str(NROWS + 4)`
-   连接字符串：要在第一行第六列连接并分配三个字符型数据 NR，请编写以下内容：`Cells(1,6)="B2."+"L"+"20"`

要在 VBA 程序中查找 $t$ 值绝对值最小的解释变量数据列，请编写以下代码。

```vba
<Begin>
TMIN = 999999
For j = 1 To CVARS
TVAL = Abs(Cells(j + NLINES + 20, 4))
If TVAL < TMIN Then
TMIN = TVAL
IMIN = j
End If
Next j
<End>
```

CVARS 表示解释变量的数量，NLINES 表示样本量，TMIN 表示当前的最小值。初始时分配一个较大的数值（999999）。j + NLINES + 20 是写入 $t$ 值的行号。要删除 $t$ 值绝对值最小的列，请在 VBA 程序中编写以下宏：

```vba
<Begin>
TRange = Chr(Asc("B") + IMIN - 1)
Columns(TRange).Select
Selection.Delete Shift:=xlToLeft
CVARS = CVARS - 1
<End>
```

解释变量数据从 B 列开始；因此，选择第 IMIN 个解释变量数据列（该数据列名为字符型数据 TRange），删除它，并执行左对齐。删除列还会使当前阶段的解释变量数量（CVARS）减少一个。

执行数据分析工具下“回归”的宏如下：

```vba
<Begin>
XRANGE = "B2:" + Chr(65 + NVARS - i + 1) + Trim(Str(NLINES + 2))
Application.Run "ATPVBAEN.XLAM!Regress",
ActiveSheet.Range(YRANGE), _ActiveSheet.Range(XRANGE),
False, True, , ActiveSheet.Range(OVERVIEW), _False, False,
False, False, , False
<End>
```

"_" 表示程序行继续；因此，以 Application.Run 开头的语句跨三行。列出了回归向导中用户指定的信息。因此，复选框由 True/False 决定，以指示是否选中或未选中。YRANGE 是因变量所在的列，XRANGE 是解释变量的列列表，OVERVIEW 是将列出回归分析结果的数据区域的左上角单元格。

将上述三个部分连接起来即完成变量缩减程序。完成的版本如下所示。

```vba
<Begin>
Sub reduce_variables()
NVAR S = Cells(1, 2)
NLINES = Cells(1, 1)
criteria = Cells(1, 3)
If criteria < 1 Then criteria = 2
YRANGE = "A2:A" + Trim(Str(NLINES + 2))
OVERVIEW = "A" + Trim(Str(NLINES + 4))
CVARS = NVARS
For i = 1 To NVARS
XRANGE = "B2:" + Chr(65 + NVARS - i + 1) + Trim(Str(NLINES + 2))
Application.Run "ATPVBAEN.XLAM!Regress",
ActiveSheet.Range(YRANGE), _ActiveSheet.Range(XRANGE),
False, True, , ActiveSheet.Range(OVERVIEW)_, False, False, False, False, , False
TMIN = 999999
For j = 1 To CVARS
TVAL = Abs(Cells(j + NLINES + 20, 4))
If TVAL < TMIN Then
TMIN = TVAL
IMIN = j
End If
Next j
If TMIN > criteria Then
Exit For
End If
TRange = Chr(Asc("B") + IMIN - 1)
Columns(TRange).Select
Selection.Delete Shift:=xlToLeft
CVARS = CVARS - 1
Next i
End Sub
<End>
```

变量判据设置为 $t$ 值的绝对值。如果设置为 2，则绝对值小于或等于 2 的 $t$ 值对应的解释变量将被删除。Trim 函数用于去除字符型数据中字符前后的空格。

## 2.4. 假设分析

Excel 的假设分析工具允许您为数据设置各种条件，并据此模拟结果。Excel 提供两种假设分析工具：一种是“数据表”，另一种是“方案管理器”。本节将向您展示如何使用数据表进行假设分析。

在执行假设分析之前，使用温度数据执行回归分析。用 2000 年 1 月东北地区 14 个主要城市的平均温度数据，通过经度和纬度表示。由于我们要找出最低气温，除了经纬度外，我们还使用平方数据（$x^{2}, y^{2}, xy$）在二次曲面上表示温度。也就是说，温度是通过以下方式计算的

