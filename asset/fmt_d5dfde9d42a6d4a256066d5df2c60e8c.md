
# 从银行短信中提取交易信息

让我们首先从 `bank_messages` 数据框的 `message` 列中提取提到的金额。这里我们假设所需的金额前面带有 INR 或 Rs。

```r
# 提取前面带有 "INR" 或 "Rs" 的金额
bank_messages <- bank_messages %>%
  mutate(amount = str_extract(message, "(?<=\\bINR\\s|\\bRs\\s)[0-9,]+\\.?[0-9]*"))

# 查看结果
View(bank_messages)
```

| Message | Amount |
| --- | --- |
| Your Bank Acc XX998006 is debited for INR 555.68 on 10-Nov-23 towards paytmqroihh5855ap@paytm. UPI Ref No 368033761556. If you have any concerns, please contact us at 1800-267-3456. | 555.68 |
| Dear Customer, Your A/C XXXXX123456 has a credit by Cheque of Rs 80,000.00 on 30/10/23. | 80,000.00 |

表 6.14：提取了交易金额的银行短信数据框

让我们分解一下 `str_extract` 函数中使用的正则表达式：

`"(?<=\\bINR\\s|\\bRs\\s)[0-9,]+\\.?[0-9]*"`

*   `(?<=\\bINR\\s|\\bRs\\s)`：这是一个正向后顾断言。它检查文本前面是否带有单词 INR 或 Rs（区分大小写）、单词边界 (`\\b`) 和空格 (`\\s`)。`\\b` 确保 INR 或 Rs 是一个完整的单词，而不是另一个单词的一部分。
*   `[0-9,]+`：这部分匹配一个或多个数字（0-9）或逗号。这允许捕获使用逗号作为千位分隔符的金额，例如 80,000。
*   `\\.?`：这匹配一个可选的小数点 (`.`)。反斜杠 (`\\`) 用于转义点号，因为在正则表达式中，点号是一个匹配任意字符的特殊字符。问号 (`?`) 使小数点成为可选的，从而允许整数和小数金额。
*   `[0-9]*`：匹配小数点后零个或多个数字，捕获金额的小数部分。

接下来，我们将创建两列 `credit` 和 `debit`，指示 `message` 列是否包含单词 credit 和 debit，包括 credited 和 debited 等变体。正则表达式使用 `str_detect` 函数来检查 "message" 列中是否存在指定的模式。

```r
# 添加列以指示消息是否包含 "credit" 或 "debit"
bank_messages <- bank_messages %>%
  mutate(
    has_credit = str_detect(message, "\\bcredit(ed)?\\b"),
    has_debit = str_detect(message, "\\bdebit(ed)?\\b")
  )

# 查看数据框
View(bank_messages)
```

| message | amount | has_credit | has_debit |
| --- | --- | --- | --- |
| Your Bank Acc XX998006 is debited for INR 555.68 on 10-Nov-23 towards paytmqroihh5855ap@paytm. UPI Ref No 368033761556. If you have any concerns, please contact us at 1800-267-3456. | 555.68 | FALSE | TRUE |
| Dear Customer, Your A/C XXXXX123456 has a credit by Cheque of Rs 80,000.00 on 30/10/23. | 80,000.00 | TRUE | FALSE |

表 6.15：带有贷记和借记指示符的银行短信数据

上述命令确定每条消息是否包含单词 credit 或 debit 及其变体。`dplyr` 包中的 `mutate` 函数用于向银行短信数据框添加两个新列 `has_credit` 和 `has_debit`。

*   `\\b`：这是一个单词边界断言。它确保匹配 credit 或 debit 作为完整单词，而不是作为另一个单词的一部分。
*   `credit(ed)?`：此部分匹配单词 `credit`，并通过 `(ed)?` 使 `ed` 部分变为可选。这允许同时匹配 `credit` 和 `credited`。
*   `debit(ed)?`：与 `credit` 部分类似，此部分匹配单词 `debit`，并使 `ed` 部分变为可选，允许匹配 `debit` 和 `debited` 等变体。
*   如果消息包含单词 `credit` 或 `credited`，则 `has_credit` 列将为 `TRUE`，否则为 `FALSE`。同理，如果消息包含单词 `debit` 或 `debited`，则 `has_debit` 列将为 `TRUE`，否则为 `FALSE`。

