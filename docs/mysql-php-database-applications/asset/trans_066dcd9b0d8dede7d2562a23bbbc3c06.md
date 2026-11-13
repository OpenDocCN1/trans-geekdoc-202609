
在数据库中，例如本示例中 answers 和 questions 表之间的关系。外键表的一个好处是约束定义中的 ON DELETE 部分。如果将此设置为 ON DELETE CASCADE，删除主表中的一条记录将自动导致子表中所有依赖记录也被删除。因此，如果删除一个问题，其所有答案也会随之删除。这意味着需要编写的代码更少（这总是件好事）。

图 9-7 展示了数据库结构的可视化表示。创建这些表的 create 语句在清单 9-1 中显示。请注意，这些表定义是从 mysqldump 实用程序复制的。如果您不了解 mysqldump 或其他 mysql 实用程序，请务必阅读附录 D。

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_312_0.png)

图 9-7：调查数据库架构

## 清单 9-1：调查的创建语句

```sql
--
-- Table structure for table 'admin'
--

CREATE TABLE admin (
username varchar(50) NOT NULL default '',
password varchar(255) NOT NULL default '',
PRIMARY KEY  (username)
) TYPE=InnoDB;

--
-- Table structure for table 'age_ranges'
--

CREATE TABLE age_ranges (
min_age int(11) NOT NULL default '0',
max_age int(11) NOT NULL default '0',
age_range varchar(10) default NULL,
PRIMARY KEY  (min_age,max_age)
) TYPE=InnoDB;

--
-- Table structure for table 'answers'
--

CREATE TABLE answers (
answer_id int(11) NOT NULL auto_increment,
question_id int(11) NOT NULL default '0',
answer text NOT NULL,
PRIMARY KEY  (answer_id),
KEY question_id (question_id,answer_id),
FOREIGN KEY (`question_id`) REFERENCES `survey.questions` (`question_id`) ON DELETE CASCADE
) TYPE=InnoDB;

--
-- Table structure for table 'blocked_domains'
--

CREATE TABLE blocked_domains (
domain varchar(64) NOT NULL default '',
block_by varchar(50) default NULL,
block_dt datetime NOT NULL default '0000-00-00 00:00:00',
release_dt datetime default NULL,
notes text,
modify_dt timestamp(14) NOT NULL,
PRIMARY KEY (domain),
KEY block_by (block_by),
FOREIGN KEY (`block_by`) REFERENCES `survey.admin` (`username`) ON DELETE SET NULL
) TYPE=InnoDB;

--
-- Table structure for table 'questions'
--

CREATE TABLE questions (
question_id int(11) NOT NULL auto_increment,
question text NOT NULL,
PRIMARY KEY (question_id)
) TYPE=InnoDB;

--
-- Table structure for table 'responses'
--

CREATE TABLE responses (
user_id int(11) NOT NULL default '0',
answer_id int(11) NOT NULL default '0',
PRIMARY KEY (user_id,answer_id),
KEY answer_id (answer_id),
FOREIGN KEY (`user_id`) REFERENCES `survey.users` (`user_id`) ON DELETE CASCADE,
FOREIGN KEY (`answer_id`) REFERENCES `survey.answers` (`answer_id`) ON DELETE CASCADE
) TYPE=InnoDB;

--
-- Table structure for table 'states'
--

CREATE TABLE states (
state char(2) NOT NULL default '',
statename varchar(30) NOT NULL default '',
PRIMARY KEY (state)
) TYPE=InnoDB;
```

## 清单 9-1（续）

```sql
--
-- Table structure for table 'users'
--

CREATE TABLE users (
 user_id int(11) NOT NULL auto_increment,
 name varchar(50) default NULL,
 email varchar(50) default NULL,
 country varchar(20) default NULL,
 state char(2) default NULL,
 age int(11) default NULL,
 remote_addr varchar(15) default NULL,
 remote_host varchar(80) default NULL,
 create_dt timestamp(14) NOT NULL,
 PRIMARY KEY  (user_id)
) TYPE=InnoDB;
```

```sql
--
-- Table structure for table 'winners'
--

CREATE TABLE winners (
 weekdate datetime NOT NULL default '0000-00-00 00:00:00',
 user_id int(11) NOT NULL default '0',
 claim_code char(8) NOT NULL default '',
 notify_dt datetime default NULL,
 claim_dt datetime default NULL,
 confirm_dt datetime default NULL,
 PRIMARY KEY  (weekdate),
 UNIQUE KEY claim_code (claim_code),
 KEY user_id (user_id),
 FOREIGN KEY (`user_id`) REFERENCES `survey.users` (`user_id`) ON DELETE CASCADE
) TYPE=InnoDB;
```

