

## 附录 G：实用的自定义函数 521

## UL_LIST()

此函数返回一个 HTML 无序列表（项目符号，`<ul>` 标签）。如果参数是一个数组，则数组中的每个值将作为列表项（`<li>`）包含在列表中。否则，参数将直接包含在 `<ul>` 标签内。

```php
string ul_list(mixed values)
```

## 来自 functions/forms.php

这些函数创建所有常见的表单元素，以及 `<form>` 标签的开始和结束标记。

### START_FORM()

此函数返回一个 HTML `<form>` 标签。如果第一个参数为空，则使用 Apache 变量 `SCRIPT_NAME` 的值作为 `<form>` 标签的 `action` 属性。表单的其他属性可以在可选的第二个参数中指定；表单的默认方法为 "post"。此函数在 Apache 以外的服务器上的行为尚不清楚。它可能可以工作，因为 `SCRIPT_NAME` 是 CGI 1.1 规范的一部分。

```php
string start_form([string action, [array attributes]])
```

### END_FORM()

此函数返回一个结束标签。

```php
string end_form(void)
```

### TEXT_FIELD()

返回一个 HTML `<input type=text>` 表单元素。默认大小为 10。

```php
string text_field([string name, [string value, [int size, int maximum length]]
```

### TEXTAREA_FIELD()

此函数返回一个 HTML 区域字段。默认大小为 50 列 10 行，默认换行模式为 "soft"，这意味着在用户向字段中输入的内容换行时，不会插入硬换行。另一种换行模式是 "hard"，这意味着将插入硬换行符。

```php
string textarea_field([string name, [string value, [int cols, int rows, [string mode]]]])
```

### PASSWORD_FIELD()

此函数返回一个 HTML 密码字段。这类似于文本字段，但字段的值是经过遮蔽的（每个字符只显示星号或圆点）。字段的默认大小为 10。可以提供起始值和最大数据长度。

```php
string password_field ([string name [, string value [, int size [, int maximum length]]])
```

### HIDDEN_FIELD()

此函数返回一个 HTML 隐藏元素。可以提供名称和值。

```php
string hidden_field ([string name [, string value]])
```

### FILE_FIELD()

此函数返回一个 HTML 文件字段元素。

```php
string file_field([string name])
```

此函数返回一个 HTML 文件字段。这些用于指定用户本地驱动器上的文件，通常作为表单的一部分进行上传。（关于此主题的更多信息，请参见 http://www.zendend/manual/features/file-upload.php。）

### SUBMIT_FIELD()

此函数返回一个 HTML 提交字段。字段的值将是用户浏览器显示的按钮字符串。默认值为“Submit”。

```php
string submit_field ([string name [, string value]])
```

### IMAGE_FIELD()

此函数返回一个 HTML 图像字段。图像字段的作用类似于提交字段，不同之处在于显示第二个参数中给出的 URL 图像而不是按钮。

```php
string image_field ([string name [, string src [, string value]])
```

### RESET_FIELD()

此函数返回一个 HTML 重置表单元素。

```php
string reset_field ([string name, [string value]])
```

## 附录 G：实用的自定义函数

## 523

### CHECKBOX_FIELD()

此函数返回一个 HTML 复选框字段。可选参数将紧接在复选框字段之后，并且该对被包含在 HTML `<label>` 标签内——这意味着它们将在同一行显示。如果第二个或第三个参数的值匹配第四个参数的值，则复选框将被“选中”（即开启）。

```php
string checkbox_field ([string name [, string value [, string label [string match]])
```

### RADIO_FIELD()

此函数返回一个单选按钮字段。可选参数将紧接在单选按钮之后，并且该对被包含在 HTML `<label>` 标签内——这意味着它们将显示在同一行。如果第二个或第三个参数的值匹配第四个参数的值，则单选按钮将被“选中”（即开启）。

```php
string radio_field ([string name [, string value [, string label [string match]])
```

### SELECT_FIELD()

此函数返回一个 HTML 选择字段（弹出字段）。如果可选的第二个参数是一个数组，则数组中的每个键都将设置为选择字段选项的值，而数组中对应的值将是该选项的显示字符串。如果数组中的键或值匹配第三个参数，则该选项将被指定为选择字段的默认值。

```php
string select_field ([string, array]])
```

### DB_SELECT_FIELD()

此函数返回一个 HTML 选择字段（弹出字段）。如果可选的第二个参数是一个数组，则数组中的每个键都将设置为选择字段选项的值。

```php
string db_select_field ([string, array]])
```

### DB_RADIO_FIELD()

此函数返回一个 HTML 单选按钮字段。如果可选的第二个参数是一个数组，则数组中的每个键都将设置为单选按钮选项的值。

```php
string db_radio_field ([string, array]])
```

## 这里的 functions/forms.php

这些函数创建所有常见的表单元素，以及 `<form>` 标签的开始和结束标记。

### START_FORM()

此函数返回一个 HTML `<form>` 标签。如果第一个参数为空，则使用 Apache 变量 `SCRIPT_NAME` 的值作为 `<form>` 标签的 `action` 属性。表单的其他属性可以在可选的第二个参数中指定；表单的默认方法为 "post"。此函数在 Apache 以外的服务器上的行为尚不清楚。它可能可以工作，因为 `SCRIPT_NAME` 是 CGI 1.1 规范的一部分。

```php
string start_form([string action, [array attributes]])
```

### END_FORM()

此函数返回一个结束标签。

```php
string end_form(void)
```

### TEXT_FIELD()

返回一个 HTML `<input type=text>` 表单元素。默认大小为 10。

```php
string text_field([string name, [string value, [int size, int maximum length]]
```

### TEXTAREA_FIELD()

此函数返回一个 HTML 区域字段。默认大小为 50 列 10 行，默认换行模式为 "soft"，这意味着在用户向字段中输入的内容换行时，不会插入硬换行。另一种换行模式是 "hard"，这意味着将插入硬换行符。

```php
string textarea_field([string name, [string value, [int cols, int rows, [string mode]]]])
```

### PASSWORD_FIELD()

此函数返回一个 HTML 密码字段。这类似于文本字段，但字段的值是经过遮蔽的（每个字符只显示星号或圆点）。字段的默认大小为 10。可以提供起始值和最大数据长度。

```php
string password_field ([string name [, string value [, int size [, int maximum length]]])
```

### HIDDEN_FIELD()

此函数返回一个 HTML 隐藏元素。可以提供名称和值。

```php
string hidden_field ([string name [, string value]])
```

### FILE_FIELD()

此函数返回一个 HTML 文件字段元素。

```php
string file_field([string name])
```

此函数返回一个 HTML 文件字段。这些用于指定用户本地驱动器上的文件，通常作为表单的一部分进行上传。（关于此主题的更多信息，请参见 http://www.zendend/manual/features/file-upload.php。）

### SUBMIT_FIELD()

此函数返回一个 HTML 提交字段。字段的值将是用户浏览器显示的按钮字符串。默认值为“Submit”。

```php
string submit_field ([string name [, string value]])
```

### IMAGE_FIELD()

此函数返回一个 HTML 图像字段。图像字段的作用类似于提交字段，不同之处在于显示第二个参数中给出的 URL 图像而不是按钮。

```php
string image_field ([string name [, string src [, string value]])
```

### RESET_FIELD()

此函数返回一个 HTML 重置表单元素。

```php
string reset_field ([string name, [string value]])
```