接下来，我们将从 `bank_messages` 数据框的 `message` 列中提取日期。日期预期采用 `dd/mm/yy` 或 `dd-mmm-yy` 格式。生成的 `date` 列将包含在每条消息中找到的日期列表。

```r
# Extract date from the message column
bank_messages <- bank_messages %>%
  mutate(
    date = str_extract_all(message, "\\b\\d{2}/\\d{2}/\\d{2}|\\d{2}-[a-zA-Z]{3}-\\d{2}\\b")
  )
# Display the modified data frame with the new "date" column.
View(bank_messages)
```

| message | amount | has_credit | has_debit | date |
| --- | --- | --- | --- | --- |
| Your Bank Acc XX998006 is debited for INR 555.68 on 10-Nov-23 towards paytmqroihh5855ap@paytm. UPI Ref No 368033761556. If you have any concerns, please contact us at 1800-267-3456. | 555.68 | FALSE | TRUE | 10-Nov-23 |
| Dear Customer, Your A/C XXXXX123456 has a credit by Cheque of Rs 80,000.00 on 30/10/23. | 80,000.00 | TRUE | FALSE | 30/10/23 |

表 6.16：提取了交易日期的银行消息数据

上述命令使用正则表达式提取两种格式的日期：`dd/mm/yy` 和 `dd-mmm-yy`。`str_extract_all` 函数提取每条消息中所有出现的指定日期模式。

*   `\\b`：单词边界断言，确认日期模式作为一个完整单词被匹配，而不是作为另一个单词的一部分。
*   `\\d{2}/\\d{2}/\\d{2}`：此部分匹配 `dd/mm/yy` 日期格式。它查找两位数字（日），后跟一个正斜杠，两位数字（月），另一个正斜杠，以及两位数字（年）。
*   `|`：管道符号充当逻辑 OR，允许正则表达式匹配 `dd/mm/yy` 或 `dd-mmm-yy` 格式。
*   `\\d{2}-[a-zA-Z]{3}-\\d{2}`：此部分匹配 `dd-mmm-yy` 日期格式。它查找两位数字（日），后跟一个连字符，三个字母代表月份（由于 `[a-zA-Z]` 不区分大小写），另一个连字符，以及两位数字（年）。
*   `\\b`：另一个单词边界断言，确保匹配的日期模式的完整性。

下图展示了用于提取日期的正则表达式的分解结构。

![](img/Figure6.1.png)

图 6.1：从消息列提取日期的正则表达式

让我们检查另一种场景：从 `message` 列中提取遵循特定格式的电话号码。

```r
# Extract phone number
bank_messages <- bank_messages %>%
  mutate(
    phone_number = str_extract(message, "\\b\\d{4}-\\d{3}-\\d{4}\\b")
  )
```

上述命令提取预期遵循 `xxxx-xxx-xxxx` 格式的电话号码。

```r
# View the dataframe
View(bank_messages)
```

| message | amount | has_credit | has_debit | date | phone_number |
| --- | --- | --- | --- | --- | --- |
| Your Bank Acc XX998006 is debited for INR 555.68 on 10-Nov-23 towards paytmqroihh5855ap@paytm. UPI Ref No 368033761556. If you have any concerns, please contact us at 1800-267-3456. | 555.68 | FALSE | TRUE | 10-Nov-23 | 1800-267-3456 |
| Dear Customer, Your A/C XXXXX123456 has a credit by Cheque of Rs 80,000.00 on 30/10/23. | 80,000.00 | TRUE | FALSE | 30/10/23 | NA |