## 代码概览

如果您已经阅读过第 8 章中同名章节，那么这里使用的结构应该对您很熟悉。/functions 文件夹中的项目已包含并可重复使用。我们还采用了用于留言本的 MySQL 函数，稍作修改使其更加通用，并将其重命名为 my_connect() 和 my_query()。这些可以在 /functions/basic 目录中找到。

显然，此调查应用程序所需的页面比留言本多得多：需要做更多工作。虽然您可以在单个页面中包含多个操作，并通过传递变量和使用 `if` 语句来筛选所需的操作，但这会使代码难以跟踪。最好有几个命名直观、执行特定任务的文件。话虽如此，此应用程序中的一些页面使用变量来决定其外观和行为。

如果您做过任何 Web 开发工作，您就知道处理 HTML 表格和表单有多么乏味。一方面，将原始 HTML 标签放入页面总是比任何基于代码的生成方法都要快。另一方面，通过所有这些原始标签传播更改可能不仅仅是乏味，而且也是 bug 的主要来源。出于这个原因，在本书中的这个以及大多数其他应用程序中，我们将努力减轻处理表格和表单所带来的痛苦。在以下部分中，您将看到几个函数，从长远来看，它们会让生活轻松很多。如果您先了解这些函数能完成什么，接下来部分中的函数将更有意义。以下是一些代码，如果与下面的函数一起使用，效果很好：

```
print start_table();
print table_row(
    table_cell('Cell text')
);
print end_table();
```

或者甚至只需这样：

```
print table('Cell text');
```

这将创建一个只有一个单元格的表格。您可以通过在 `table_row()` 函数调用中添加更多 `table_cell()` 调用，在单单元格表格的基础上增加复杂性。您可以这样做是因为 PHP 能够处理可变数量的参数。我们设计 `table_row()` 函数是为了遍历所有参数（其中一些是对 `table_cell()` 函数的调用）。您可能想知道这些函数如何处理表格属性，例如 `width`、`align` 和其他属性。您如何为特定表格（或一次性为所有表格）更改这些属性？

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_316_0.png)

> 如果您不喜欢我们为表格、表单和其他 HTML 元素创建的函数，请勿使用它们。直接输入 HTML 元素而不是通过函数创建它们是完全可以接受的（也许更常见）。如同编程中的许多事情一样，这最终取决于个人偏好。对于是硬编码 HTML 还是以编程方式生成 HTML 的问题，没有正确答案。但是，在高流量网站上动态生成 HTML 确实会给服务器带来很大负担。在这种情况下，您可能希望在页面中放入原始 HTML — 至少在生产页面中 — 或者研究某种缓存系统。

这里又涉及另一个样式问题。您可以编写函数，要求以特定顺序将某些属性作为参数，如下所示：

```php
function table_cell ($value='', $align='left', $valign='top', $width='')
```

这很简单，调用函数也很简单：

```php
print table_cell('This will be in the upper left corner');
print table_cell('This will end up in the lower right corner',
'right', 'bottom');
```

但缺点是您必须记住哪个属性放在哪里。六个月后再次阅读这样的代码，特别是当您忘记自己写过它或根本没有写过它时，可能会出问题。对于上面的 table_cell() 函数这样的例子，这还不算太糟——“right”和“bottom”足够清晰。但像下面这样的代码行

```php
print image_tag('/images/b129.gif', 10, 20, 5, 1, 0);
```

就不那么清晰。作为一种替代方案，您可以在数组中以命名值的形式指定参数：

```php
print image_tag(array('src'=>'/images/b129.gif', 'width'=>10,
'height'=>20,
'vspace'=>5, 'hspace'=>1, 'border'=>0
));
```

这使得函数调用更易读，但代价是函数本身稍微不那么易读：

```php
function image_tag ($attributes=NULL)
```

现在，确定传递给函数的值是什么的工作是在函数内部完成的。尽管如此，这将工作集中在一个地方。函数调用编写起来稍微麻烦一些，函数本身也更棘手一些。好处是代码更易读、更易维护，编写时也更少歧义；这意味着更少的 bug。（除非您像我们有些人一样容易忘记括号。）
