
[content]

# 第 12 章 努力不弄乱：数据收集与存储

这是一种处理任何内容的方法。其良好之处在于，你通常不需要担心细节，因为你有程序可以正确地读写 CSV 文件。如果一个心怀不轨或粗心的人给给你一个没有妥善处理这些特定字符的 CSV 文件，识别起来可能很困难，但并非不可不可。

Excel 可以毫无困难地打开 CSV 文件，你通常可以安全地编辑并保存它们（假设行数没有超过一百行）。然而，CSV 仅仅是文本，因此它不会保存你在 Excel 中添加的任何格式，例如粗体列表头。如果你用 Excel 打开图 12-7 所示书籍数据的 CSV 版本，它看起来将是一样的，没有粗体表头，也没有不同大小的列。如果你想亲眼看到 CSV 的真实面，可以在文本编辑器中打开它。书中的版本看起来就像图 12-8 所示。空值会被完全省略，因此你会看到一连串在一起的逗号，就像图 12-8 中所示的大多数记录的末尾；大多数书籍并没有多个作者。

| | 标题 | 副标题 | 姓名编号 | 出版日期 | ISBN | 出版社 | 贡献者 | 贡献者1 | 贡献者2 | 贡献者3 | 贡献者4 | 主要贡献者 |
|--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 10 | 标题 | 副标题 | 姓名编号 | 出版日期 | ISBN | 出版社 | 贡献者 | 贡献者1 | 贡献者2 | 贡献者3 | 贡献者4 | 主要贡献者 |
| 11 | 我们的小笔记本 | ... | little, a | Breeze Smyth | 作者 | | | | | | | |
| 12 | 我们的小笔记本 | ... | little, a | Breeze Smyth | 著者... | 1996 | 780572365323 | The Free Press | George Stark, Jr., Thomas M. Weat, Author | | | | |
| 13 | 原子的世界 | ... | | 1998 | 7805123456 | Academic House | Neil Grah, Author... | | | | | |
| 14 | 原子的世界 | ... | | 2001 | 7805120000 | Academic House | James Brown, Michael Nelson, Author... | | | | | |
| 15 | 原子的世界 | ... | | 2003 | 7805120000 | Penguin Group Publishing | Peter Group, Author, Sharon Messenger, Editor | | | | | |
| 16 | 运营数据科学 | ... | | 2004 | 7805128888 | Academic Press | Patricia Cress, Author... | | | | | |
| 17 | 运营数据科学 | ... | | 2006 | 7805128899 | Academic Press | James Gordon, Author... | | | | | |
| 18 | 小切尼的 A 三书 | ... | | 2007 | 7805129999 | Penguin Group Publishing | Peter Group, Author... | | | | | |
| 19 | 小切尼的 A 三书 | ... | | 2008 | 7805120000 | Academic House | Sarah White, Author... | | | | | |
| 20 | 商业经济 | ... | | 2009 | 7805121111 | Academic Press | Paul Muller, Author... | | | | | |
| 21 | 商业经济 | ... | | 2010 | 7805122222 | Penguin Group Publishing | Peter Group, Author... | | | | | |
| 22 | 最后的危机生活 | ... | | 2011 | 7805123333 | Academic Press | John Smith, Author, Michael Schank, Author... | | | | | |
| 23 | 最后的危机生活 | ... | | 2012 | 7805124444 | Academic House | James Gordon, Author... | | | | | |
| 24 | 最后的危机生活 | ... | | 2013 | 7805125555 | Academic Press | Sarah White, Author... | | | | | |
| 25 | 讲述之谜 | ... | | 2014 | 7805126666 | Academic House | James Brown, Author... | | | | | |
| 26 | 讲述之谜 | ... | | 2015 | 7805127777 | Academic Press | Michael Nelson, Author... | | | | | |
| 27 | 为你推荐 | ... | | 2016 | 7805128888 | Academic House | James Gordon, Author... | | | | | |
| 28 | 为你推荐 | ... | | 2017 | 7805129999 | Academic House | Brandon Sanderson, Steve Argyle, Illustrator... | | | | | |

## 图 12-8：在文本编辑器中查看书籍 CSV 文件

# 序列化文件和其他文件格式

还有其他存储方式，但在 Python 中配合 Pandas 和 R 使用它们，只需使用为读取此类文件而构建的正确库，然后只需要一两行代码。有时数据或其他对象在 Python 中被存储和写入为 `pickle`。任何内容都可以以这种方式保存，保存机器学习模型时也很常见。

另一种在云平台上变得越来越流行的格式是 `parquet`，它是保存大量数据的好方法，因为它可以跨多个文件拆分。Parquet 文件与拆分耗时操作的工具配合良好，可以并行执行部分（这被称为分布式计算，在处理具有大量数据的云工具时很常见）。

存储数据的更多文件类型在不断出现，因此跟进动态是很好的。

# 数据库

数据库系统是几乎所有数据科学家工作的日常部分。从许多原因来说，数据库通常比电子表格和文本文件更好，包括从存储管理的角度，以及因为易于操作。数据库管理系统是处理数据库中所有信息存储的软件。用户通过几种方式交互，通常通过由数据库托管的界面进行编写和运行。数据科学家也使用此界面，但很多时候，他们通过其他环境中的 Python 或 R 代码与系统进行交互。

在技术领域，“数据库”一词本身指的是可以通过数据库管理系统访问的相关数据的集合。你经常会看到系统本身被简写为 DBMS（数据库管理系统），它可以是任何类型的数据库。大多数 DBMS 在高层将内容组织成它们所谓的“数据库”，这是一个对象，其中可以包含其他对象，如表或其他层次级对象。作为一个典型的例子，Oracle DBMS 拥有的可以包含许多模式（schemas），模式内部包含表和对象对象。在这种意义上，模式仅仅是一个组织对象（例如，在模式级别授予的权限将适用于其内部的所有对象）。在 Oracle 的设置中，引用特定的表需要数据库名、模式名和表名本身。

# 模式 (SCHEMA)

“模式”一词在数据库世界中也以不同的方式使用，指的是数据库的整体结构，通常意味着它的视觉表示。在大多数情况下，它将包含表名、列以及表之间的关系。图 12-9 显示了我们将在下文“关系数据库系统”部分查看的表的模式。

| | 专业 | |
|---|---|---|
| key | MAJOR_ID | integer |
| | MAJOR_NAME | string |

| | 学生专业 | |
|---|---|---
| key | STUDENT_ID | integer |
| | STUDENT_FIRST_NAME | string |
| | STUDENT_MIDDLE_NAME | string |
| | STUDENT_LAST_NAME | string |
| | MAJOR_ID | integer |
| | ADVISOR_ID | integer |
| | SCHOOL_ID | integer |

| | 导师 | |
|---|---|---|
| key | ADVISOR_ID | integer |
| | ADVISOR_NAME | string |

| | 学校 | |
|---|---|---|
| key | SCHOOL_ID | integer |
| | SCHOOL_NAME | string |

> 图 12-9：一个微型数据库的示例简化模式

[/content]
