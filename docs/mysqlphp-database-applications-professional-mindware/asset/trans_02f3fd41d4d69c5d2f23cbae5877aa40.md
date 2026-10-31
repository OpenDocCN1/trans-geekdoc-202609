
### 表 1-1 用于数据存储的简单表

| 姓名 | 地址1 | 地址2 | 城市 | 州 | 邮编 | 电话 | 电子邮件 |
|---|---|---|---|---|---|---|---|
| Jay Greenspan | 211 Some St | Apt 2 | San Francisco | CA | 94107 | 4155551212 | jgreen_1@yahoo.com |
| Brad Bulger | 411 Some St | Apt 6 | San Francisco | CA | 94109 | 4155552222 | bbulger@yahoo.com |
| John Doe | 444 Madison Ave |  | New York | NY | 11234 | 2125556666 | nobody@hotmail.com |

### 表 1-2 有问题的表存储

| id | 公司名称 | 公司地址 | 联系人姓名 | 联系人职位 | 电话 | 电子邮件 |
|---|---|---|---|---|---|---|
| 1 | BigCo Company | 1121 43rd St | Jay Greenspan | Vice President | 4155551212 | jgreen_1@yahoo.com |
| 2 | BigCo Company | 1121 43rd St | Brad Bulger | President | 4155552222 | bbulger@yahoo.com |
| 3 | LittleCo Company | 4444 44th St | John Doe | Lackey | 2125556666 | nobody@hotmail.com |

### 表 1-3 公司

| 公司编号 | 公司名称 | 公司地址 |
|---|---|---|
| 1 | BigCo Company | 1121 43rd St |
| 2 | LittleCo Company | 4444 44th St |

### 表 1-4 联系人

| 联系人编号 | 公司编号 | 联系人姓名 | 联系人职位 | 电话 | 电子邮件 |
|---|---|---|---|---|---|
| 1 | 1 | Jay Greenspan | Vice President | 4155551212 | jgreen_1@yahoo.com |
| 2 | 1 | Brad Bulger | President | 4155552222 | bbulger@yahoo.com |
| 3 | 2 | John Doe | Lackey | 2125556666 | nobody@hotmail.com |

现在与 BigCo Co. 相关的信息已放在它自己的表中，名为 Companies。如果查看下一张表（表 1-4），名为 Contacts，你会看到我们插入了另一列，称为 company_id。该列引用 Company 表的 company_id 列。在 Brad 的行中，我们看到 company_id（第二列）等于 1。然后我们可以转到 Companies 表，查看 company_id 为 1 的信息并看到所有相关的地址信息。这里发生的事情是我们在这两个表之间创建了一个关系——因此得名 *relational database*。

我们仍然拥有之前设置中的所有信息，只是将其分段了。在此设置中，我们只需更改单行即可更改 Jay 和 Brad 的地址。这正是我们想要的便利。

也许这会让你好奇我们如何将这些信息重新合并。关系数据库使我们能够合并或连接表。考虑以下语句，其目的是为我们提供 Brad 的所有可用信息：“Give me all the columns from the contacts table where contact_id is equal to 1, and while you're at it throw in all the columns from the Companies table where the company_id field equals the value shown in Brad's company_id column.” 换句话说，在此语句中，你要求在 company_id 字段相同的地方连接这两个表。此请求或查询的结果看起来会像表 1-5。

在几页的篇幅中，你已经学会了通过分段信息并创建额外的表来解决数据完整性问题。但我尚未为此问题命名。当我从一本非常厚且昂贵的书中学习与关系数据库相关的词汇时，这种问题被称为 *update anomaly*。现实世界中可能有人使用这个术语，也可能没有；如果有，我还没遇到过。然而，我认为这个术语非常贴切。在本节前面展示的表中，如果我们更新表中的一行，包含相同信息的其他行将不会受到影响。

## 删除异常

现在查看表 1-6，重点关注第 3 行。考虑如果 Mr. Doe 从数据库中被删除会发生什么。这看起来像是简单的更改，但假设有人访问数据库想要一份过去一年联系过的公司列表。在当前设置中，当我们删除第 3 行时，我们不仅删除了 John Doe 的信息，还删除了公司的信息。这个问题被称为 *deletion anomaly*。

如果公司信息被移到它自己的表中，如我们在上一节所见，这就不会成为问题。我们可以删除 Mr. Doe，然后独立决定是否要删除他关联的公司。

### 表 1-5 查询结果

| 公司编号 | 公司名称 | 公司地址 | 联系人编号 | 联系人姓名 | 联系人职位 | 电话 | 电子邮件 |
|---|---|---|---|---|---|---|---|
| 1 | BigCo Company | 1121 43rd St | 2 | Brad Bulger | President | 4155552222 | bbulger@yahoo.com |

### 表 1-6 存在删除异常的表

