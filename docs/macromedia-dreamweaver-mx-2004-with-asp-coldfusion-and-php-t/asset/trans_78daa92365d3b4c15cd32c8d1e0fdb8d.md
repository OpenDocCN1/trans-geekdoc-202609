

同样，这会释放服务器上的内存，一旦您的页面不再需要该记录集。

### 5) 在代码视图中，找到countryName表单元素。为其提供一个value属性，如下所示：

```
value="XX"
```

这是标准HTML，因此对于ASP、ColdFusion和PHP都是相同的。如果现在测试页面，字母XX将出现在“Country Name”字段中。

> **提示** 如果在课程中测试此页面，请记住它期望一个querystringURL参数。如果未提供（按F12时从不提供），您将看到错误。要解决此问题，在浏览器地址/位置栏中的URL末尾，键入以下内容：?countryID=3 然后按Enter/Return。这样做会为查询运行提供必要的信息，错误将被消除。

### 6) 将XX占位符替换为动态值，如下所示：

In ASP：

```
<%=rs_countryDetail("countryName")%>
```

In ColdFusion：

```
<cfoutput>#rs_countryDetail.countryName#</cfoutput>
```

In PHP：

```
<?php echo $row_rs_countryDetail['countryName']; ?>
```

这样一来，当页面加载时，正确的国家名称将默认出现在字段中。如果用户对其进行修改，则国家名称将在数据库中更新。如果用户未做任何更改，那么从严格意义上讲，表单值仍将替换数据库中的值，但由于它们相同，因此不会有任何变化。

![](img/43fd0127a958864ab2d93e28efe683e7_488_0.png)

### 7) 使用正确的ASP、ColdFusion或PHP语法，对其余每个文本字段元素重复步骤5和6，使用以下信息（以伪代码提供）：

人口：rs_countryDetail.population

国家货币：rs_countryDetail.country_currency

图片URL：rs_countryDetail.imageURL，

现在，四个文本字段已准备就绪。您仍需处理两个文本区域。

![](img/43fd0127a958864ab2d93e28efe683e7_489_0.png)

### 8) 在description和imageALT的两组<textarea></textarea>开始和结束标签之间，插入将动态数据作为其默认值输出所需的代码。

In ASP：

```
<%=rs_countryDetail("description")%>
<%=rs_countryDetail("imageALT")%>
```

In ColdFusion：

```
<cfoutput>#rs_countryDetail.description#</cfoutput>
<cfoutput>#rs_countryDetail.imageALT#</cfoutput>
```

In PHP：

```
<?php echo $row_rs_countryDetail['description']; ?>
<?php echo $row_rs_countryDetail['imageALT']; ?>
```

![](img/43fd0127a958864ab2d93e28efe683e7_489_1.png)

<textarea>标签使用的语法与其他表单元素标签略有不同。它没有value属性，而是将默认值放在开始标签和结束标签之间。不过，ASP、ColdFusion或PHP代码的语法是相同的。

完成后，保存并上传文件以便进行测试。

### 9) 在“站点”面板中选择admin_cp_master.asp，登录，然后单击选择任何非非洲国家。

![](img/43fd0127a958864ab2d93e28efe683e7_490_0.png)

更新表单将出现，所有默认值均已提供。但是，只要您选择了非非洲国家，就会看到一个问题：该国家的区域列为非洲。这是因为不同的记录集(rs_regions)正在填充下拉菜单，而非洲是记录集中的第一个区域，因此默认显示。您可以更改菜单，使其显示rs_countryDetail的数据，但由于该记录集只有一条记录，只会显示一个区域，从而无法更改区域。虽然意大利不太可能搬到南美洲，但您应该保留更改区域的灵活性，以防万一Newland Tours的某人决定使用不同于大洲的区域划分逻辑，例如北欧和南欧，而不仅仅是欧洲。

您可能会考虑要求员工每次根据需要更改此下拉菜单，但这属于糟糕的易用性。迟早，员工会忘记更改它，那么墨西哥等国家将被列为非洲。此错误的后果是重大的：请记住，用户可以按区域搜索，因此如果他们在中美洲下搜索，将看不到墨西哥。如果一家旅行社宣称墨西哥在非洲，设想一下它将遭受的信誉打击！这是一个需要解决的问题。

但是，解决方案需要一些工作。目前，发送到浏览器的（即在经过ASP、ColdFusion或PHP解释器处理后）此菜单元素的代码如下所示：

