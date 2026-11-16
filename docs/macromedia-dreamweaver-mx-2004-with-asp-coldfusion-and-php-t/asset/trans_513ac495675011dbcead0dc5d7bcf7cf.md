
此设置，因为 ColdFusion 仅支持 ColdFusion 标记语言 (CFML)，因此不会存在混淆的可能。

第二个属性 CODEPAGE 指定页面的语言。1252 指英语。

- 3) 仅限 ASP：将插入点定位在第 2 行，按两次 Enter/Return 键以添加更多空间。从第 3 行开始，键入以下代码：

```
<%
Dim numAdult, numChild, basePrice, tourPrice
%>
```

如前所述，<% 用于标记服务器需要处理的 ASP 代码。结尾 %> 上方的额外空间是为留给后续脚本预留空间，您稍后将添加该脚本。

第二行可能看起来有点奇怪。在 ASP 中，每当您想要创建新变量时，必须先声明它。您使用 Dim 声明新变量。因此，第二行向服务器宣布您正在创建三个新变量。这些变量尚未分配任何值——您将立即为它们赋值。

> 注意 某些语言不要求您在设置变量值之前先声明变量。ColdFusion 和 PHP 都不要求先声明变量，因此它们没有与 Dim 行对应的内容。

到本步骤结束时，ASP 用户的代码窗口应如下屏幕截图所示。ColdFusion 和 PHP 用户，再次强调，在此任务中尚未执行任何操作，但情况即将改变。

![](img/43fd0127a958864ab2d93e28efe683e7_214_0.png)

- 4) 所有用户：将三个变量 numAdult、numChild 和 basePrice 设置为在 numAdults、numChildren 和 tourName 表单字段中输入的值。

在 ASP 中，在 Dim 行后面的空行处插入以下代码：

```
numAdult = Request.Form("numAdults")
numChild = Request.Form("numChildren")
basePrice = Request.Form("tourName")
```

在 ColdFusion 中，在文档顶部、开头 <!DOCTYPE> 标记之前输入以下代码：

```
<cfset numAdult = form.numAdults>
<cfset numChild = form.numChildren>
<cfset basePrice = form.tourName>
```

在 PHP 中，在文档顶部、开头 <!DOCTYPE> 行之前输入以下代码：

```
$numAdult = $_POST['numAdults'];
$numChild = $_POST['numChildren'];
$basePrice = $_POST['tourName'];
```

在之前的课程中，您已经见过 Request.Form("fieldname")、form.fieldname 和 $_POST['fieldname']。此次，与之前直接在页面上打印它们不同，您是将这些值存储在新变量中。这样做的原因是，页面上需要打印的是计算结果。通过使用命名描述性的变量来存储这些值，计算更容易编写（也更易读）。

ColdFusion 用户可能会疑惑，为什么表单变量没有像以前课程中那样用井号（##）括起来。井号仅在 ColdFusion 向外部源（例如 HTML）输出动态值时使用。如果没有井号，ColdFusion 会打印变量名，而不是其值。但在此处不需要井号，因为此操作是在 ColdFusion 内部执行的——它没有向任何位置输出值。

- 5) 设置第四个变量 tourPrice，使其等于计算本身的输出。

在 ASP 中：在 basePrice 行下方插入以下代码：

```
tourPrice = (numAdult * basePrice) + (numChild * basePrice)
```

在 ColdFusion 中，在 basePrice 行下方插入以下代码：

```
<cfset tourPrice = (numAdult * basePrice) + (numChild * basePrice)>
```

在 PHP 中，在 basePrice 行下方插入以下代码：

```
$tourPrice = ($numAdult * $basePrice) + ($numChild * $basePrice);
```

假设您七年级数学及格了，您可能知道这一行在做什么。它将 tourPrice 的值设置为简单计算的输出。括号如同在算术中一样，用于确保计算按正确顺序执行。

当服务器解析此代码行时，tourPrice 的值即为最终计算出的美元金额。有了这个，我们只需要将其输出到 HTML 代码中 XXX 占位符所在的位置，用户就能看到所需的信息。

```
<%@LANGUAGE="VBScript" CODEPAGE="1252" %>
<%
Dim numAdult, numChild, basePrice, tourPrice
numAdult = Request.Form("numAdults")
numChild = Request.Form("numChildren")
basePrice = Request.Form("basePrice")
tourPrice = (numAdult * basePrice) + (numChild * basePrice)
%>

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-t
<html xmlns="http://www.w3.org/1999/xhtml">
```

## 6) 仍在代码视图中，向下滚动到 XXX 占位符（ASP 中大约在第 34 行，ColdFusion 中大约在第 30 行，PHP 中大约在第 33 行）。删除 XXX，并在此处输入以下代码以输出 tourPrice 变量的值。

