

![](img/1ddec54918a4802eb9b4febec3d4e7f6_262_0.png)

图 9-1

## 工作原理

这个 XHTML 网页包含了你可能遇到的最常见的表单控件类型。首先，创建表单本身：

```
<form action="" method="get">
```

注意，表单是使用 get 方法创建的。这意味着表单字段名称和值将通过 URL 发送到服务器。你很快将了解更多关于 get 和 post 方法的内容。与此同时，空的 action 属性告诉浏览器将表单发回同一页面（web_form.html）。在实际表单中，此属性将包含表单处理脚本的 URL。

接下来，依次创建每个表单控件。大多数控件都有一个 name 属性，它是存储数据的字段名称，以及一个 value 属性，它包含固定的字段值，或者对于允许用户输入自身值的字段，包含默认字段值。你可以将字段名称和字段值视为类似于关联数组的键和值。

大多数控件还有一个包含字段标签的相关 label 元素。此文本向用户描述字段并提示他们在字段中输入数据。每个 label 使用其 for 属性与控件关联，该属性与控件元素中相应的 id 属性匹配。

创建的表单字段包括：

- 文本输入字段 —— 这允许用户输入一行文本。你可以使用 `value` 属性可选地用初始值预填充字段（如果你不想这样做，请为 `value` 属性指定空字符串，或完全省略该属性）：

```
<label for="textField">A text input field</label>
<input type="text" name="textField" id="textField" value="" />
```

- 密码字段 —— 其工作方式类似于文本输入字段，只是输入的文本不会显示。当然，这旨在用于输入密码等敏感信息。同样，你可以使用 `value` 属性预填充字段，但不建议这样做，因为查看网页源代码时可能会泄露密码：

```
<label for="passwordField">A password field</label>
<input type="password" name="passwordField" id="passwordField" value="" />
```

- 复选框字段 —— 这是一个简单的切换开关；它可以是开或关。`value` 属性应包含复选框被选中时将发送到服务器的值（如果未选中复选框，则不会发送任何内容）：

```
<label for="checkboxField">A checkbox field</label>
<input type="checkbox" name="checkboxField" id="checkboxField" value="yes" />
```

你可以通过向 input 标签添加属性 `checked="checked"` 来预选复选框 — 例如：`<input type="checkbox" checked="checked" ... />`。

通过创建具有相同 name 属性的多个复选框字段，你可以允许用户为同一字段选择多个值。（你将在本章后面学习如何处理多个字段值的 PHP 代码。）

- 两个单选按钮字段 —— 单选按钮通常被放置在至少包含两个按钮的组中。组中所有按钮都有相同的 `name` 属性。每个组只能选择一个按钮。与复选框一样，使用 `value` 属性来存储按钮被选中时发送到服务器的值。请注意，`value` 属性对于复选框和单选按钮是必需的，对于其他字段类型是可选的：

```
<label for="radioButtonField1">A radio button field</label>
<input type="radio" name="radioButtonField" id="radioButtonField1" value="radio1" />
<label for="radioButtonField2">Another radio button</label>
<input type="radio" name="radioButtonField" id="radioButtonField2" value="radio2" />
```

你可以使用与预选复选框相同的技术来预选单选按钮。

- 提交按钮 —— 单击此类按钮会将填写好的表单发送到服务器端脚本进行处理。`value` 属性存储显示在按钮内部的文本标签（单击按钮时该值也会发送到服务器）：

```
<label for="submitButton">A submit button</label>
<input type="submit" name="submitButton" id="submitButton" value="Submit Form" />
```

- 重置按钮 —— 此类按钮将所有表单字段重置为其初始值（通常为空）。value 属性包含按钮标签文本：

```
<label for="resetButton">A reset button</label>
<input type="reset" name="resetButton" id="resetButton" value="Reset Form" />
```

- 文件选择字段 —— 这允许用户选择其硬盘上的文件以上传到服务器（参见本章后面的“创建文件上传表单”）。浏览器通常会忽略 value 属性：

