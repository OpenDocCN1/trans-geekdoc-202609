

## 第 3 章

然后：

```
$connect = mysql_connect("localhost", "root", "mysqlpass");
```

在大多数情况下，你的具体需求以及你设计表格的方式决定了你所使用的代码。出于安全考虑，大多数人使用第一种方法，他们甚至会将这些变量放在一个不同的文件中，并在需要时包含它们，以便连接到数据库。

既然我们已经连接到了服务器，我们觉得不该来对数据库做些什么操作呢？

## 查看现有的数据库

让我们创建一个你将用于电影网站的数据库。它由由三个表组成：

- movie 表，存储电影名称及其相关信息
- movietable 表，存储不同的电影类型
- people 表，存储电影中演员和导演的名字

## 尝试一下：创建数据库

执行以下步骤创建数据库和表：

1. 打开你的浏览器并输入以下代码。这将创建我们的数据库以及你存储数据所需的表。

```php
<?php
// 连接到 MySQL：注意我使用了自己的参数 - 你应该使用
// 自己的主机名、用户名和密码
$connect = mysql_connect("localhost", "root", "mysqlpass") or
die("Hey loser, check your server connection.");

// 创建主数据库
mysql_create_db("wiley")
or die(mysql_error());

// 确保我们最近创建的数据库是激活状态
mysql_select_db("wiley");

// 创建 "movie" 表
$movie = "CREATE TABLE movie (
movie_id int(11) NOT NULL AUTO_increment,
movie_name varchar(255) NOT NULL,
movie_type tinyint(2) NOT NULL default 0,
movie_year int(4) NOT NULL default 0,
movie_actor int(11) NOT NULL default 0,
movie_director int(11) NOT NULL default 0,
PRIMARY KEY (movie_type,movie_year)
) TYPE=MyISAM AUTO_INCREMENT=4 *;";

$results = mysql_query($movie)
or die (mysql_error());

//// 创建 'movietype' 表
$movietype="CREATE TABLE movietype (
mietype_id int(11) NOT NULL auto_increment,
mietype_label varchar(100) NOT NULL,
PRIMARY KEY (movietype_id)
) TYPE=MyISAM AUTO_INCREMENT=9";

$results = mysql_query($movietype)
or die (mysql_error());

// 创建 'people' 表
$people="CREATE TABLE people (
people_id int(11) NOT NULL auto_increment,
people_fullname varchar(255) NOT NULL,
people_isactor tinyint(1) NOT NULL default 0,
people_isdirector tinyint(1) NOT NULL default 0,
PRIMARY KEY (people_id)
) TYPE=MyISAM AUTO_INCREMENT=7";

$results = mysql_query($people)
or die (mysql_error());

echo "Movie Database successfully created!";

?>
```

2. 将此文件保存为 createmovie.php。

3. 使用此文件填充数据库，你应将其保存为 moviedata.php：

```php
<?php
// 连接到 MySQL
$connect = mysql_connect('localhost', 'root', 'mysqlpass') or
die ("Hey loser, check your server connection");

// 确保我们正在使用正确的数据库
mysql_select_db('wiley');

// 向 'movie' 表插入数据
$insert="INSERT INTO movie (movie_id, movie_name, movie_type, movie_year,
movie_actor, movie_director)
VALUES (1, 'Bruce Almighty', 5, 2003, 1, 2),
(2, 'Office Space', 5, 1999, 5, 6),
(3, 'Grand Canyon', 2, 1991, 4, 3)";
$results = mysql_query($insert);

// 向 'movietype' 表插入数据
$type="INSERT INTO movietype (movietype_id, movietype_label)
VALUES (1, 'Sci Fi'),
(2, 'Drama'),
(3, 'Adventure'),
(4, 'War'),
(5, 'Comedy'),
(6, 'Horror'),
(7, 'Action'),
(8, 'Kids')";
$results = mysql_query($type)
or die(mysql_error());

// 向 "people" 表插入数据
$people="INSERT INTO people (people_id, people_fullname, people_isactor, people_isdirector)
VALUES (1, 'Jim Carrey', 1, 0),
(2, 'Tom Shade', 0, 1),
(3, 'Lawrence Kasdan', 0, 1),
(4, 'Kevin Kline', 1, 0),
(5, 'Ron Livingston', 1, 0),
(6, 'Mike Judge', 0, 1)";
$results=mysql_query($people)
or die(mysql_error());

echo "Data inserted successfully!";
?>
```