表 6.17：提取了电话号码的银行消息数据

正则表达式 `\\d{4}-\\d{3}-\\d{4}` 匹配电话号码模式 `xxxx-xxx-xxxx`。它查找四位数字，后跟一个连字符，三位数字，另一个连字符，以及四位数字。

正如你所见，我们使用正则表达式从 `bank_messages` 数据框中提取了交易类型、金额、日期和电话号码。这些信息可用于各种目的，例如欺诈检测和客户细分。

## 结论

本章探讨了使用 `stringr` 包操作和清理字符串的基本技术。`stringr` 提供了多种用于操作字符串的函数。本章涵盖了基本字符串操作，如更改大小写、计算字符串长度、替换和移除子字符串、处理空白字符、填充和连接字符串。正则表达式提供了一种通用且高效的方式来搜索、编辑、操作和提取数据。它们可用于执行各种任务，例如：

*   **数据清洗**：移除不需要的字符、统一数据格式和纠正错误。
*   **特征工程**：从现有数据创建新特征，例如提取日期和时间信息、识别产品类别和检测垃圾邮件。
*   **文本分析**：正则表达式可用于执行各种文本分析任务，如实体提取。

在下一章中，您将学习如何使用数据可视化以可视化方式呈现您的发现。

## 加入我们书籍的 Discord 空间

加入书籍的 Discord 工作区，获取最新动态、优惠、全球科技资讯、新书发布及作者见面会：

