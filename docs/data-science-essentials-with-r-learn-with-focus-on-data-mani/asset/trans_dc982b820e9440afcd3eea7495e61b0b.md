
*   `credit(ed)?`：此部分匹配单词 `credit`，并通过 `(ed)?` 使 `ed` 部分变为可选。这允许同时匹配 `credit` 和 `credited`。

*   `debit(ed)?`：与 `credit` 部分类似，此部分匹配单词 `debit`，并使 `ed` 部分变为可选，允许匹配 `debit` 和 `debited` 等变体。

*   如果消息包含单词 `credit` 或 `credited`，则 `has_credit` 列将为 `TRUE`，否则为 `FALSE`。同理，如果消息包含单词 `debit` 或 `debited`，则 `has_debit` 列将为 `TRUE`，否则为 `FALSE`。

接下来，我们将从 `bank_messages` 数据框的 `message` 列中提取日期。日期预期采用 `dd/mm/yy` 或 `dd-mmm-yy` 格式。生成的 `date` 列将包含在每条消息中找到的日期列表。

```
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

![](images/Figure6.1.png)

图 6.1：从消息列提取日期的正则表达式

让我们检查另一种场景：从 `message` 列中提取遵循特定格式的电话号码。

```
# Extract phone number
bank_messages <- bank_messages %>%
  mutate(
    phone_number = str_extract(message, "\\b\\d{4}-\\d{3}-\\d{4}\\b")
  )
```

上述命令提取预期遵循 `xxxx-xxx-xxxx` 格式的电话号码。

```
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

### 加入我们书籍的 Discord 空间

加入书籍的 Discord 工作区，获取最新动态、优惠、全球科技资讯、新书发布及作者见面会：

[https://discord.bpbonline.com](https://discord.bpbonline.com)

![](images/fm1.png)

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
