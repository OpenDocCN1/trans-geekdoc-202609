

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_123_0.png)

图 3-9：使用 sum() 会很有帮助的表格

要获取每个州的总计，你需要运行以下查询：

```
select state, sum(contribution) from contributions group by state;
```

### min()

min() 函数会提取每个分组中的最低值。要找出任何州的最低贡献，只需对上一查询做一点小改动：

```
select state, min(contribution) from contributions group by state;
```

### max()

如你可能猜到的，max() 将返回分组中的最高值：

```
select state, max(contribution) from contributions group by state;
```

### avg()

avg() 返回分组的平均值：

```
select state, avg(contribution) from contributions group by state;
```

你可以将所有这些组合起来，创建一个非常有用的查询，如图 3-10 和以下查询所示：

```
select state, sum(contribution) as 'Total',
avg(contribution) as 'Average',
min(contribution) as 'Minimum',
max(contribution) as 'Maximum'
from contributions
group by state;
```

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_124_0.png)

图 3-10：共同使用多个聚合函数

## group by 选项

大多数关系数据库要求 select 子句中列出的字段必须用在 group by 谓词中。但 MySQL 提供了第二个选项：你可以对列出的列的子集进行分组。例如，如果你想统计一个城市中的人数，并查看该城市的一个示例邮政编码，可以运行以下查询：

```
select city, zip, count(*) from users group by city;
```

该查询将返回城市列表、每个城市的条目数以及一个示例邮政编码。这些结果与以下查询的结果截然不同：

```
select city, zip, count(*) from users group by city, zip;
```

这将为每个城市/邮政编码组合返回单独一行，并为每个唯一组合提供计数。

### having

having 谓词限制 group by 显示的行。这个谓词与 where 子句不同。where 子句实际上限制了用于 group by 的行，而 having 子句仅阻止它们的显示。

如果你需要找出所有捐款超过 100 美元的人按州计算的平均捐款金额，可以运行以下查询：

```
select avg(donations), state from contributions where donations > 100;
```

但是，如果你想显示平均捐款超过 100 美元的所有州的平均捐款，则必须使用 having 子句。因为 having 子句不限制进入 group by 的行，所以像本例中的 avg() 这样的聚合函数会在其计算中使用所有行。

```
select avg(contribution) as avg_contrib, state
from contributions
group by state
having avg(contribution) > 100;
```

## 连接表

如果你读过第 1 章，你就会知道关系数据库之所以工作如此出色，是因为它们对信息进行分段。不同的表保存不同主题的信息，字段被插入到表中以维持关系。在完成规范化过程后，你的表很可能没有其他表就无法单独使用。这就是为什么你需要在 SQL select 语句中连接表。

### 两表连接（等值连接）

为保持连续性，我们将重新介绍在第 1 章中首次出现的几个表。请看图 3-11 中熟悉的表格。

如果你想向 contacts 表中所有人进行邮件寄送，你需要将 contacts 表与 companies 表连接，因为街道地址在 companies 表中（这正是它应该在的地方）。contacts 表中的 company_id 列在建立这些表之间的关系。如果你在这些表的 company_id 字段相等时连接它们，所有信息都将触手可及。

| 公司 ID | 公司名称 | 地址 |
|---|---|---|
| 1 | Big Co Company | 1121 43rd St |
| 2 | Little Co Company | 4444 44th St |

| 联系人 ID | 公司 ID | 姓名 | 职位 | 电话 | 电子邮件 |
|---|---|---|---|---|---|
| 1 | 1 | Jay Greenspan | 副总裁 | 4155551212 | 1121 43rd St |
| 2 | 1 | Brad Bulber | 总裁 | 4155552222 | 4444 44th St |
| 3 | 2 | John Doe | Lacky | 2125556666 | 4444 44th St |

图 3-11：需要连接的表格

在 SQL 中进行此连接非常简单。所有要连接的表都必须在 select 语句的 from 部分中列出。并且，进行连接的字段必须在 where 部分中列出：

```
select *
from companies, contacts
where companies.company_id = contacts.company_id;
```

当对字段名的引用具有歧义时，你需要使用 table_name.column_name 语法指定列来自哪个表。你可以在图 3-12 的 where 子句中这样做。如果在 SQL 语句中未指明列来自哪个表，MySQL 将返回错误。

这种基于公共字段相等性来合并表的连接类型极其常见。它被称为等值连接或内连接。当你在本章后面学习外连接时，“内连接”这个名称会更容易理解。

一旦你开始执行连接，别名就会变得很方便。通过在 from 子句中指定别名，可以节省一些输入。在以下代码中，t1 是 companies 的别名，t2 是 contacts 的别名。

```
select *
from companies t1, contacts t2
where t1.company_id = t2.company_id;
```

### 多表连接

等值连接可以应用于多个表。你的许多 SQL 语句将连接三个、四个或更多表。你只需要在 select 之后添加额外的列，在 from 子句中添加额外的表，并在 where 子句中添加额外的连接参数。请看图 3-13 中需要多表连接的表格。

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_127_0.png)

图 3-12：基本连接

如果你想查找在加利福尼亚州设有办事处且擅长咨询的所有公司的地址，你需要连接所有这四个表。以下查询可以完成任务。在这里，where 子句包含相当多的测试：where 子句的前两行将返回的行限制为符合你标准的公司。where 子句的其余部分处理连接。

```
select *
from companies, locations, expertise, companies_expertise
where state = 'CA' and
companies_expertise.expertise_id = 3 and
companies.company_id = companies_expertise.company_id and
companies.company_id = locations.company_id and
companies_expertise.expertise_id = expertise.expertise_id
```

### 外连接

空值带来的挑战在这本书中反复出现。在第 2 章中，我们介绍了表 2-1 和表 2-2，在此作为表 3-13 和表 3-14 重新呈现。

| 公司 ID | 名称 |
|---|---|
| 1 | IBM |
| 2 | Xerox |
| 3 | Sun |

| 专长 ID | 领域 |
|---|---|
| 1 | 硬件 |
| 2 | 软件 |
| 3 | 咨询 |

| 公司 ID | 专长 ID |
|---|---|
| 1 | 1 |
| 1 | 2 |
| 1 | 3 |
| 2 | 1 |
| 2 | 3 |
| 3 | 1 |
| 3 | 2 |

| 位置 ID | 公司 ID | 地址 | 州 |
|---|---|---|---|
| 1 | 1 | 4 My Way, Durham | NC |
| 2 | 2 | 44 Circle Dr, New York | NY |
| 3 | 1 | 1 Front St, San Francisco | CA |
| 4 | 2 | Park Dr, Palo Alto | CA |
| 5 | 2 | 48 Times Square, New York | NY |
| 6 | 3 | 280 South, Sunnyvale | CA |

图 3-13：需要多表连接的表格

表 3-13 联系人表

| 名 | 姓 | 幻想配偶 ID |
|---|---|---|
| Jay | Greenspan | 1 |
| Brad | Bulger | NULL |

表 3-14 desired_spouse

| 幻想配偶 ID | 名 | 姓 |
|---|---|---|
| 1 | Nicole | Kidman |

