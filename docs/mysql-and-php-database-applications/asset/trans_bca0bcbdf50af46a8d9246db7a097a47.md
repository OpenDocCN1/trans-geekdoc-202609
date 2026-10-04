

## 336 第四部分：并不简单的应用

`status`（状态表）是一个查找表，包含了问题可能的所有状态；例如“开启”、“已关闭”、“处理中”等。`sources`（来源表）是另一个查找表，记录问题最初记录的地方。如果用户通过 Web 提交投诉，`sources` 表将记录此类；员工收到的投诉可能源于电话、电子邮件或“愤怒的箭”。

`entries_type` 表记录了 `history`（历史表）中的特定项目应该是公开的还是私有的。如果是私有的，当用户访问查看问题时，Web 页面将不会显示，且当有更新时不会向用户发送电子邮件。“公开”更新将是可见的，且用户将收到电子邮件通知。

这个架构中有一个有点奇怪的地方，即 `calls`（调用表）。`calls` 表的目的是存储每个拥有所有者的调用的最新条目。如果你查看它，可能会疑惑为什么这是必须的。毕竟，员工、问题和历史记录之间存在关系。因此，应该有一种方法来连接这三张表以获取你想要的信息。通常，你会使用子查询（sub-selects）来完成此类操作。

```sql
select problem.*, history.*, staff.*
from problem, history, staff
where problem.owner = '$PHP_AUTH_USER'
and history.dt_in 
(select max(n.entry_dt) from history)
```

如果我们使用的是 MySQL 3.23 版本，我们将使用临时表。

```sql
create temporary table calls
select max(entry_dt) from history
```

然后你可以将 `problem` 表和 `history` 表连接到这个临时表上。然而，由于我们在创建这些应用时使用的 3.23 版本不支持该功能，我们不得不手动创建一个临时表。每次访问它时，`calls` 表都会被清空，并重新填充我们完成连接所需的信息。请参考 `staff.php` 页面以查看架构以及我们使用的 SQL 创建语句。

现在，关于在规划你的网站时的几点说明，你可能想要添加一个表或更改一两个列定义。首先，你可能想在 `staff` 表中添加密码列，以便确保查看该网站的人确实应该出现在那里。

注意我们在 `problems` 表中有一个 `problem_code` 列。但是，如果你通过电子邮件发送问题状态，你可能希望比下面的链接透明度低一点：http://yoursite.com/tracking/problems.php?problem_id=7。

如果你回想起第 9 章，我们在遇到类似情况时采取了一些预防措施。我们不希望人们能够仅仅通过猜测 URL 中的变量名来访问我们数据的受限部分。在这里，我们将采用

我们在问卷调查应用程序中使用的相同技术，通过 `md5()` 和 `uniqid()` 函数创建一个随机的 8 字符字母数字字符串。

## 第 13 章：问题跟踪系统

列表 13-1 显示了我们在此应用中使用的表及其创建语句。除了创建语句外，该列表还包含了启动应用所需的某些默认数据。请注意，如果你从 CD-ROM 安装此应用，你将拥有一套完整的可以运行的虚拟数据。

列表 13-1：问题跟踪系统中使用的创建语句

```sql
CREATE TABLE customers (
  customer_id int(11) NOT NULL auto_increment,
  firstname varchar(40),
  lastname varchar(40),
  address varchar(40),
  address2 varchar(40),
  city varchar(20),
  state char(2),
  zip varchar(5),
  ip4 varchar(5),
  email varchar(255),
  day_area char(3),
  day_prefix char(3),
  day_suffix varchar(4),
  day_ext varchar(5),
  day_start varchar(8),
  day_end varchar(8),
  eve_area char(3),
  eve_prefix char(3),
  eve_suffix varchar(4),
  eve_ext varchar(5),
  eve_start varchar(8),
  eve_end varchar(8),
  PRIMARY KEY (customer_id)
);
```

### 表 'entry_types' 的结构

```sql
CREATE TABLE entry_types (
  entry_type_id tinyint(4) NOT NULL auto_increment,
  entry_type varchar(10) NOT NULL,
  PRIMARY KEY (entry_type_id)
);
INSERT INTO entry_types VALUES (1,'private');
INSERT INTO entry_types VALUES (2,'public');
```

### 表 'history' 的结构

```sql
CREATE TABLE history (
  entry_id int(11) NOT NULL auto_increment,
  problem_id char(32) NOT NULL,
  entry_type_id tinyint(4) NOT NULL,
  entered_by varchar(20),
  source_id tinyint(4) NOT NULL,
  entry_dt timestamp(14),
  notes text,
  PRIMARY KEY (entry_id),
  KEY history_problem_id (problem_id)
);
```

### 表 'problems' 的结构

```sql
CREATE TABLE problems (
  problem_id char(32) NOT NULL,
  customer_id int(11) NOT NULL,
  status_id tinyint(4) NOT NULL,
  owner varchar(20),
  summary text,
  problem text,
  entered_by varchar(20),
  source_id tinyint(4) NOT NULL,
  entry_dt datetime,
  modify_dt timestamp(14),
  problem_code char(8) not null,
  PRIMARY KEY (problem_id),
  KEY problem_customer_id (customer_id),
  KEY problem_code_key (problem_code)
);
```

### 表 'sources' 的结构

```sql
CREATE TABLE sources (
  source_id tinyint(4) NOT NULL auto_increment,
  source varchar(10) NOT NULL,
  PRIMARY KEY (source_id)
);
INSERT INTO sources VALUES (1,'web');
INSERT INTO sources VALUES (2,'email');
INSERT INTO sources VALUES (3,'phone');
INSERT INTO sources VALUES (4,'in-store');
INSERT INTO sources VALUES (5,'staff');
INSERT INTO sources VALUES (6,'program');
```

### 表 'staff' 的结构

```sql
CREATE TABLE staff (
  username varchar(20),
  password varchar(255),
  staff_name varchar(50),
  active int(1) DEFAULT 1,
  PRIMARY KEY (username)
);
```

### 表 'status' 的结构

```sql
CREATE TABLE status (
  status_id tinyint(4) NOT NULL auto_increment,
  status varchar(20),
  PRIMARY KEY (status_id)
);
INSERT INTO status VALUES (1,'Opened');
INSERT INTO status VALUES (2,'In Progress');
INSERT INTO status VALUES (3,'Closed');
INSERT INTO status VALUES (4,'Re-opened');
```

### 表 'tracking_admin' 的结构

```sql
CREATE TABLE tracking_admin (
  username varchar(50),
  password varchar(255)
);
```

