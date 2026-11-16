

这就是为什么此刻就必须理解这个重要主题的原因。你为项目选择的数据库平台取决于多个重要因素，而一名真正的专业人士几乎肯定会在他或她的职业生涯中某个时间点上使用之前提到的所有四个平台。

话虽如此，也会有些时候选择完全开放，最终取决于个人偏好。本书的作者在这种情况下更倾向于 PostgreSQL。它免费、快速、支持良好、可扩展、可伸缩且可靠，并拥有一个企业级功能集，在功能上略胜 MySQL 一筹。毫无疑问，这种观点与常见做法相悖，但同样，在企业中使用 PHP 的想法本身也是如此。

这里要记住的关键是，你要意识到这只是一种 *个人偏好*；归根结底，*这并不重要*。关于任何事情（操作系统、编程语言、Web 服务器、数据库）的计算机相关的宗教战争都极其令人厌倦，是青春痘少年程序员的标志，而非专业人士。每一个倡导平台 X 的所谓专家，你都会找到另一个倡导平台 Y 的人，而且此人很可能同样能滔滔不绝地侃侃而谈。

所以，坦率地说，*放下执念*。本章（实际上，本书的其余部分）将向你展示，为何开发得当的 PHP 应用程序是“数据库无关”的——正如它们是“Web 服务器无关”和“操作系统无关”的。本书不是关于“LAMP”或“LAPP”；如果你将命名法推演到其自然结论，本书实际上讲的是“XXXP”——也就是，纯 PHP。

不过，本书中你遇到的示例将使用 PostgreSQL。有关其安装和配置的更多信息，请参阅附录 D。如果这个选择让你极度困扰，作者恳请你为了本书提供的更广泛的教育而忍一忍——然后在自己的项目中随意使用 *任何你喜欢的东西*。正如本章和下一章所示，你不需要做太多更改就能进行切换。

## 回顾

让我们回顾一下 PHP 自诞生以来数据库连接的工作方式。以下内容假设你已安装正常工作的 PHP 并启用了 PostgreSQL 支持，且同一台机器上已安装正常工作的 PostgreSQL。

在控制台中按如下方式在 PostgreSQL 中创建新数据库：

```
$ /usr/local/pgsql/bin/createdb chaptersix
CREATE DATABASE
```

此语法假设 PostgreSQL 安装在 Linux 或其他 UNIX 平台的 /usr/local/pgsql 目录中。如果你在 Windows 或 Mac OS X 上运行，情况可能会有所不同。PostgreSQL 安装程序可能已将 bin 目录添加到你的路径中。如果是这样，你可以直接输入 createdb chaptersix。

CREATE DATABASE 消息表明数据库已从控制台成功创建。很好，但你的应用程序必须能够连接到该数据库。你的应用程序不会从控制台运行，因此它需要自己的登录凭据进行身份验证。因此，创建一个名为 chaptersix 的新用户，该用户可以连接到你的新数据库：

```
$ /usr/local/pgsql/bin/createuser -P chaptersix
Enter password for new role:
Enter it again:
Shall the new role be a superuser? (y/n) n
Shall the new role be allowed to create databases? (y/n) n
Shall the new role be allowed to create more new roles? (y/n) n
CREATE ROLE
```

在第一个提示符处，为新角色输入密码。就本测试而言，我们也将其设为 chaptersix。不完全安全，但用于测试目的足够了。

自然后来，后三个提示符都应该得到否定的回答。这不是什么特殊类型的用户；因此它只需要最低权限。

现在你有了一个空数据库，以及应用程序可以使用的登录凭据。让我们创建一个示例表：

```
$ /usr/local/pgsql/bin/psql chaptersix
Welcome to psql 8.2.4, the PostgreSQL interactive terminal.

Type:  \copyright for distribution terms
       \h for help with SQL commands
       \? for help with psql commands
       \g or terminate with semicolon to execute query
       \q to quit

chaptersix=# CREATE TABLE "user" (
chaptersix(#  "id" SERIAL PRIMARY KEY NOT NULL,
chaptersix(#  "username" character varying(32),
chaptersix(#  "password_hash" character varying(32),
chaptersix(#  "first_name" character varying(64),
chaptersix(#  "last_name" character varying(64));
NOTICE:  CREATE TABLE will create implicit sequence "user_id_seq" for serial column
             "user.id"
NOTICE:  CREATE TABLE / PRIMARY KEY will create implicit index "user_pkey" for
             table "user"
CREATE TABLE
```

如果从上述快照中不清楚，以下是你在 PostgreSQL 控制台中输入的内容：

```
CREATE TABLE "user" (
  "id" SERIAL PRIMARY KEY NOT NULL,
  "username" character varying(32),
  "password_hash" character varying(32),
  "first_name" character varying(64),
  "last_name" character varying(64));
```

