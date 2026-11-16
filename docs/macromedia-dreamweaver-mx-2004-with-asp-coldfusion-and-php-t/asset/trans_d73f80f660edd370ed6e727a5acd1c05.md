

- 7) 使用占位符为 <td> 标签内的内容创建静态 HTML 结构。

```
<td>Country Name</td>
<td><a href="admin_cp_update.asp?countryID=CountryID">Modify this country's profile</a></td>
<td><a href="admin_cp_delete_processor.asp?countryID=CountryID">Delete</a></td>
```

此代码对 ASP 和 ColdFusion 都相同（除了 ColdFusion/PHP 的 href 属性中文件扩展名应为 .cfm/.php 而非 .asp），因为它仅是静态 HTML。我们在此处使用占位符，以确保在添加动态代码之前 HTML 语法正确。

![](img/43fd0127a958864ab2d93e28efe683e7_483_0.png)

- 8) 如下所示，将三个占位符替换为动态输出。

### 在 ASP 中：

```
<td><%=rs_countries("countryName")%></td>
<td><a href="admin_cp_update.asp?countryID=<%=rs_countries("countryID")%>">Modify this country's profile</a></td>
<td><a href="admin_cp_delete_processor.asp?countryID=<%=rs_countries("countryID")%>">Delete</a></td>
```

### 在 ColdFusion 中：

```
<td>#countryName#</td>
<td><a href="admin_cp_update.cfm?countryID=#countryID#">Modify this country's profile</a></td>
<td><a href="admin_cp_delete_processor.cfm?countryID=#countryID#">Delete</a></td>
```

### 在 PHP 中：

```
<td><?php echo $row_rs_countries['countryName']; ?></td>
<td><a href="admin_cp_update.php?countryID=<?php echo $row_rs_countries['countryID']; ?>">Modify this country's profile</a></td>
<td><a href="admin_cp_delete_processor.php?countryID=<?php echo $row_rs_countries['countryID']; ?>">Delete</a></td>
```

在本书学习过程中，你已经看到过大量的 ASP、ColdFusion 和 PHP 输出代码，因此代码应该易于阅读，尤其是记住 ASP 中的 <%= 等同于 <% Response.Write() 之后。

```
57 <table width="984" border="1" cellspacing="0" cellpadding="3">
58 <%
59 Do Until rs_countries.EOF
60 <tr>
61 <td><%=rs_countries("countryName")%></td>
62 <td><a href="admin_cp_update.asp?countryID=<%=rs_countries("countryID")%>">Modify this country's</a></td>
63 <td><a href="admin_cp_delete_processor.asp?countryID=<%=rs_countries("countryID")%>">Delete</a></td>
65 </tr>
66
67 rs_countries.MoveNext()
68
69 Loop
70 </table>
```

- 9) 在浏览器中保存、上传并测试文件。

表格的行数与 tbl_country 中的记录数相同。如果将鼠标悬停在其中一个链接上，你将看到不仅有 URL，还会看到附加了正确国家 ID 的 countryID 参数。

![](img/43fd0127a958864ab2d93e28efe683e7_484_0.png)

你也可以关闭 admin_cp_master.asp。

## 创建更新记录详细信息页面

主页已准备就绪，因此下一步是创建详细信息页面。在此任务中，你将构建用于更新记录的详细信息页面。实际上，你不需要为删除记录创建详细信息页面，因为用户不需要查看页面的任何详细信息——他们只需要一个处理删除的脚本。

你即将创建的更新页面与你之前构建的允许用户插入新国家文件的页面非常相似。事实上，该页面将使用同一表单的修改版本。唯一的区别是，更新页面上的表单字段将已经填好，并且，当然，当用户提交表单时，将更新数据库记录，而不是创建新记录。

- 1) 打开 admin_cp_insert.asp。选择“文件”>“另存为”，并将其另存为 admin_cp_update.asp（覆盖原始文件）。将页面标题更改为“更新国家简介”，并将网页标题更改为“Newland Tours Admin: 更新国家简介”。

这样做，你将保留所创建的表单以及 rs_regions 记录集，该记录集检索所有区域及其 ID，并填充“区域”下拉菜单。

使用此技术时，你必须牢记所有需要更改的内容。在此表单中，每个字段都必须为所选国家自动填充来自数据库的相应数据；需要创建一个新记录集来便于此更改。<form> 标签的 action 属性需要指向 admin_cp_update_processor.asp，而不是插入处理器页面，并且应重命名表单。

- 2) 在代码视图中，查找打开的 <form> 标签，并按如下所示设置其属性。

action (ASP):