```
<select name="region" id="region">
<option value="6">Africa</option>
<option value="8">America, Central</option>
<option value="1">America, North</option>
<option value="2">America, South</option>
<option value="7">Asia, Central</option>
<option value="4">Asia, East</option>
<option value="5">Asia, West</option>
<option value="3">Europe</option>
</select>
```

如您所知，<select>元素有一个附加属性selected，可用于指定哪个项目默认显示。因此，在以下列表中，Asia, Central将是浏览器中默认显示的元素（应用了加粗以便更容易发现更改）。

```
<select name="region" id="region">
<option value="6">Africa</option>
<option value="8">America, Central</option>
<option value="1">America, North</option>
<option value="2">America, South</option>
<option value="7" selected>Asia, Central</option>
<option value="4">Asia, East</option>
<option value="5">Asia, West</option>
<option value="3">Europe</option>
</select>
```

因此，您需要做的是将单词selected插入到对应于活动国家的区域的代码中。现在，您面临的复杂情况是，您的菜单不是硬编码的，而是由一个循环填充的，该循环为rs_regions记录集中的每条记录插入一行新的<option>。

问题的解决方案如下：每次遍历填充下拉菜单的循环时，脚本都会测试当前记录的regionID是否与rs_countryDetail记录集中的区域匹配。如果匹配，脚本将把单词selected输出到代码中。如果不匹配，脚本将按常规继续。伪代码中的块如下所示：

```
Loop the following code until rs_regions runs out of records
Write the <option> line, using rs_regions.regionID as the value attribute,
=>and rs_regions.regionName as the label
If the active rs_regions.regionID equals rs_countryDetail.region
Write the word "selected" into the code
End If
```

返回循环开头并开始下一次迭代

从概念上讲，这需要吸收很多内容，但一旦您理解了这个想法，实际编写代码并不难。

### 10) 更新region之间开始和结束<select></select>标签中的代码，如下所示：

In ASP：

```
<%
 Do Until rs_regions.EOF
%>
<option value="<%=rs_regions("regionID")%>"
<%
 If rs_regions("regionID")=rs_countryDetail("region") Then
 Response.Write(" selected")
 End If
%>
><%=rs_regions("regionName")%></option>
<%
 rs_regions.MoveNext
 Loop
%>
```

In ColdFusion：

```
<cfoutput query="rs_regions">
 <option value="#regionID#"<cfif (rs_regions.regionID EQ rs_countryDetail.region)> selected</cfif>>#regionName#</option>
</cfoutput>
```

In PHP：

```
<?php
 do {
 ?>
 <option value="<?php echo $row_rs_regions['regionID']; ?>"
 <?php
 if ($row_rs_regions['regionID'] == $row_rs_countryDetail['region']) {
 echo " selected";
 }
 ?>
><?php echo $row_rs_regions['regionName']; ?></option>
 <?php
 } while ($row_rs_regions = mysql_fetch_assoc($rs_regions));
 ?>
```

我将`<option>`标签的开始部分和结束部分加粗，只是为了使其更易于阅读——特别是闭合尖括号(`>`)，在ASP、ColdFusion和PHP中看起来像是孤立的。（顺便说一句，在所有三种服务器模型的代码编辑器中，该括号应为橙色。）之所以这样做，是因为`selected`必须写在该闭合括号之前，因此该括号本身位于`if`部分代码的右侧，而其余标签位于`if`部分代码的左侧。

```
63     <td name="region">"region"</td>
64     <%
65     Do Until rs_regions.EOF
66     <%
67     <% Response.Write "<" & rs_regions("regionID") & ">" %>
68     <%
69     If rs_regions("regionID") = rs_countryDetail("region") Then
70     Response.Write(" selected")
71     End If
72     %>
73     <% =rs_regions("regionName") %></option>
74     <%
75     rs_regions.MoveNext
76     Loop
77     %>
78
```

键入此代码时，请仔细注意间距——在`selected`之前必须有一个空格，以免它与前面的value="X"连在一起。

ASP和PHP用户可能会注意到，此部分用于`<option>`语句的语法与您在课程开始时构建的插入表单中的菜单不同。它不是使用单个ASP/PHP块来串联多个元素来构建`<option>`行，而是使用多个ASP/PHP块，使用ASP分隔符(`<%...%>`)或PHP分隔符(`<?...?>`)。此更改没有功能影响。主要区别是，一旦您添加了`if`部分，像这样拆分后，代码更容易理解。

### 11) 保存并上传文件。测试admin_cp_master.asp，并像之前一样选择一个非非洲国家。

正确的区域将默认选定，但所有其他区域仍然可用。