因为你创建的用户没有权限，所以它对刚才创建的表没有访问权限。你必须告诉 PostgreSQL，允许名为 chaptersix 的用户访问名为 chaptersix 的数据库，并且该用户对该数据库中的关系拥有完全读写权限。

假设你仍在 PostgreSQL 控制台会话中（除非你输入 \q 并按 Enter 退出了），你可以运行以下两个 SQL 语句来设置所需的权限：

```
chaptersix=# GRANT ALL PRIVILEGES ON "user" TO "chaptersix";
GRANT
chaptersix=# GRANT ALL PRIVILEGES ON "user_id_seq" TO "chaptersix";
GRANT
```

请注意，你必须同时授予数据库表及其关联序列的权限。

最后，为了本练习的目的，让我们向刚创建的表中插入一些数据。PostgreSQL 允许你使用 COPY 语句批量插入数据，但对于输入测试数据，它比较挑剔。相反，让我们仅使用一些老派的 INSERT 语句将四行测试数据插入数据库，如下所示：

```
INSERT INTO "user"("username", "password_hash", "first_name", "last_name")
VALUES ('ed', md5('berkhamsted'), 'Ed', 'Lecky-Thompson');
INSERT INTO "user"("username", "password_hash", "first_name", "last_name")
VALUES ('steve', md5('newyork'), 'Steve', 'Nowicki');
INSERT INTO "user"("username", "password_hash", "first_name", "last_name")
VALUES ('marie', md5('leicester'), 'Marie', 'Ellis');
INSERT INTO "user"("username", "password_hash", "first_name", "last_name")
VALUES ('harriet', md5('cambridge'), 'Harriet', 'Frankland');
```

假设一切顺利无误，你应该会看到以下消息的四个实例：

```
INSERT 0 1
```

现在你已经使用完 PostgreSQL 控制台。你可以输入 \q 并按 Enter 键退出它。

现在你已经设置好了数据库，配置了用户，并且测试表和数据也都准备就绪。是时候重新熟悉 PHP 如何与数据库协同工作了。启动你的文本编辑器，敲出以下代码。将其命名为 dbtest.php 并放在 Web 服务器文档根目录的某个位置：

```
<?php
$objHandle = pg_connect("host=localhost port=5432 dbname=chaptersix user=chaptersix
         password=chaptersix");

if (!$objHandle) {
    echo "An error occurred connecting.\n";
    exit;
}
$objResult = pg_query($objHandle, "SELECT * FROM \"user\"");
if (!$objResult) {
    echo "An error occurred querying.\n";
    exit;
}
$arRowHash = pg_fetch_all($objResult);
for ($i=0; $i>=sizeof($arRowHash)-1; $i++) {
    print "Row $i<br />\n";
foreach ($arRowHash[$i] as $key => $value) {
    print " - Column $key, value $value<br />\n";
};
pg_close($objHandle);
?>
```

在 Web 浏览器中打开上述代码，你会看到以下输出：

```
Row 0
- Column id, value 1
- Column username, value ed
- Column password_hash, value fb097067945b57d5943bf9a49b7b7f12
- Column first_name, value Ed
- Column last_name, value Lecky-Thompson
Row 1
- Column id, value 2
- Column username, value steve
- Column password_hash, value 369389d19e24204b4927e30dd7c39efc
- Column first_name, value Steve
- Column last_name, value Nowicki
Row 2
- Column id, value 3
- Column username, value marie
- Column password_hash, value 16ba4bec9c54a088c9762527601b355a
- Column first_name, value Marie
- Column last_name, value Ellis
Row 3
- Column id, value 4
- Column username, value harriet
- Column password_hash, value efa93cabd5de7d42d6a31d41c33043ab
- Column first_name, value Harriet
- Column last_name, value Franklin
```

如果你反而看到一个刻意捕获的错误消息，请检查 PHP 错误日志以找出原因。你可能忘记正确设置权限，或者可能未启动 PostgreSQL 以允许来自外部数据源的 TCP/IP 连接。有关所需的 PostgreSQL 设置，请参阅附录 D。

希望一切顺利，并且上述代码看起来相当直接。它当然不应该是你以前没遇到过的东西。

这里基本上调用了四个过程式函数：pg_connect、pg_query、pg_fetch_all 和 pg_close。它们基本上按名称所暗示的方式工作。前缀 pg_ 表示它们是 PostgreSQL 特定函数；同样地，MySQL 特定函数以 mysql_ 开头，Oracle 的以 oci_ 开头，SQL Server 的以 mssql_ 开头。

## 问题

坦率地说，这种状况是一团糟。PHP 非常独特，因为它几乎没有预定义的类。几乎每个方法都存在于一种全局命名空间中。它不是父类的一部分，这意味着它实际上是一个“函数”。这是 PHP 3 的遗留问题，当时对 OOP 的支持，嗯，