1. 首先，在浏览器中运行 createmovie.php，然后运行 moviedata.php。

##原理

我们希望运行之前的文件时没有遇到错误，并且看到了“success”语句。虽然我们在代码中尝试了插入，但让我们逐一分析这些内容。

首先，我们连接到 MySQL 服务器以开始发送命令并操作数据库和表。我们也希望在发生错误时能立即停止。我们在代码的前几行中实现了这一点：

```php
<?php
// 连接到 MySQL；我们使用了自己的参数 - 你应该使用
// 自己的主机名、用户名和密码
$connect = mysql_connect('localhost', 'root', 'mysqlpass')
or die("Hey loser, check your server connection.");
```

然后我们实际上创建了数据库，如果由于某些原因无法创建，我们告诉服务器停止并显示问题：

```php
// 创建主数据库
mysql_create_db("wiley")
or die(mysql_error());
```

我们还确保选择了数据库，以便服务器知道我们正在操作哪一个：

```php
// 确保我们最近创建的数据库是激活状态
mysql_select_db("wiley");
```

然后我们开始创建表，从 movie 表开始。我们定义了字段并设置了它们的参数。我们还将 movie_id 的自增值设置为 4，因为我们将通过 moviedata.php 输入 1-3 的记录。我们将在本章后面详细讨论这一功能，但现在可以让你预览一下：

```php
// 创建 'movie' 表
$movie = "CREATE TABLE movie (
movie_id int(11) NOT NULL auto_increment,
movie_name varchar(255) NOT NULL,
movie_type tinyint(2) NOT NULL default 0,
movie_year int(4) NOT NULL default 0,
movie_actor int(11) NOT NULL default 0,
movie_director int(11) NOT NULL default 0,
PRIMARY KEY (movie_type,movie_year)
TYPE=MyISAM AUTO_INCREMENT=4;";
```

一旦我们准备好了 MySQL 语句，只需通过 `mysql_query` 命令将其发送到服务器。同样，如果有错误，我们告诉服务器停止执行并告知错误：

```php
$results = mysql_query($movie)
or die(mysql_error());
```

我们以同样的方式创建了 movie 类型和 people 表：

```php
// 创建 'movietype' 表
$movietype = "CREATE TABLE movietype (
movietype_id int(11) NOT NULL auto_increment,
movetype_label varchar(100) NOT NULL,
PRIMARY KEY (movietype_id)
) TYPE=MyISAM AUTO_INCREMENT=9";
```

```php
$results = mysql_query($movietype)
or die(mysql_error());
```

```php
// 创建 'people' 表
$people = "CREATE TABLE people (
people_id int(11) NOT NULL auto_increment,
people_fullname varchar(255) NOT NULL,
people_isactor tinyint(1) NOT NULL default 0,
people_isdirector tinyint(1) NOT NULL default 0,
PRIMARY KEY (people_id)
) TYPE=MyISAM AUTO_INCREMENT=7";
```

```php
$results = mysql_query($people)
or die(mysql_error());
```

如果我们的程序运行到最后，我们就假设一切都是成功的，因此我们输出了一条语句以便确认：

```php
echo "Movie Database successfully created";
```

通过我们的 moviedata.php 文件，我们向表中填充了信息。一既如此，我们必须连接到 MySQL 服务器并选择数据库。（提示：这难道不像一个包含的文件一样棒吗？）

```php
<?php
// 连接到 MySQL
$connect = mysql_connect('localhost', 'root', 'mysqlpass') or die("Hey loser, check your server connection.");
```

```php
// 确保我们正在使用正确的数据库
mysql_select_db("wiley");
```

然后我们开始向 movie 表插入数据。我们首先列出了我们要访问的列。我们列出了每个记录的值：

```php
// 向 "movie" 表插入数据
$insert="INSERT INTO movie (movie_id, movie_name, movie_type, movie_year,
movie_actor, movie_director)
VALUES (1, 'Bruce Almighty', 5, 2003, 1, 2),
(2, 'Office Space', 5, 1999, 5, 6),
(3, 'Grand Canyon', 2, 1991, 4, 3)";
$results = mysql_query($insert)
or die(mysql_error());
```

我们对其他表（movie 和 type也执行了同样的操作。

