
# 表 6.3：标准化大小写后的图书数据

| product_name | product_category | product_id |
| :--- | :--- | :--- |
| Learning Google Cloud Vertex AI | Cloud and networking | 537 |

正如你所见，`product_name` 和 `product_category` 列现在均为小写。你可以使用 `str_to_upper()` 函数将字符串转换为大写。在文本分析中，将字符串转换为小写或大写是处理文本数据的基础操作。当比较字符串、消除大小写敏感性或统一格式化字符串时，这种转换是必要的。

例如，假设你有一个包含客户姓名和电子邮件地址的数据库。某些条目可能是大写，而另一些是小写。为了准确识别并移除重复记录，你需要将所有姓名和电子邮件转换为大写或小写。这样可以防止将 `business@bpbonline.com` 和 `Business@bpbonline.com` 错误地视为独立条目，从而确保数据完整性。

## 计算字符串长度

现在让我们使用 `str_length()` 函数计算 `product_name` 列的长度。计算每个产品名称长度的代码如下：

```r
# Calculate the length of the product_name
books <- books %>%
  mutate(product_name_length = str_length(product_name))

# View the modified data frame
View(books)
```

请参考下表：

| product_name | product_category | product_id | product_name_length |
| :--- | :--- | :--- | :--- |
| Mastering mean stack | Web development | 255 | 20 |
| Breaking ransomware | Security | 78 | 20 |
| Data science with R | ML and AI | 7077 | 20 |
| Learning Google Cloud Vertex Ai | Cloud and networking | 537 | 31 |

**表 6.4：包含产品名称长度的图书数据**

`str_length()` 函数在文本分析中具有多种用途，包括：

*   **验证输入数据**：`str_length()` 函数可通过根据指定标准检查输入数据的长度来验证数据。例如，在密码验证函数中，你可以使用 `str_length()` 确保输入密码至少有八个字符。如果密码少于八个字符，该函数可返回错误消息或直接拒绝输入。
*   **格式化输出数据**：通过填充字符串至固定长度来格式化输出数据。这在以表格或报表形式显示数据时非常有用，因为一致的格式至关重要。例如，向字符串添加前导空格直到达到指定长度，确保表格中所有行的列宽相同。
*   **分析文本数据**：计算与字符串长度相关的各种指标。例如，计算句子中单词的平均长度，或查找段落中最长的单词。

## 替换子字符串

移除特殊字符（如 URL 链接中的 `&`）通常是推荐的做法，因为不同的 Web 浏览器和服务器对特殊字符的解析可能不同。

以下代码使用 `str_replace_all()` 将 `books` 数据框 `product_category` 列中所有出现的 `&` 字符替换为空字符串。

```r
# Replacing substring from the column product_category
books <- books %>%
  mutate(product_category = str_replace_all(product_category, "&", ""))

# View the data frame
View(books)
```

| product_name | product_category | product_id | product_name_length |
| :--- | :--- | :--- | :--- |
| Mastering mean stack | Web development | 255 | 20 |
| Breaking ransomware | Security | 78 | 20 |
| Data science with R | ML and AI | 7077 | 20 |
| Learning Google Cloud Vertex Ai | Cloud networking | 537 | 31 |

**表 6.5：从产品类别中移除 `&` 后的图书数据**

`str_replace_all()` 是一个字符串操作函数，用于将字符串中所有出现的模式替换为替换字符串。在本例中，模式是 `&` 字符，替换字符串为空字符串。

`str_replace_all()` 函数可用于多种文本分析任务，例如移除停用词。停用词是指那些不太具备信息量的常用词，如 `and`、`the`、`is`；替换缩写为全拼；纠正拼写错误等。`str_replace()` 函数与 `str_replace_all()` 类似，但它仅针对并替换指定子字符串的**首次出现**。当你想要执行一次性替换而不影响同一单词后续出现的情况时，这非常有用。

## 移除不必要的空白字符

在文本分析中，`str_trim()` 和 `str_squish()` 函数常用于在应用情感分析、主题建模或机器学习算法等其他技术之前清理和预处理文本数据。

`str_trim()` 函数移除字符串开头和结尾的空白字符，有助于规范化数据。它接受一个参数，即待修剪的字符串。

```r
# Remove leading and trailing spaces in product_name and product_category
books <- books %>%
  mutate(product_name = str_trim(product_name),
         product_category = str_trim(product_category))

# Display the modified data frame
View(books)
```

| product_name | product_category | product_id | product_name_length |
| :--- | :--- | :--- | :--- |
| Mastering mean stack | Web development | 255 | 20 |
| Breaking ransomware | Security | 78 | 20 |
| Data science with R | ML and AI | 7077 | 20 |
| Learning Google Cloud Vertex Ai | Cloud networking | 537 | 31 |

**表 6.6：修剪产品名称和类别后的图书数据**

请注意每个书名和类别周围的前导和尾随空格已被移除。另一方面，`str_squish()` 除了像 `str_trim()` 一样修剪首尾空格外，还会将文本中多个连续的内部空格缩减为单个空格。在下面的代码中，我们将 `product_category` 列中的所有内部空白字符替换为单个空格。

```r
# Apply str_squish() to product_category column
books <- books %>%
  mutate(product_category = str_squish(product_category))

# View the data frame
View(books)
```

| product_name | product_category | product_id | product_name_length |
| :--- | :--- | :--- | :--- |
| Mastering mean stack | Web development | 255 | 20 |
| Breaking ransomware | Security | 78 | 20 |
| Data science with R | ML and AI | 7077 | 20 |
| Learning Google Cloud Vertex AI | Cloud networking | 537 | 31 |

**表 6.7：标准化产品类别后的图书数据**

此输出将连续的空白字符压缩为单个空格，使字符串更加简洁。此外，在 URL 中使用连字符（`-`）代替空格分隔单词是一种良好的实践，有助于用户和搜索引擎更好地阅读和理解。为了实现这一点，我们将把产品名称和类别中的所有空格替换为连字符。

```r
# Replacing all spaces in product names and categories with hyphens
books <- books %>%
  mutate(product_name = str_replace_all(product_name, " ", "-"),
         product_category = str_replace_all(product_category, " ", "-"))

# Display the dataframe
View(books)
```

| product_name | product_category | product_id | product_name_length |
| :--- | :--- | :--- | :--- |
| Mastering-MEAN-Stack | Web-development | 255 | 20 |
| Breaking-ransomware | Security | 78 | 20 |
| Data-science-with-R | ML-and-AI | 7077 | 20 |
| Learning-Google-Cloud-Vertex-AI | Cloud-networking | 537 | 31 |

**表 6.8：产品名称和类别中空格被替换后的图书数据**

## 填充
