

## MySQL/PHP 数据库应用程序电子书版本，第二版

本书的完整文本位于光盘中，格式为 Adobe 的可移植文档格式 (PDF)。您可以使用 Adobe Acrobat Reader（也包含在光盘中）阅读和搜索该文件。

## 故障排除

如果您在安装或使用伴随光盘上的任何材料时遇到困难，请尝试以下解决方案：

- 关闭您可能正在运行的任何防病毒软件 – 安装程序有时会模拟病毒活动，并可能导致您的计算机错误地认为其正在受到病毒感染。（请务必稍后重新打开防病毒软件。）

- 关闭所有正在运行的程序 – 您运行的程序越多，可供其他程序使用的内存就越少。安装程序通常还会更新文件和程序；如果您保持其他程序运行，安装可能无法正常工作。

- 参阅 ReadMe – 请参阅位于 CD-ROM 根目录中的 ReadMe 文件，以获取出版时的最新产品信息。

如果您在使用 CD-ROM 时仍然遇到问题，请致电 Wiley 产品技术支持电话号码：(800) 762-2974。美国境外，请致电 1(317) 572-3994。您也可以通过 www.wiley.com/techsupport 联系 Wiley 产品技术支持。Wiley 出版社仅针对安装和其他一般质量控制事项提供技术支持；对于应用程序本身的技术支持，请咨询程序的供应商或作者。

如需下单或索取其他 Wiley 产品的信息，请致电 (800) 225-5945。

## 附录 B

### HTML 表单

如果您希望应用程序能够接收用户数据，就需要为用户提供一个输入数据的地方。这就需要 HTML 表单（或者，如果您想要花哨些，也可以使用 PDF 文件或 Macromedia Flash 应用程序，但那些是另外的话题）。HTML 表单足够容易使用。有几种常用的输入类型可供选择，在使用 HTML 4.0 和层叠样式表的浏览器中，您可以使用某些技巧让表单看起来更花哨一些。关于表单能做的所有事情的完整讨论已超出本书的范围。如果您需要更多关于表单及其如何与 CSS 或 JavaScript 配合使用，或者关于某些较新的浏览器特定表单类型的信息，请查阅 http://microsoft.com 或 http://mozilla.org 上的文档。另一个关于不同标签和属性在不同浏览器中如何工作的问题的绝佳资源是 Index DOT Html 网站，http://www.blooberry.com/indexdot/html/。您可以在 http://www.w3.org/MarkUp/ 上找到官方文档。

### 表单基础

每个表单由开始和结束的 `<form>` 标签界定。`<form>` 标签接受以下属性：

- action – 此属性指定表单将被发送到进行处理的页面的 URL。它可以包含相对 URL（例如 myscript.php 或 ../myfolder/myscript）或完整 URL（例如 http://www.mydomain/myscript.php）。

- method – 此属性指示浏览器将发送到服务器的 HTTP 请求类型。它必须设置为 GET 或 POST。如果将其设置为 GET，名称/值对将出现在浏览器的地址栏中（例如 http://mypage.com?name1=value1&name2=value2）。使用 GET 的优点是结果可以在浏览器中加书签，且调试更容易。缺点是您发送的变量会更加透明。如果将 method 属性设置为 POST，名称/值对将不可见。此属性的默认值为 GET。

- name – 此属性最适合通过 JavaScript 寻址表单的部分，尽管它也可用于 CGI 应用程序。提交表单时，表单名称不会发送到服务器。

- enctype – 此属性的默认值为 application/x-www-form-urlencoded，通常这没问题。但如果您正在上传文件（使用 `<input type="file">`），则应使用 multipart/form-data。

一个典型的表单外壳看起来如下：

```
<form name="myform" action="processor.php" method="POST">
?
</form>
```

### 输入类型

表单中的大部分工作将由输入类型完成。输入标签和 type 属性决定在浏览器中渲染哪种表单元素。

每个表单字段都必须有一个 name 属性。您给表单字段的名称由 PHP 用于识别放置在其中的值。请参见紧随其后的代码示例以获取具体示例。（要完全准确地说，您不需要为提交和重置按钮提供 name 属性，但这样做可以更轻松地从表单元素中检索值。否则，您将不得不通过数组位置来完成。）