| 公司编号 | 公司名称 | 公司地址 | 联系人姓名 | 联系人职位 | 电话 | 电子邮件 |
|---|---|---|---|---|---|---|
| 1 | BigCo Company | 1121 43rd St | Jay Greenspan | Vice President | 4155551212 | jgreen_1@yahoo.com |
| 2 | BigCo Company | 1121 43rd St | Brad Bulger | President | 4155552222 | bbulger@yahoo.com |
| 3 | LittleCo Company | 4444 44th St | John Doe | Lackey | 2125556666 | nobody@hotmail.com |

## 插入异常

我们最后关注的领域是在插入过程中引入的问题。再次查看表 1-6，我们看到此表的目的是存储联系人信息，而不是公司信息。如果想添加公司但不添加个人，这就会变得很麻烦。在大多数情况下，你必须等待有具体的联系人要添加到数据中后，才能将公司信息添加到数据库中。这是一个荒谬的限制。

## 规范化

现在我们向你展示了你可能遇到的一些问题，你需要学习寻找和消除这些异常的方法。此过程称为规范化。理解规范化对于使用关系数据库至关重要。但对于有数据库经验的人来说，规范化并不是数据设计的全部。经验和直觉在创建良好的数据库中也起着作用。在本书后面呈现的示例中，数据在很大程度上会被规范化——但也会有不规范结构更可取的情况。

还有一个快速的提醒。规范化过程包含几个“normal forms。”在本章中我们将介绍 1st、2nd、和 3rd normal forms。在此之外，规范化过程还可以通过另外四种范式继续。（对于好奇的人来说，它们被称为 Boyce-Codd normal form、4th normal form、5th normal form、和 Domain/Key normal form）。我之所以知道这些是因为我在书中读到过。在现实世界中，真正开发数据库应用程序的人们根本不会谈论这些范式。如果你的数据达到 3rd normal form 就足够好了。是的，第三范式中可能仍然存在异常，但如果你能做到这一步应该没问题。

## 第一范式

将数据放入 1st normal form 相对容易。数据需要在表结构中并满足以下标准：

- 每列必须包含一个“atomic”值。这意味着每个单元格只有一个值。任何单元格中都不会存在数组或其他表示多个值的方式。
- 每列必须有唯一名称。
- 表必须有一组值唯一标识行（这称为表的 primary key）。
- 任意两行不能相同。
- 不允许重复的数据组。

### 表 1-7 存在重复数据组的表

| 公司编号 | 公司名称 | 公司地址 | 联系人姓名 | 联系人职位 | 电话 | 电子邮件 |
|---|---|---|---|---|---|---|
| 1 | BigCo Company | 1121 43rd St | Jay Greenspan | Vice President | 4155551212 | jgreen_1@yahoo.com |
| 2 | BigCo Company | 1121 43rd St | Brad Bulger | President | 4155552222 | bbulger@yahoo.com |
| 3 | LittleCo Company | 4444 44th St | John Doe | Lackey | 2125556666 | nobody@hotmail.com |

这里的最后一项是唯一可能需要一些解释的。查看表 1-7：

正如我们已经看到的，第 1 行和第 2 行包含两列具有相同的信息。这是一个重复的数据组。只有当我们删除这些列并将它们放在自己的表中时，这些数据才是 first normal form。我们在表 1-3 和表 1-4 中做的表分离将使这些数据进入 1st normal form。

在我们继续讨论 2nd 和 3rd normal form 之前，你需要几个快速定义。第一个是 primary key。主键是一列或一组列，可通过它唯一标识每一行。在迄今为止展示的表中，我包含了一列顺序值，并且随着行添加到这些表中，数据库引擎会自动插入一个大于该列最大值 1 的整数。这是一种确保每行都有唯一字段的简便方法。世界上每个数据库都有定义此类列的方法。在 MySQL 中它称为 auto_increment 字段。根据你的数据，有各种各样的值可用于主键。社会安全号码效果很好，电子邮件地址和 URL 也不错。数据只需要唯一。在某些情况下，两个或多个列可能构成你的主键。例如，继续以我们的地址簿示例为例，如果需要为拥有多个地点的公司存储联系信息，最好将总机号码和邮寄地址信息存储在一个以 company_id 和公司城市作为主键的表中。

接下来，我们需要定义 dependency 这个词，其含义基本就是你想到的。依赖列是与主键不可分割地联系在一起的列。如果删除主键，它就不能存在于表中。

有了这些基础，我们就可以开始处理 2nd normal form 了。

## 第二范式

此过程的这一部分仅在你最终得到我刚才讨论的多列主键时才适用。假设在划分地址表的过程中我们得到了表 1-8。这里，company_name 和 company_location 构成了多列主键。

### 表 1-8 不在第二范式的表

| 公司名称 | 公司地点 | 公司 CEO | 公司地址 |
|---|---|---|---|
| BigCo Company | San Francisco | Bill Hurt | 1121 43rd St |
| LittleCo Company | LA | LittleCo Company | 4444 44th st |

你应该能很快看出，如果我们为 BigCo Co. 添加另一个地点，插入异常就会出现。我们会在额外的行中重复 CEO 姓名 Bill Hurt，这是不好的。