在 ASP 中：

<% Response.Write(tourPrice) %>

在 ColdFusion 中：

<cfoutput>#tourPrice#</cfoutput>

在 PHP 中：

<?php echo $tourPrice; ?>

输出变量值对您来说现在应该很熟悉了。此次输出变量与您在第 5 课中所做的主要区别在于，您不需要指定 HTTP 兼容的作用域——URL/查询字符串、表单、cookie 等。此变量的作用域是页面本身，在 ASP、ColdFusion 或 PHP 中处理时，该变量会在代码通过 HTTP 发送到浏览器之前被解析并移除。

```
25 </tr>
26 </table>
27 <td><img src="images/nav_bar.gif" name="navbar" width="450" height="20" border="0" usemap="#navbarMap">
28 <td><img name="copyright_bar" src="images/copyright_bar.gif" width="272" height="20" border="0" alt="">
29 </tr>
30 </table>
31 <td colspan="2">
32 <h1><br />
33 <p name="top" id="top"><strong>Tour Price Calculator</strong></p>
34 <p>The estimated cost of your tour is <strong><%= Response.Write(tourPrice) %></strong>.</p>
35 <p>Prices include hotel, accommodation, and travel expenses during the tour. They do not include airf
36 <p><a href="tourprice_processor.asp">Calculate</a> another tour.</p>
37 <p><a href="contact.asp">Contact</a> one of our qualified agents. </p>
38 </div>
39 </td>
40 </table>
```

- 7) 保存并上传 tourprice.asp 和 tourprice_processor.asp 两个文件。在“站点”面板中选择 tourprice.asp，并按 F12 进行测试。

您应始终尽快测试页面的功能。这两个页面已准备好进行测试。您将为这个应用程序添加很多增强功能，但其核心功能已经可以工作——或者应该可以。

尝试多种不同的变体。在每个字段中输入数值，选择一个旅程，然后单击提交。您应该能看到计算出的金额以粗体显示的输出页面。请注意，美元金额会显示出来，但没有任何内容表明它是美元金额。ASP、ColdFusion 和较新版本的 PHP 都具有内置函数，可让您以正确的货币格式输出数字，如您稍后将看到的那样。

![](img/43fd0127a958864ab2d93e28efe683e7_217_0.png)

一旦您验证了在最佳情况下（即正确输入数字时）它能正常工作，就尝试在表单中输入错误数据来使应用程序崩溃。将一个或两个字段留空，或输入一个字母，例如 D。

![](img/43fd0127a958864ab2d93e28efe683e7_217_1.png)

页面要么返回错误消息，要么无论如何都会尝试完成计算，并返回一个无意义的数字。原因是您的脚本会相乘和相加表单字段的内容。如果这些字段没有内容或包含非数字字符，它就无法执行计算。这个应用程序可以从表单验证增强功能中受益，该功能将确保用户在两个字段中都实际输入了数字，然后再尝试计算价格。

## 8) 返回 Dreamweaver 中的 tourprice_processor.asp，并插入将输出数字转换为美元货币格式的函数。

在 ASP 中：

```
<% Response.Write(FormatCurrency(tourPrice)) %>
```

在 ColdFusion 中：

```
<cfoutput>#DollarFormat(tourPrice)#</cfoutput>
```

在 PHP 中：

```
<?php echo number_format($tourPrice, 2, '.', ','); ?>
```

**注意** PHP 4.3 及更高版本有一个 money_format() 函数，但早期版本的 PHP（包括随 Macintosh OS X 附带的版本）中没有此函数。在此上下文中使用 number_format() 的唯一缺点是它不会输出美元符号 ($)。您可以手动添加它，方法是在 <strong>（或者，如果您未更改，则为 <span class="author"> 标签）和 <?php echo... 开始标记之间输入 $。

函数是预定义的操作，用于告诉解释器如何执行某项操作。计算机语言通常为常见任务内置了几十个甚至更多函数。将数字转换为货币格式是一项常见任务，因此许多语言都有执行此任务的函数。

函数采用以下格式：FunctionName(Parameter)。在某些情况下，没有参数，但括号仍然存在，例如 ColdFusion 的 Now() 函数，它返回服务器上的当前时间。在 ASP 的 FormatCurrency() 和 ColdFusion 的 DollarFormat() 中，唯一的参数是您要格式化的数字。由于数字存储在 tourPrice 变量中，您将该变量放在参数中。

PHP 的 number_format() 函数接受四个参数。它们按顺序是：要格式化的数字 ($tourPrice)、允许的小数位数 (2)、用于指示小数点的标点符号 (.) 以及用于分隔千位的标点符号 (,)。由于句点和逗号字符在