```
<label for="fileSelectField">A file select field</label>
<input type="file" name="fileSelectField" id="fileSelectField" value="" />
```

- 隐藏字段 —— 此类字段在页面上不显示；它只是存储 value 属性中指定的文本值。隐藏字段非常适合将额外信息从表单传递到服务器，如你在本章后面所见：

```
<label for="hiddenField">A hidden field</label>
<input type="hidden" name="hiddenField" id="hiddenField" value="" />
```

- 图像字段 —— 其工作方式类似于提交按钮，但允许你使用自己的按钮图形而不是标准的灰色按钮。你使用 src 属性指定按钮图形的 URL，并使用 width 和 height 属性指定图形的宽度和高度（以像素为单位）。与提交按钮一样，value 属性包含单击按钮时发送到服务器的值：

```
<label for="imageField">An image field</label>
<input type="image" name="imageField" id="imageField" value="" src="asterisk.gif" width="23" height="23" />
```

- 推送按钮 —— 此类按钮单击时默认不执行任何操作，但你可以使用 JavaScript 使此类按钮在浏览器中触发各种事件。value 属性指定要在按钮中显示的文本标签：

```
<label for="pushButton">A push button</label>
<input type="button" name="pushButton" id="pushButton" value="Click Me" />
```

- 下拉菜单 —— 这允许用户从预定义的选项列表中选择单个项目。size 属性值为 1 告诉浏览器你希望列表以下拉菜单格式显示。在 select 元素内，为每个选项创建一个 option 元素。将选项标签放置在 <option> ... </option> 标签之间。每个 option 元素可以有一个可选的 value 属性，它是选择该选项时发送到服务器的值。如果不包含 value 属性，则改为发送 <option> ... </option> 标签之间的文本：

```
<label for="pullDownMenu">A pull-down menu</label>
<select name="pullDownMenu" id="pullDownMenu" size="1">
  <option value="option1">Option 1</option>
  <option value="option2">Option 2</option>
  <option value="option3">Option 3</option>
</select>
```

- 列表框 —— 其工作方式与下拉菜单完全相同，但一次显示多个选项。要将下拉菜单转换为列表框，请将 size 属性从 1 更改为要一次显示的选项数量：

```
<label for="listBox">A list box</label>
<select name="listBox" id="listBox" size="3">
  <option value="option1">Option 1</option>
  <option value="option2">Option 2</option>
  <option value="option3">Option 3</option>
</select>
```

- 多选列表框 —— 其工作方式类似于列表框，但还允许用户通过按住 Ctrl（Windows 和 Linux 浏览器）或 Command（Mac 浏览器）一次选择多个项目。要将普通列表框转换为多选框，请向 select 元素添加多选属性（值为 "multiple"）。如果用户选择多个选项，所有选定的值都将发送到服务器（你将在本章后面学习如何处理多个字段值）：

```
<label for="multiListBox">A multi-select list box</label>
<select name="multiListBox" id="multiListBox" size="3" multiple="multiple">
  <option value="option1">Option 1</option>
  <option value="option2">Option 2</option>
  <option value="option3">Option 3</option>
</select>
```

你可以通过向相关 <option> 标签添加属性 selected="selected" 来预选任何类型的 select 元素中的选项 — 例如：<option value="option1" selected="selected">。

- 文本区域字段 —— 这类似于文本输入字段，但允许用户输入多行文本。与大多数其他控件不同，你通过将文本放置在 <textarea> ... </textarea> 标签之间（而不是在 value 属性中）来指定初始值（如果有）。textarea 元素必须包含控件高度（以行为单位，rows）和宽度（以列为单位，cols）的属性：

```
<label for="textAreaField">A text area field</label>
<textarea name="textAreaField" id="textAreaField" rows="4" cols="50"></textarea>
```

一旦将控件添加到表单中，只需关闭表单元素即可：

```
</form>
```

