

记录被定义为包含 Demo php 布局中所有字段（即 `$result`）的内容，并使用了表中的所有记录（`newFindAllCommand('Demo php')`）。你可能会认为，取决于布局中字段的数量和表中的记录数，这可能会产生大量数据。然而，当你继续往下看时，你会发现搜索“循环”可以快速处理 Records 文件中的内容进行解析，以便在网页上显示每个字段和记录。你甚至不需要显示布局上的每一个字段。你可以选择：

FileMaker PHP 方法被定义为脚本函数。大约有 70 种 FileMaker PHP 方法和大约 140 个 FileMaker 脚本，其中少于 80 个与 Web 应用程序是“兼容”的。需要说明的是，FileMaker Pro 显然比 Web 应用程序健壮得多。在下方的 PHP 脚本中，`$request`正在向数据库添加一条记录。它正在使用 `setField` 方法将 Post 请求头（header）中 `FirstName` 的值插入到表的 `FirstName` 字段中。这与将脚本参数值插入到 `FirstName` 字段的 FileMaker Set field 脚本并没有太大区别。如果你熟悉 FileMaker PHP 方法 API，它与理解后面出现的 API 的步骤将非常相似。

```
$request->setField('FirstName', $_POST['FirstName']);
```

对比：

```
Set Field [php::FirstName; Get(ScriptParameter)]
```

PHP 方法与 FileMaker 函数或自定义函数相同。PHP 拥有的方法比 FileMaker 函数多得多。你可以在 php.net 网站找到特定的方法。PHP 的主要优势是处理和解析数据字符串。你的工作是为方法提供来自字段、变量或表单输入的数据。例如，下方的 PHP 方法正在返回由 `$max` 计算的变量 `$found` 的整数值。这与 FileMaker 中的整数函数非常相似。并不是所有的 FileMaker 函数都相似的。不过，在扩展 FileMaker 章节的末尾，我们将尝试提供 FileMaker 方法与 PHP 方法的对比作为参考。

```
int($found / $max)
```

对比：

```
RecordID vs. Serial Number
```

任何用过数据库的人都知道为每条记录的主键使用自动生成的序列号（Serial Number）。事实上，FileMaker 有一个内置功能可以创建开发者定义的序列号。然而，如果你正在使用 ODBC 驱动程序，你肯定需要一个序列号字段。但是，FileMaker PHP API 对你的序列号字段一无所知，也不会对你有帮助。尝试强制使用它将非常困难。相反，FileMaker 在底层创建了一个唯一的 `RecordID`。`RecordID` 也是一个序列号。但是，它不能被修改或删除。这就是为什么 FileMaker PHP API 使用这个 `RecordID` 的原因——它是访问预期记录的绝对可靠的方法。

所以你可能会想，太棒了，我可以轻松从表中获取序列号并使用已有的 `RecordID`。但这其中有一个问题：我强烈建议你将序列号字段更改为自动生成的 `Get(RecordID)` 计算值。这样做有几个很好的理由。事实上，`RecordID` 本质上是 FileMaker Pro 数据库中的一个隐藏功能。因此，如果你想操作它，就无法导出它，也没有特定的脚本步骤来使用它。然而，PHP API 暴露了它，因此你可以使用它并根据 `RecordID` 创建关联记录。其次，如果你结合了 FileMaker 和 PHP 客户端界面，你需要将主键（`RecordID`）链接到关联记录的外键上。为了方便起见，我强烈建议你使用 `RecordID` 作为主键和外键，而不是自动生成的序列号。只有当你需要将记录导入回数据库且新记录与导入记录不同时，RecordID 才会成为问题。这可能会严重影响正确关联记录的显示。

# 使用序列号而不是 RecordID 将让你的生活变得艰难。

| 自动输入 (Auto-Enter) | 验证 (Validation) | 存储 (Storage) | 假名 (Furigana) |
|---|---|---|---|
| 自动将以下数据输入此字段中： | | | |
| 创建日期 (Creation Date) | | | |
| 修改日期 (Modification Date) | | | |
| 序列号 (Serial number) | | 创建时 (On creation) | 提交时 (On commit) |
| 下一个值 (next value) | 1 | 递增1 | |
| 来自上一次访问记录的值 (Value from last visited record) | | | |
| 数据 (Data:): | | | |

| 计算值 (Calculated value) | 指定... (Specify...) |
|---|---|
| 不替换字段现有值（如果有的话） | |
| 查找值 (Looked-up value) | 指定... |

禁止在数据输入期间修改值 (Prohibit modification of value during data entry)

# 图 5-9：主键的自动输入序列号

在 php_demo 的上下文中求此此计算

| 当前表 (php_demo) | 运算符 (Operators) | 视图：按名称查看所有函数 (View: all functions by name) |
|---|---|---|
| FirstName | & | Abs (number) |
| LastName | + | Asc (number) |
| Number | | Count (number) |
| Date | 1 | Atn (number) |
| Timestamp | | Average (field result...) |
| Image | 0 | Case (text) result(text2 resu... |
| Calculation | | Ceiling (number) |
| RecordID | | Char (number) |
| Email | | Choose (text; res0) result1 r... |
| Serial - | | Cast (text; res0) result1 |
| Get(RecordID) | | |

计算结果必须为文本 (Text)

不要在所有引用的字段为空时求值 (Do not evaluate all referenced fields are empty)

# 图 5-10：自动输入 Get(RecordID) 而非自动序列号

# 布局 (Layouts)，而非表访问

对于那些有 ASP 或 JSP 经验的人来说，你们习惯于使用 SQL 从表中检索数据并连接表。我不想扫大家的兴，FileMaker PHP API 不提供这种对数据库的访问。你必须为你的网页创建一个包含你可能需要的各种功能和值列表的特定布局。这种情况下真正的问题在于，单个布局可能会强制暴露额外的字段和记录，这将极大地影响 Web 应用程序的性能。因此，提高性能的唯一方法是创建仅包含网页所需的字段和记录的 PHP 布局。当然，更多的布局意味着更多的管理和文档工作。好消息是 FileMaker 客户端不会访问你的 PHP 布局。因此，你可能不需要创建复杂的用户界面。只需字段和记录就能为你提供操作空间，例如将布局命名为特定的名称如“Contact php”，除非你想破坏 PHP 页面，否则永远不要删除该布局。我还建议你将所有的 PHP 布局组织在一个 FileMaker Pro 文件夹中，以此提醒开发者在更改任何与 PHP 相关的数据库时要极其小心。

对布局、值列表、表和脚本的更改将破坏你的 PHP 页面。如果你更改了数据库，将必须更新你的 PHP 网页。

![](img/5a2c5fda68d42e5d65f51850276e9ec_61_0.png)

图 5-11：仅为 PHP 设计的布局

# 命名规范 (Naming Conventions)

字段的命名规范不仅对 FileMaker Pro 重要，对 PHP 也是如此。网页在特殊字符方面往往脆弱，而 FileMaker 则允许使用它们。标准的 Web 规定你应该使用 a-z、0-9、下划线来命名字段，并且不要使用点、空格或高 ASCII 字符（如 "??"）。字段名应以字母开头，而不是数字或下划线。例如，使用 "FirstName" 而不是 "First Name"。注意我在每个单词的首字母使用了大写字母，以便于阅读字段名。

![](img/5a2c5fda68d42e5d65f51850276e9ec_61_1.png)

> 绝对不要一旦字段在 PHP 网页上使用就更改它。如果你更改了字段名，你将必须更新你的 PHP 网页。

