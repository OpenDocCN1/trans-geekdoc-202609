

理解这些行更容易，如果你回忆 SQL 中 INSERT 语句的基本语法：

```
INSERT INTO tbl_table
(field1, field2, field3)
VALUES
('value1', 'value2', 'value3')
```

ASP、ColdFusion 和 PHP 代码块正在构建使用此语法的 SQL 语句。但是，同样，由于它们正在用实际值替换变量，你需要让每个服务器知道在将这些表达式插入数据库之前先对其进行求值。结果，你会在 ColdFusion 版本中看到大量的井号，在 ASP 和 PHP 版本中看到大量的字符串连接。

> **提示** ASP 和 PHP 用户应该善用代码着色。通常在你输入错误的一瞬间着色就会改变，从而在页面测试之前轻松发现问题。ASP：在所有情况下，Request.Form 应该是紫色，而表单字段名应该始终是绿色。用于连接的和号（&）应始终是蓝色。PHP：在所有情况下，字符串字面量（包括所有逗号和单引号）是红色，$_POST 始终是浅蓝色，而句点和方括号始终是深蓝色。

> **注意** ASP 和 PHP 同时使用双引号（""）和单引号（''），这可能会令人困惑。双引号括起来的内容是 ASP/PHP 的一部分，具体来说，是 ASP/PHP 应该原样传递而不求值的字符串字面量。单引号括起来的内容属于 SQL，表示正在插入数据库的值。

- 4) 插入将用户重定向到主页面的代码，一旦插入完成。

在 ASP 中，在闭合 `%>` 之前：

```
Response.Redirect("admin_cp_master.asp")
```

在 ColdFusion 中：

```
<cflocation url="admin_cp_master.cfm">
```

在 PHP 中，在闭合 `?>` 之前：

```
header("Location: admin_cp_master.php");
```

因为 ASP、ColdFusion 和 PHP 会在出现问题时显示错误消息，所以只有在插入成功时才会执行重定向行。

测试页面以确保其正常工作（你可以随意编造关于你国家的详细信息）。插入数据后，你将被发送到一个尚未完成的 admin_cp_master.asp。但是，有一个简单的方法可以查看插入是否成功：转到国家配置文件。更新国家配置文件是这个应用程序的全部目的。你应该在那里找到刚插入的国家。不要担心无意义的数据——你将在本课后面构建一个删除应用程序，并且需要一个或两个虚拟国家来测试它，所以暂时让你的创作留在数据库中。

![](img/43fd0127a958864ab2d93e28efe683e7_478_0.png)

> **注意** 在测试这些页面的功能时，不要在任何描述中输入撇号。如果这样做，你会看到错误消息。本课后面将解决此问题。

> **注意** 除非你将图片上传到 images 文件夹，并且名称与表单中输入的名称相同，否则图片链接将损坏。

## 创建主页面

主页面-详细页面配对对于更新和删除功能是必要的，因为你必须允许用户选择要更新或删除的国家。在此任务中，你将创建一个简单的主页面-详细页面，包含一个表格，每行显示每个国家的名称、修改国家的链接和删除国家的链接。与以前一样，这些链接中的每一个都会传递一个 URL 参数，标识用户选择的国家。

- 1) 打开 admin_cp_master.asp，并切换到代码视图。
  与以前一样，你将在布局页面之前创建记录集，并且由于你将手写创建记录集所需的代码，你需要处于代码视图。

- 2) 在限制访问服务器行为代码和文档本身开头之间（就在 `<!DOCTYPE>` 标记之前），输入创建记录集所需的代码，该记录集（"rs_countries"）将检索 tbl_country 中每条记录的国家名称和 ID。
  在 ASP：

```
<%
Dim dbConn
Dim rs_countries
set dbConn = Server.CreateObject("adodb.connection")
dbConn.open("newland")
Set rs_countries = dbConn.Execute("SELECT countryID, countryName FROM tbl_country ORDER BY countryName ASC")
%>
```

在 ColdFusion 中：

```
<cfquery name="rs_countries" datasource="newland">
SELECT countryID, countryName FROM tbl_country ORDER BY countryName ASC
</cfquery>
```

在 PHP 中：

