

## 使用实时数据修订计算脚本

此前两次，当您从数据库输出数据时，都是直接输出到 HTML 中。您将“旅行者日记”条目输出到 index.asp 的主页面中，并将 tourName/tourID 配对输出到表单菜单元素中。在此步骤中，您无需向用户可见的位置输出成人和儿童价格。事实上，它们需要输出到计算本身中。不过，您会看到，向脚本内部输出的方式与向 XHTML 输出的方式相同。

不过，在执行此操作之前，让我们添加一个简单的功能：显示用户刚刚计算的旅游名称，以防他们忘记或选择了错误的旅游。

- 1) 在 tourprice_processor.asp 中，切换到设计视图。在第一句中的单词 tour 之后，添加以下文本：, XX,。选择 XX，并使用属性检查器对其应用加粗。

再次说明，X 被用作占位符文本。使用此文本的优势在于，您可以按照希望动态内容显示的方式对其进行格式化，在此示例中为加粗。

![](img/43fd0127a958864ab2d93e28efe683e7_280_0.png)

- 2) 选择 XX 文本，然后切换到插入栏的 Application 类别。单击 Dynamic Data 按钮，并在弹出菜单中选择 Dynamic Text。

Application 选项卡用于插入常见的动态元素，例如动态文本。

![](img/43fd0127a958864ab2d93e28efe683e7_280_1.png)

- 3) 在 Dynamic Text 对话框中，展开 Recordset (rs_tourprices_filtered)，然后单击 tourName。单击 OK。

![](img/43fd0127a958864ab2d93e28efe683e7_281_0.png)

您刚刚完成的操作相当于将绑定从“绑定”面板拖动到页面上。您还应该能够理解 Dreamweaver 在代码窗口中输出的代码：

在 ASP 中，XX 原先出现的位置会添加以下内容：<%= (rs_tourprices_filtered.Fields.Item("tourName").Value) %>。请记住，<%=（与 <% 相对）表示 <% Response.Write，因此这是一个输出脚本。从其余内容您大概可以猜到，它正在输出记录集 rs_tourprices_filtered 中 tourName 字段的值。

在 ColdFusion 中，会出现以下代码：<cfoutput>#rs_tourprices_filtered.tourName#</cfoutput>。同样，<cfoutput> 标签等同于 ASP 的 Response.Write，输出的是存储在 rs_tourprices 中的 tourName 值。

在 PHP 中，会出现以下代码：<?php echo $row_rs_tourprices_filtered ['tourName']; ?>。echo 命令大致相当于 ASP 的 Response.Write 和 ColdFusion 的 <cfoutput>。与 ASP 和 ColdFusion 版本一样，此块正在输出 rs_tourprices 中的 tourName 值。

阅读和理解代码非常重要，因为在下一步中，您需要进行一些手动编码。

- 4) **在代码视图中，查找计算脚本。删除将 basePrice 变量的值设置为表单变量 tourName 的行。**

要在 ASP 中删除的行是 basePrice=Request.Form("tourName")，在代码视图中大约位于第 34 行（上下几行）。

要在 ColdFusion 中删除的行是 <cfset basePrice = form.tourName>，在代码视图中大约位于第 14 行（上下几行）。

要在 PHP 中删除的行是 $basePrice = $_POST['tourName'];，在代码视图中大约位于第 12 行。

此行已不再必要，因为您不再从表单获取基础价格，而是从数据库获取。此外，您现在需要使用两个价格：儿童价格和成人价格。

```
25   IF Not IsNumeric(Request.Form("numAdults")) Or Not IsNumeric(Request.Form("numChildren")) Then
26      Response.Redirect("tourprice.asp?error=notnumeric")
27   End If
28  %>
29  <%
30  
31   Dim numAdult, numChild, basePrice, tourPrice
32   numAdult = Request.Form("numAdults")
33   numChild = Request.Form("numChildren")
34   basePrice = Request.Form("tourName")
35   tourPrice = (numAdult * basePrice) + (numChild * basePrice)
36   %>
37
38   <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"
39   <html xmlns="http://www.w3.org/1999/xhtml">
40   <head>
```

