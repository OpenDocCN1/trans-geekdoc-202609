
## 图 9-2：基本调查结果

## 调查结果

你最喜欢的州是？
vt 60%
wv 20%
ny 20%
你最喜欢的县是？
San Francisco 100%

## 图 9-3：详细调查结果

你最喜欢的州是？（共 5 票）

**按年龄：**
| 答案 | 未说明 | 16 岁以下 | 17 至 32 | 33 至 48 | 49 至 64 | 65 岁及以上 |
|---|---|---|---|---|---|---|
| vt | 33.3% | | | | 33.3% | 33.3% |
| wv | | | | | | 100% |
| ny | | | | 100% | | |

**按国家/地区：**
| 答案 | Canada | 其他 | USA | USA |
|---|---|---|---|---|
| vt | | | 33.3% | 66.6% |
| wv | | | | 100% |
| ny | | 100% | | |

**按州：**
| 州 | vt | wv | ny |
|---|---|---|---|
| CA | 66.6% | 33.3% | |
| 未说明 | 100% | | |

![](img/de0823012275cf4ceebdb822a56e6b71_248_0.png)

## 当前问题

你最喜欢的县是？
你最喜欢的州是？

## 添加一个问题

问题：

答案：

图 9-4：调查管理页面

![](img/de0823012275cf4ceebdb822a56e6b71_248_1.png)

以 jay 编辑

## 调查管理员：每周随机抽奖

为 2000-05-28 当周抽取获奖者

fred programmer fred@fred.com WINNER! Notify Winner

## 过去几周：
- 2000-05-28
- 2000-06-04
- 2000-07-02
- 2000-10-29
- 2000-11-05

管理页面

图 9-5：选择获奖者页面

获奖者将通过电子邮件收到通知，并会收到一个 URL，他们需要前往该 URL 以认领奖品。该页面看起来与图 9-6 中的页面类似。到达后，他们需要确认自己的身份，以便为你提供额外的安全层。

![](img/de0823012275cf4ceebdb822a56e6b71_249_0.png)

图 9-6：认领奖品页面

## 我们需要防止什么？

在上一章中，我们讨论了人们试图通过表单元素发送垃圾信息的方法。我们将在此处继续使用这些函数。该应用程序还将执行一些电子邮件地址验证。

![](img/de0823012275cf4ceebdb822a56e6b71_249_1.png)

想知道验证电子邮件是否符合正确格式到底需要什么？这需要大量工作。查看 CD 上 /functions 目录中的 CheckEmail.php 文件。你会看到它需要多个正则表达式来确保电子邮件完全正确。鉴于正则表达式执行速度相当慢，你可能会怀疑运行这样的脚本是否值得，尤其是当你运行一个流量非常大的网站时。你需要自己决定。是否需要确保电子邮件完美无缺，还是更简单、健壮性较低的验证形式就足够了？即使你确保地址格式正确，也几乎没有办法知道该地址是否对应一个实际的邮箱。

该应用程序将为你提供一种简单的方法来阻止某些人向你的网站输入信息。它并不十分复杂；一个精明的互联网用户可以在一分钟内绕过它。使用图 9-6 中显示的表单，你可以输入一个将被阻止访问该站点的来源域名。所有输入数据的用户，其 `REMOTE_HOST` 变量都将被与数据库中的表进行检查。如果找到该主机，应用程序将拒绝该用户访问。同样，这并不完美。根据所使用的 ISP，一些客户端甚至不会在 HTTP 头中标识 `REMOTE_HOST`。如果你确实有敏感信息并且需要有效阻止用户的方法，你应该使用某种登录方案。这只是你可以用数据库和 HTTP 头信息做的一个例子。

你还需要采取一些措施，确保错误的人不会认领奖品。你需要确保来认领奖品的人就是他们声称的那个人。

## 设计数据库

此调查应用程序允许任意数量的问题。每个问题可以有任意数量的答案。为了创建这种关系，你需要两个表，一个名为 questions，一个名为 responses，它们之间存在一对多的关系。（每个（1）问题可以有（n）任意数量的答案。）

用户信息最好也用多个表表示。一个名为 users 的表将存储相关的用户信息。两个名为 states 和 countries 的表充当查找表，并与 users 表存在一对多的关系。

最后，还有两个与其他表没有关系的表。它们存储该应用程序需要跟踪的其他信息。它们恰当地命名为 blocked_domains 和 survey_admin。