```
<?php
// Set up connection to MySQL
$host = "localhost";
$user = "[enter your username]";
$pwd = "[enter your password]";
$dbConn = mysql_connect($host,$user,$pwd);
// Connect to newland_tours database
$database = "newland_tours";
mysql_select_db($database);
$query_rs_countries = "SELECT countryID, countryName FROM tbl_country ORDER BY
countryName ASC";
$rs_countries = mysql_query($query_rs_countries);
$row_rs_countries = mysql_fetch_assoc($rs_countries);
?>
```

```
19 Response.Redirect(MM_urlFailedURL)
20 End If
21 %>
22 <%
23 <%
24 Dim dbConn
25 Dim rs_countries
26 Set dbConn = Server.CreateObject("adodb.connection")
27 dbConn.open("newland")
28 Set rs_countries = dbConn.Execute("SELECT countryID, countryName FROM tbl_country ORDER BY countryName ASC")
29 %>
30 <%
31 <!DOCTYPE HTML PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-t...
32 <html xmlns="http://www.w3.org/1999/xhtml">
33 <head>
```

除了 SQL 语句的细节之外，这段代码与本课前面使用的代码相同，因此你应该能够理解它。查询本身也很容易阅读：它按国家名称检索国家名称和唯一 ID，并按国家名称排序。

- **3) 仅限 ASP 和 PHP 用户：在文档末尾添加关闭和销毁记录集的代码。**

在 ASP 中：

```
<%
rs_countries.Close()
Set rs_countries = Nothing
%>
```

在 PHP 中：

```
<?php
mysql_free_result($rs_countries);
?>
```

同样，这段代码防止记录集在服务器上浪费内存。

```
70 </body>
71 </html>
72 <%
73 rs_countries.Close()
74 Set rs_countries = Nothing
76 %>
```

- 4) 切换到设计视图，并键入以下两行文本：

Select a country to modify or delete.

Caution: Deleting is instant and permanent.

同样，为用户提供指示对于应用程序的成功至关重要。

![](img/43fd0127a958864ab2d93e28efe683e7_481_0.png)

## 选择要修改或删除的国家配置文件

Select a country to modify or delete.

Caution: Deleting is instant and permanent.

- 5) 返回代码视图，在刚刚创建的段落下方，添加代码以创建一个具有一行三列的新表。

```
<table width="98%" border="1" cellspacing="0" cellpadding="3">
<tr>
<td>XX</td>
<td>XX</td>
<td>XX</td>
</tr>
</table>
```

这将创建表的基本框架。完成后，其内容将动态生成，每条记录将映射到单个行。由于你无法预先知道行数，你将不得不遍历记录集，为每条记录创建一个新行。

- 6) 输入创建循环结构所需的适当代码，该结构应围绕 `<tr>` 标记。代码应包装在开头和结尾的 `<tr>` 标记之外。

在 ASP：

```
<%
   Do Until rs_countries.EOF
   %>
   <tr>
   <td>XX</td>
   <td>XX</td>
   <td>XX</td>
   </tr>
   <%
   rs_countries.MoveNext()
   Loop
   %>
```

### 在 ColdFusion 中：

```
<cfoutput query="rs_countries">
<tr>
<td>XX</td>
<td>XX</td>
<td>XX</td>
</tr>
</cfoutput>
```

### 在 PHP 中：

```
<?php
 do {
 ?>
 <tr>
 <td>XX</td>
 <td>XX</td>
 <td>XX</td>
 </tr>
 <?php
 }
 while ($row_rs_countries = mysql_fetch_assoc($rs_countries));
 ?>
```

在这一步中，你实际上正在创建重复区域——只是不使用 Dreamweaver 行为。尽管三种服务器模型在外观上有所不同，但它们使用的逻辑非常相似。每个模型都有一段代码位于要循环的部分（`<tr>` 部分）之前和之后。每个模型都指定一个查询并创建一个循环，只有在记录集没有更多记录时才会中断：ASP 的 EOF 明确实现此功能；ColdFusion 中的记录集循环是隐含的；当你在 `<cfoutput>` 标记中指定 query 属性时；PHP 使用 mysql_fetch_assoc() 进行测试。

接下来，你需要构建表格单元格的内容，这些内容将包含 HTML 与 ASP、ColdFusion 或 PHP 代码的混合物。

![](img/43fd0127a958864ab2d93e28efe683e7_482_0.png)