- 5) **添加两行新代码，用于设置两个新变量的值：basePriceAdult 和 basePriceChild。**

```
In ASP:

basePriceAdult=rs_tourprices_filtered.Fields.Item("basePriceAdult").Value
basePriceChild=rs_tourprices_filtered.Fields.Item("basePriceChild").Value
```

```
In ColdFusion:

<cfset basePriceAdult = rs_tourprices_filtered.basePriceAdult>
<cfset basePriceChild = rs_tourprices_filtered.basePriceChild>
```

```
In PHP:

$basePriceAdult = $row_rs_tourprices_filtered['basePriceAdult'];
$basePriceChild = $row_rs_tourprices_filtered['basePriceChild'];
```

所有这些脚本都会创建两个新变量，并将值设置为从数据库中检索到的相应成人和儿童价格。

```
<%
Dim numAdult, numChild, basePrice, tourPrice
numAdult = Request.Form("numAdults")
numChild = Request.Form("numChildren")
basePriceAdult = rs_tourprices_filtered.Fields.Item("basePriceAdult").Value
basePriceChild = rs_tourprices_filtered.Fields.Item("basePriceChild").Value
tourPrice = (numAdult * basePrice) + (numChild * basePrice)
%>
```

- 6) 仅限 ASP 用户：从 Dim 行中删除 basePrice，并将 basePriceAdult 和 basePriceChild 添加到列表中。

由于 ASP 要求显式声明所有变量，因此每次更改变量时，都要记得更新该声明。

- 7) 在计算行本身中，使用适当的新变量更新 basePrice 变量。

In ASP:

```
tourPrice = (numAdult * basePriceAdult) + (numChild * basePriceChild)
```

In ColdFusion:

```
<cfset tourPrice = (numAdult * basePriceAdult) + (numChild * basePriceChild)>
```

In PHP:

```
$tourPrice = ($numAdults * $basePriceAdult) + ($numChildren * $basePriceChild);
```

现在，计算反映了您从数据库中检索到的值。

```
<%
Dim numAdult, numChild, basePriceAdult, basePriceChild, tourPrice
numAdult = Request.Form("numAdults")
numChild = Request.Form("numChildren")
basePriceAdult = rs_tourprices_filtered.Fields.Item("basePriceAdult").Value
basePriceChild = rs_tourprices_filtered.Fields.Item("basePriceChild").Value
tourPrice = (numAdult * basePriceAdult) + (numChild * basePriceChild)
%>
```

- 8) 保存并上传 tourprice_processor.asp。在站点面板中，选择 tourprice.asp 并按 F12 测试应用程序。

应用程序按预期运行。应用程序会根据用户输入的信息输出正确的计算结果。最棒的是，维护此应用程序与维护数据库一样简单。如果价格上涨并将新值添加到数据库中，计算器会立即反映该变化。如果您添加或删除整个旅游，该变化也会在应用程序中体现。

![](img/43fd0127a958864ab2d93e28efe683e7_284_0.png)

## 使用注释记录代码

您添加了大量功能，使旅游价格计算器应用程序能够运行。您可以在所有 Web 页面中看到这项工作的结果。例如，在我的 tourprice_processor.asp 副本中，正式的 XHTML 文档直到第 39 行才开始——其上方全部是 ASP 脚本！使用 ColdFusion 的用户会发现，他们的 XHTML 文档大约从第 18 行开始。在大多数情况下，它们具有相同的脚本并执行相同的操作——只是 ColdFusion 所需的代码行数较少。PHP 介于两者之间——我的 XHTML 文档从第 28 行开始。

如果您浏览 tourprice.asp 和 tourprice_processor.asp 顶部的所有代码，应该能够理解您会发现的几乎所有脚本（ASP 和 PHP 用户会有一个例外，我稍后会说明）。您之所以能够阅读这些脚本，不仅是因为您开始掌握 ASP、ColdFusion 或 PHP 脚本，还因为它们在您脑海中记忆犹新。但是，如果您六个月后回来，或者今天有人第一次将这段代码交给您，您可能无法一眼看出所有内容的作用。