图 9-7 显示了数据库结构的视觉表示。创建这些表的 `create` 语句显示在列表 9-1 中。请注意，这些表定义是从 `mysqldump` 实用程序复制的。如果你不熟悉 `mysqldump` 或其他 `mysql` 实用程序，请务必查阅附录 C。

![](img/de0823012275cf4ceebdb822a56e6b71_251_0.png)

## 图 9-7：调查数据库架构

## 列表 9-1：调查的创建语句

```sql
# Table structure for table 'age_ranges'
#
CREATE TABLE age_ranges (
    min_age int(11) NOT NULL,
    max_age int(11) NOT NULL,
    age_range varchar(10)
);
```

```sql
# ----------------------------------------
#
# Table structure for table 'answers'
#
CREATE TABLE answers (
    answer_id int(11) NOT NULL auto_increment,
    question_id int(11),
    answer text,
    PRIMARY KEY (answer_id)
);
```

```sql
# ----------------------------------------
#
# Table structure for table 'blocked_domains'
#
CREATE TABLE blocked_domains (
    domain varchar(30) NOT NULL,
    block_by varchar(10) NOT NULL,
    block_dt datetime DEFAULT '0000-00-00 00:00:00' NOT NULL,
    release_dt datetime,
    notes text,
    modify_dt timestamp(14)
);
```

```sql
# ----------------------------------------
#
# Table structure for table 'countries'
#
CREATE TABLE countries (
    country varchar(30) NOT NULL
);
```

```sql
# ----------------------------------------
#
# Table structure for table 'questions'
#
CREATE TABLE questions (
    question_id int(11) NOT NULL auto_increment,
    question text NOT NULL,
    KEY question_key (question_id)
);
```

```sql
# ----------------------------------------
#
# Table structure for table 'responses'
#
CREATE TABLE responses (
    user_id int(11) NOT NULL,
    answer_id int(11) NOT NULL
);
```

```sql
# ------------------------------------------------------------
#
# Table structure for table 'states'
#
CREATE TABLE states (
    statename varchar(30) NOT NULL,
    state char(2) NOT NULL
);

# ------------------------------------------------------------
#
# Table structure for table 'survey_admin'
#
CREATE TABLE survey_admin (
    username varchar(50) NOT NULL,
    password varchar(255) NOT NULL
);

# ------------------------------------------------------------
#
# Table structure for table 'users'
#
CREATE TABLE users (
    user_id int(11) NOT NULL auto_increment,
    name varchar(50),
    email varchar(50),
    country varchar(20),
    state char(2),
    age int(11),
    remote_addr varchar(15),
    remote_host varchar(80),
    create_dt timestamp(14),
    KEY user_key (user_id)
);

# ------------------------------------------------------------
#
# Table structure for table 'winners'
#
```

```sql
CREATE TABLE winners (
    user_id int(11) NOT NULL,
    weekdate datetime DEFAULT '0000-00-00 00:00:00' NOT NULL,
    notify_dt datetime,
    claim_dt datetime,
    confirm_dt datetime
);
```

## 代码概述

如果你已经阅读了第 8 章中同名的部分，我们在此使用的结构应该对你来说很熟悉。/functions 文件夹中的项目已包含并可重复使用。

很明显，这个调查应用程序需要的页面比留言簿多得多：需要做的事情更多。虽然你可以在单个页面中包含多个操作，并通过传递变量和使用 if 语句来筛选所需的操作，但这会使代码难以跟踪。最好有几个直观命名的文件来执行特定任务。话虽如此，该应用程序中的某些页面会使用变量来决定在给定页面上采取什么操作。

如果你做过任何 Web 工作，你就知道处理 HTML 表格和表单是多么乏味。因此，在本章和本书的大多数其他应用程序中，我们将尝试减轻处理表格和表单带来的痛苦。在以下各节中，你将看到几个函数，它们至少在长期来看会让生活变得轻松得多。接下来的各节中的函数如果先看到它们实现的功能会更容易理解。这里有一些代码，如果与以下函数一起使用，将能很好地工作。

```
print start_table();
print table_row(
    table_cell("Cell text")
);
print end_table();
```

![](img/de0823012275cf4ceebdb822a56e6b71_254_0.png)

> 如果你不喜欢我们为表格、表单和其他 HTML 元素创建的函数，就不要使用它们。手动输入 HTML 元素而不是通过函数创建是完全可以接受的（也许甚至更常见）。就像编程中的许多事情一样，这归结为个人偏好。在这种情况下没有正确答案：按你喜欢的方式做。

这将创建一个包含一个单元格的表格。你可以通过在 table_row 函数调用中添加额外的 table_cell() 调用在此基础上增加复杂性。你