作为快速示例，以下内容将创建一个带有单个文本框和提交按钮的简单表单。文本框的默认值为“hello there”，如图 B-1 所示。

```
<form>
<input type="text" size="50" maxlength="15"
value="hello there"><br>
<input type="submit" name="submit" value="OK?">
</form>
```

输入类型如下。请注意，不同的输入类型具有与其关联的不同属性。每个都接受 name 属性。

- text — 此类型在前面的示例中显示。它可以接受这些属性：

  - size—指示在 Web 浏览器中渲染的框的长度。

  - maxlength—限制可以输入到字段中的字符数量。请记住，旧浏览器会忽略 maxlength；即使在较新的浏览器中，也不应依赖此属性来限制上传。

  - value—框中的默认值。用户可以通过键入不同信息来覆盖它。

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_608_0.png)

图 B-1：简单的 HTML 表单

- password – 此类型与文本字段相同，只是键入框中的文本显示为星号。

- hidden – 此类型不在屏幕上渲染。它在页面之间传递值时非常有用。使用隐藏字段时，只需要 name 和 value 属性；如果您对 Cookie 或会话不放心，请考虑使用它们。请注意，精通技术的用户只需查看网页源代码即可看到您的隐藏表单元素。请勿将任何敏感数据放入隐藏表单字段中。

- submit – 在页面上放置一个提交按钮。value 属性中的文本将出现在提交按钮上。提交表单时，提交按钮的名称和值会与所有其他表单元素一起传递。如果您为所有提交按钮都使用名称/值对，则在单个表单中拥有多个提交按钮会有额外的灵活性。

- image – 与提交按钮服务于相同的目的，但它允许您指定要使用的图像，而不是那个丑陋的旧提交按钮。像对待任何 `` 标签一样对待此表单元素。同时提供 src 和 alt 属性。如果您使用图像映射（即单击同一图像的不同区域具有不同的功能意义），则可以通过 name_x 和 name_y 访问单击的坐标。

- reset — 此表单字段创建一个按钮，按下后将表单恢复到页面加载时的状态。用户输入到表单中的任何数据都将被清除。

- file—允许用户将文件从其计算机发送到远程服务器。该字段看起来很像一个文本框，旁边放置了一个标记为“Browse”的按钮。当用户按下 Browse 按钮时，将显示一个文件选择对话框。用户可以为每个文件上传表单字段选择一个文件。一个表单可以有多个文件上传字段。使用此输入类型时，请务必将表单 enctype 属性更改为 multipart/form-data。有关使用 PHP 进行文件上传的讨论，请参见第 12 章。

- checkbox—只有在提交表单时复选框被选中时，才会传递复选框的名称和值。如果标签中出现单词“checked”，则复选框将默认被选中。请记住使用 name=box_name[] 将多个复选框作为数组传递。有关使用 PHP 传递数组的讨论，请参见第 4 章。

- radio—允许用户在多个选项中只选择一个。具有相同 name 属性的单选按钮属于同一组。checked 属性表示默认选择。

下一个表单使用了我们刚才介绍的所有表单元素，但 image 类型除外。图 B-2 显示了它在浏览器中的渲染方式。

```html
<h2>Please Enter Personal Information</h2>
<form>
<input type="text" size="25" maxlength="15" name="name"
value="Name Here"><br>
<input type="password" size="25" maxlength="15" name="password"
value=""><br>
<input type="hidden" value="you can't see me">
<input type="checkbox" name="telemarket" value="yes" checked>If
checked, I have permission to clear out your bank account.
<p>
<b>What is your eye color?</b><br>
<input type="radio" name="eye_color" value="blue"
checked>blue<br>
<input type="radio" name="eye_color" value="green">green<br>
<input type="radio" name="eye_color" value="brown">brown<br>
<input type="radio" name="eye_color" value="red">red<br>
<input type="submit" name="submit" value="submit"> &nbsp; &nbsp;
<input type="Reset">
</form>
```