[`discord.bpbonline.com`](https://discord.bpbonline.com)

![](img/fm1.png)

# 第 7 章：数据可视化

## 简介

数据可视化是艺术与科学的融合。在这两个方面之间实现微妙的平衡对于准确传达数据至关重要。在创建具有视觉吸引力的图形的同时准确呈现数据，是有效沟通的关键。数据可视化可以揭示模式、识别异常值、指导数据转换，并为机器学习模型启发新特征。成功的数据可视化应在不误导或扭曲数据的前提下准确传达数据，同时具有美感以增强其影响力。分散数据注意力的视觉元素（如刺眼的颜色或不平衡的元素）会阻碍解读。`ggplot2` 是一个广泛使用的 R 数据可视化包，它采用基于图形语法的绘图系统。这简化了创建复杂且富有洞察力的可视化的过程。它为指定图表的不同元素（如数据、美学映射和几何对象）提供了一套一致的规则。

## 结构

在本章中，我们将详细阐述与数据可视化相关的基本概念。

*   `ggplot2` 模板与美学映射
*   可视化分布
    *   条形图
    *   直方图
    *   密度图
*   可视化比例
    *   饼图
    *   堆叠条形图
*   可视化关联
    *   箱线图
    *   散点图
*   使用折线图可视化时间序列

## 目标

本章将教您如何使用数据可视化正确呈现数据。您将获得使用 `ggplot2` 包生成多种可视化的知识，包括条形图、直方图、密度图、箱线图、饼图、折线图和散点图。您还将学习如何可视化时间序列数据和数据分布。在本章结束时，您将能够创建信息丰富且引人入胜的数据可视化，有效地向他人传达您的发现。

## ggplot2 模板与美学映射

### ggplot2：图形语法

与许多其他图形包不同，`ggplot2` 基于 Wilkinson 的*图形语法*（2005）运行，拥有一套独特的语法体系。这种语法允许您通过组装不同的组件来构建图形，使 `ggplot2` 成为数据可视化的强大工具。`ggplot2` 的方法论鼓励迭代过程：从代表原始数据的基础层开始，逐步添加用于注释和统计摘要的额外层。这种迭代方法使创建图形的过程与我们典型分析中涉及的结构化思维保持一致。

在 Wilkinson 语法的基础上，Wickham (2009) 引入的 `ggplot2` 着重于图层的重要性，并将该语法调整为可与 R 语言集成。图形语法是将数据映射到几何对象（如点、线或条形）的美学属性（颜色、形状和大小）上。此外，图形还可能包含数据的统计变换以及关于图形坐标系统的细节。这些独立组件的深思熟虑的组合构成了一个全面且信息丰富的图形。

#### 基本组件

每个 `ggplot2` 图形均由三个基本组件构建而成：

*   **数据**：图形的基础，代表您想要可视化的信息。
*   **几何对象（geom 函数）**：数据的视觉表现形式，由 geom 函数定义。Geom 函数决定构成图形的图形元素，如点、线、条形或多边形。
*   **美学映射**：数据与其视觉表现之间的连接，通过美学映射指定。美学映射将数据变量分配给视觉属性，如颜色、形状和大小，控制数据在图形上的显示方式。

要创建 `ggplot2` 图形，您可以使用以下模板组合这三个组件：

*   `ggplot(data = <YOUR_DATA>) +`
*   `geom_<YOUR_GEOM_FUNCTION>(aes(<YOUR_MAPPINGS>))`

将 `<YOUR_DATA>`、`<YOUR_GEOM_FUNCTION>` 和 `<YOUR_MAPPINGS>` 替换为您打算使用的特定数据集、geom 函数和映射。

#### 附加图层

除了数据、几何对象和美学映射这些基础组件外，`ggplot2` 还允许您通过引入完善和丰富图形的附加图层来增强视觉叙事能力。

*   **统计变换**：`stat` 函数直接在图形内对数据进行汇总和处理。
*   **标度**：它们将数据值映射到颜色、形状、大小和不透明度等美学属性。标度还有助于构建图例和坐标轴。
*   **坐标系**：它们通过映射数据坐标来组织几何对象。
*   **分面**：分面将数据分解为不同的子集，并在同一图形中将它们显示为多个较小的图形。这一强大技术允许您探索变量之间的关系，并识别在整体检查数据时可能不明显的模式。
*   **主题**：主题控制显示的细节，如字体大小和背景颜色。

`ggplot2` 所基于的图形语法认识到，一个图形是数据集、几何对象、一组映射、统计变换、位置调整、坐标系和分面方案的独特融合。下图展示了 `ggplot2` 模板的所有组件。

![](img/Figure7.1.png)

**图 7.1**：ggplot2 模板

现在，让我们探索如何利用此模板创建各种类型的图形。

#### 入门：包安装

要开始可视化，第一步是安装必要的包。我们有两种选择：要么加载包含 `ggplot2` 包的 `tidyverse`，要么采用更专注的方法，单独安装 `ggplot2`。

```r
# Load tidyverse:
library(tidyverse)

# Alternatively, install ggplot2
install.packages("ggplot2")
install.packages("forcats")

# Load ggplot2 and forcats
library(ggplot2)
library(forcats)
```

## 可视化分布

有效传达数据分布是数据分析的一个基本方面，可视化方法因变量的性质而异——无论是分类变量还是数值变量。本节探讨三种基本的可视化技术：条形图、直方图和密度图。

### 条形图

在许多情况下，我们关注的是理解一组给定数值的规模。设想一家零售企业想要描绘各产品类别（如电子产品、书籍和家居用品）在特定时间段内的销售业绩。又或一位网站所有者可能希望剖析其网站流量的来源，区分直接访问、搜索引擎推荐和其他来源。同样，一位教育工作者可能想展示学生在不同学科中取得的平均分数。在每种情况下，我们都面临这样一种场景：不同的类别（如产品类别、流量来源或学科）与相应的定量数值相关联。此类情况下的首选可视化方法是条形图。

有些人可能会避免使用条形图，因为他们认为条形图太过常见，但这是一个错误的假设。实际上，条形图的广泛使用反而对您有利，使您的受众能够更快地掌握您呈现的信息。受众无需费力去理解陌生的图表，而是可以专注于从视觉展示中提取有价值的见解。我们的眼睛可以轻松比较条形的长度，从而快速识别类别的排名，区分最大值和最小值，并感知它们之间的渐变变化。
