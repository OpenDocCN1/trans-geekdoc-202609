

# 第一章 数字数字处理：数据究竟是什么？

## 表 1-8. 具有不同部分的期刊文章元数据表

| 论文编号 | 引言 | 方法 | 结论 | 参与者 | 过程 | 总结 |
|---|---|---|---|---|---|---|
| 1 | 100 | 250 | 250 | | | |
| 2 | 110 | 400 | 150 | | | |
| 3 | 75 | 350 | 320 | | | |
| 4 | 55 | 90 | 150 | | | |
| 5 | 85 | | 125 | 230 | 100 | |
| 6 | 170 | 350 | | | | 325 |

现在我们有一组带有缺失值的列。我们稍后会处理缺失数据的挑战，因为你对处理方式的选择会对后续产生影响。但对于表 1-8 来说，填入 0 可能是避免缺失数据的合理解决方案——因为某个章节中不存在该论文未包含的单词。但随着我们查看的论文越来越多，列数只会增加，最终会变得难以处理，并包含大量的 0。这比处理大多数结构化数据要困难得多（尽管现实世界中的结构化数据也有缺失数据）。

最后，表示这种数据意味着我们丢失了大量信息——例如数据出现在某篇论文的具体章节。我们将在后面的章节中讨论非结构化数据，但这里的要点是：某些数据比其他数据具有更内在的结构。

数据是否是结构化的通常很清楚，但半结构化数据则介于两者之间。XML、HTML 和 JSON 具有某些结构，但还不足以被真正的结构化数据。然而，将它们转换为表格格式比非结构化数据更容易且更直观。请参见图 1-4 的这三种格式的示例。

| XML | HTML | JSON |
| --- | --- | --- |
| <animals> | <html> | { |
| <animal> | <head> | 'animals': { |
| <id>id</id> | <title>Two Cats</title> | 'id': '1', |
| <species>species</species> | <body> | 'species': 'cat', |
| <name>Marvin</name> | <p>Cat to Know the Cats</p> | 'name': 'Marvin', |
| <age>14</age> | <h2>Madox</h2> | 'age': '14', |
| <age_unit>age_unit</age_unit> | <p>Marvin is a great cat even though he has health problems.</p> | 'age_unit': 'years', |
| <sex>male</sex> | <paragraph>8-year-old Siamese cat likes to bite hard things like metal chair legs</paragraph> | 'sex': 'neutral male', |
| <breed>domestic</breed> | <h2>Madox</h2> | 'breed': 'domestic', |
| <colors> | <paragraph>Madox is a slightly obnoxious</paragraph> | 'colors': { |
| <color1>tabby</color1> | </body> | 'color1': 'tabby', |
| <color2>brown</color2> | </html> | 'color2': 'brown', |
| <color3>white</color3> | | }, |
| <deceased>deceased</deceased> | | 'deceased': true |
| <animal> | | } |
| <animal> | | { |
| <id>2</id> | | 'id': '2', |
| <species>cat</species> | | 'species': 'cat', |
| <name>Madox</name> | | 'name': 'Madox', |
| <age>8</age> | | 'age': 8, |
| <age_unit>years</age_unit> | | 'age_unit': 'years', |
| <sex>male</sex> | | 'sex': 'neutral male', |
| <breed>Siamese</breed> | | 'breed': 'Siamese', |
| <colors> | | 'colors': { |
| <color1>seal-point</color1> | | 'color1': 'seal-point', |
| <colors> | | } |
| <animal> | | } |
| <animal> | | { |
| <id>3</id> | | 'id': '3', |
| <name>Pelusa</name> | | 'name': 'Pelusa' |
| <animal> | | } |

**图 1-4. XML、HTML 和 JSON**

图 1-4 中的 XML 和 JSON 示例在三种不同的格式上代表完全相同的内容。HTML 风格的格式具有特定目的，告诉网页浏览器如何显示内容。这些示例看起来是结构化的，但原因在于每个标签（在 XML 中）或条目（在 JSON 中）在格式本身上都是可选的。在这种情况下，一只猫可以有多种颜色，也可以只有一种或一个没有。颜色标签可以完全不留，它仍然是有效的 XML。此外，还有一个标签/元素仅在条件为真时才存在，即 `deceased`（已去世）元素。它存在于第一只猫中，但不存在于第二只。但最重要的是，我们对第三只动物只有一个 ID 和一个名称，而这些仍然是有效的 XML 和 JSON 格式。使用这些数据的人可能会有自己的需求。正如将非结构化数据转换为表格格式很困难，半结构化数据的转换则要容易得多。

## 表 1-9. 动物细节

| 动物编号 | 物种 | 姓名 | 年龄 | 年龄单位 | 性别 | 品种 | 颜色1 | 颜色2 | 是否去世 |
|---|---|---|---|---|---|---|---|---|
| 1 | cat | Marvin | 14 | years | neutral male | tabby | brown | True |
| 2 | cat | Maddox | 8 | years | neutral male | Siamese | | |
| 3 | | Pelusa | | | | | | |

## 原始数据与派生数据

除了期刊文章示例外，我们目前讨论的所有数据都是**原始**的——关于现实世界的直接事实。这些数据进入计算机并以某种形式存储。但它们直接反映现实世界。我们经常谈论**派生**数据，这意味着它是通过其他数据产生的。

派生新数据在数据科学中非常强大且重要。派生数据的两种方式是**聚合**和**交互**。在结构化数据中，聚合是在一个列中进行的：我们可能会计算学生的平均身高。表 1-10 显示了身高聚合。

表 10. 身高聚合数据

| 性别 | 平均值（英寸） |
|---|---|
| 女性 | 65 |
| 男性 | 69 |
| 非二 | 67 |

交互是跨列行的：在科学数据集中，我们将空字段填充 0 后，可能会创建一个名为 `Intro Sum` 的新列，它是引言部分和结论部分的**和**。表 1-11 显示了带有交互变量的表格。

## 表 1-11. 带有交互变量的文章章节长度表

| 论文 | 引言 | 方法 | 结论 | 参与者 | 总结 | 引言+结论 |
|---|---|---|---|---|---|---|
| 1 | 100 | 250 | 250 | 0 | 0 | 350 |
| 2 | 110 | 400 | 150 | 0 | 0 | 260 |
| 3 | 75 | 350 | 320 | 0 | 0 | 395 |
| 4 | 55 | 90 | 150 | 0 | 0 | 205 |
| 5 | 85 | 0 | 125 | 230 | 100 | 210 |
| 6 | 170 | 350 | 0 | 0 | 0 | 325 | 170 |