```
admin_cp_update_processor.asp?countryID=<%=Request.QueryString("countryID")%>
```

action (ColdFusion):

```
admin_cp_update_processor.cfm?countryID=<cfoutput>#URL.countryID#</cfoutput>
```

action (PHP):

```
admin_cp_update_processor.php?countryID=<?php echo $_GET['countryID']; ?>
```

method: post（与之前相同）

name: frm_updateProfile

id: frm_updateProfile

这是一个容易忽略的步骤，因此最好立即完成。

```
<div>
 <% name="top" id="top"/> %>Update a Country Profile </div>
 <div id="tmp_updateProfile" runat="server">
 <form id="form1" runat="server">
```

action 属性需要解释。请记住，当此页面首次加载时，countryID 变量会出现在从主页发送的 URL 中。查询依赖于此变量，因此知道用户想要修改哪个国家。
现在，数据库的实际更新将在另一个页面上完成：
admin_cp_update_processor.asp。但是，该页面也需要知道应更新哪个记录。通过将查询字符串或 URL 参数附加到表单的 action 属性，你实际上将此查询字符串变量发送到处理器页面。

> 提示 通过表单传递只读数据的另一种常见方法是使用隐藏表单字段。

- 3) 创建一个新记录集 rs_countryDetail，它检索主页上所选国家简介的所有存储信息。

在 ASP 中，在 dbConn 块内，在当前以 Set rs_regions = 开头的行下方新建一行：

```
Set rs_countryDetail = dbConn.Execute("SELECT * FROM tbl_country INNER
JOIN tbl_region ON tbl_region.regionID=tbl_country.region WHERE
tbl_country.countryID=" & Request.QueryString("countryID")")
```

在 ColdFusion 中：

```
<cfquery name="rs_countryDetail" datasource="newland">
SELECT *
FROM tbl_country
INNER JOIN tbl_region ON tbl_region.regionID=tbl_country.region
WHERE tbl_country.countryID=#url.countryID#
</cfquery>
```

在 PHP 中，在你先前编写的查询块末尾，就在闭合 ?> 之前：

```
$query_rs_countryDetail = "SELECT * FROM tbl_country INNER JOIN tbl_region
ON tbl_region.regionID=tbl_country.country WHERE
tbl_country.countryID=" . $_GET['countryID'];
$rs_countryDetail = mysql_query($query_rs_countryDetail);
$row_rs_countryDetail = mysql_fetch_assoc($rs_countryDetail);
```

```
$rs ...
Dim rs_countryDetail
...
```

```
<?php
$host = "localhost";
$user = "root";
$pwd = "priscilla";
$dbConn = mysqli_connect($host,$user,$pwd);

// $dbconn = "newland_tours";
$valSelect_db = mysqli_select_db($dbConn,
"newland_tours");
$query_rs_regions = "SELECT * FROM tbl_region ORDER BY regionName";
$rs_regions = mysqli_query($dbConn, $query_rs_regions);
$row_rs_regions = mysqli_fetch_assoc($rs_regions);
$query_rs_countryDetail = "SELECT * FROM tbl_country INNER JOIN tbl_region ON tbl_region.regionID=tbl_country";
$rs_countryDetail = mysqli_query($query_rs_countryDetail);
$row_rs_countryDetail = mysqli_fetch_assoc($rs_countryDetail);
?>
```

再次，此代码中的大部分内容对你来说应该很熟悉。不过，解构一下 SQL 语句是值得的。请记住，tbl_country 包含 Newfoundland 关于一个国家的大部分信息。例外是区域名称，它存储在另一个表中，并通过关系与 tbl_country 链接。因此，SQL 语句使用 JOIN 来检索此附加信息。注意的是，此 SQL 语句不会检索所有国家简介——只检索用户在主页上选择的那个简介，其 ID 作为查询字符串/URL 变量发送。

> ASP 用户还应在脚本顶部其他 Dim 语句出现的位置附近 Dim 新变量 rs_countryDetail。没有它代码仍应能工作，但声明所有变量是良好实践。

你现在拥有 Newfoundland 保存的所选国家的所有信息。你将使用此信息使用数据库中的实时数据填充页面上的表单。当用户提交表单时，脚本将用表单中的信息替换现有数据库数据。既然此数据已可用，你需要将其绑定为每个相应表单元素的默认值。

- 4) ASP 和 PHP 用户：滚动到页面底部，添加关闭和销毁记录集所需的代码。

在 ASP 中：

```
<%
rs_countryDetail.Close()
Set rs_countryDetail = Nothing
%>
```

在 PHP 中：

```
<?php
mysql_free_result($rs_countryDetail);
?>
```

