

![](img/c3e650db0d8dfdecc0f8e34a67719f65_201_0.png)

## 其他信息

### PostFormValue 方法

`net/http` 包还提供了 `r.PostFormValue()` 方法，这本质上是一个快捷函数，它会为你调用 `r.ParseForm()`，然后从 `r.PostForm` 中获取相应的字段值。

我建议避免使用这个快捷方式，因为它会静默忽略 `r.ParseForm()` 返回的任何错误。如果使用它，解析步骤可能会遇到错误并导致用户请求失败，但没有反馈机制来让他们（或你）知道问题。

### 多值字段

严格来说，本章使用的 `r.PostForm.Get()` 方法只返回特定表单字段的第一个值。这意味着你无法将其用于可能发送多个值的表单字段，例如一组复选框。

```
<input type="checkbox" name="items" value="foo"> Foo
<input type="checkbox" name="items" value="bar"> Bar
<input type="checkbox" name="items" value="baz"> Baz
```

在这种情况下，你需要直接操作 `r.PostForm` 映射。`r.PostForm` 映射的底层类型是 `url.Values`，而 `url.Values` 的底层类型又是 `map[string][]string`。因此，对于具有多个值的字段，你可以遍历底层映射来访问它们，如下所示：

```
for i, item := range r.PostForm["items"] {
	fmt.Fprintf(w, "%d: Item %s\n", i, item)
}
```

## 限制表单大小

默认情况下，使用 POST 方法提交的表单数据大小限制为 10MB。例外情况是，如果表单具有 enctype="multipart/form-data" 属性且正在发送多部分数据，则没有默认限制。

如果要更改 10MB 限制，可以像这样使用 `http.MaxBytesReader()` 函数：

```
// Limit the request body size to 4096 bytes
r.Body = http.MaxBytesReader(w, r.Body, 4096)

err := r.ParseForm()
if err != nil {
	http.Error(w, "Bad Request", http.StatusBadRequest)
	return
}
```

使用这段代码，在 r.ParseForm() 期间只会读取请求体的前 4096 字节。尝试读取超出此限制会导致 MaxBytesReader 返回错误，随后会由 r.ParseForm() 抛出。

此外——如果达到限制——MaxBytesReader 会在 http.ResponseWriter 上设置一个标志，指示服务器关闭底层 TCP 连接。

## 查询字符串参数

如果你有一个使用 HTTP GET 方法（而非 POST）提交数据的表单，则表单数据将作为 URL 查询字符串参数包含在内。例如，如果你有一个如下所示的 HTML 表单：

```
<form action='/foo/bar' method='GET'>
<input type='text' name='title'>
<input type='text' name='content'>
<input type='submit' value='Submit'>
</form>
```

提交表单时，它将发送一个 URL 如下所示的 GET 请求：
/foo/bar?title=value&content=value.

你可以在处理程序中通过 `r.URL.Query().Get()` 方法获取查询字符串参数的值。这将始终返回参数的字符串值，如果不存在匹配参数，则返回空字符串 ""。例如：

```
func exampleHandler(w http.ResponseWriter, r *http.Request) {
title := r.URL.Query().Get("title")
content := r.URL.Query().Get("content")
...
}
```

### r.Form 映射

访问查询字符串参数的另一种方式是通过 `r.Form` 映射。这与本章使用的 `r.PostForm` 映射类似，不同之处在于它包含任何 POST 请求正文和任何查询字符串参数中的表单数据。

假设你的处理程序中有如下所示的代码：

```
err := r.ParseForm()
if err != nil {
http.Error(w, "Bad Request", http.StatusBadRequest)
return
}

title := r.Form.Get("title")
```

在这段代码中，`r.Form.Get("title")` 行将从 POST 请求正文或名为 title 的查询字符串参数中返回 title 值。如果发生冲突，请求正文的值将优先于查询字符串参数。

如果希望你的应用程序不关心数据值是如何传递给它的，使用 `r.Form` 会非常有帮助。但在该场景之外，`r.Form` 没有任何优势，通过 `r.PostForm` 从 POST 请求正文读取数据或通过 `r.URL.Query().Get()` 从查询字符串参数读取数据，读起来更清晰、更明确。

## 验证表单数据

目前我们的代码有一个明显的问题：我们根本没有以任何方式验证来自表单的（不可信）用户输入。我们应该这样做，以确保表单数据存在、类型正确，并符合我们的任何业务规则。

具体来说，对于这个表单我们希望：

- 检查 title 和 content 字段不为空。
- 检查 title 字段长度不超过 100 个字符。
- 检查 expires 值是否完全匹配我们允许的值之一（1、7 或 365 天）。

使用一些 if 语句以及 Go 的 strings 和 unicode/utf8 包中的各种函数，实现所有这些检查都相当简单。

打开 handlers.go 文件，并更新 snippetCreatePost 处理程序以包含相应的验证规则，如下所示：

```
File: cmd/web/handlers.go

package main

import (
	"errors"
	"fmt"
	"net/http"
	"strconv"
	"strings" // New import
	"unicode/utf8" // New import

	"snippetbox.alexedwards.net/internal/models"
)

...

func (app *application) snippetCreatePost(w http.ResponseWriter, r *http.Request) {
	err := r.ParseForm()
	if err != nil {
		app.clientError(w, http.StatusBadRequest)
		return
	}

	title := r.PostForm.Get("title")
	content := r.PostForm.Get("content")

	expires, err := strconv.Atoi(r.PostForm.Get("expires"))
	if err != nil {
		app.clientError(w, http.StatusBadRequest)
		return
	}

// Initialize a map to hold any validation errors for the form fields.
fieldErrors := make(map[string]string)

// Check that the title value is not blank and is not more than 100
// characters long. If it fails either of those checks, add a message to the
// errors map using the field name as the key.
if strings.TrimSpace(title) == "" {
    fieldErrors["title"] = "This field cannot be blank"
} else if utf8.RuneCountInString(title) > 100 {
    fieldErrors["title"] = "This field cannot be more than 100 characters long"
}

// Check that the Content value isn't blank.
if strings.TrimSpace(content) == "" {
    fieldErrors["content"] = "This field cannot be blank"
}

// Check the expires value matches one of the permitted values (1, 7 or
// 365).
if expires != 1 && expires != 7 && expires != 365 {
    fieldErrors["expires"] = "This field must equal 1, 7 or 365"
}

// If there are any errors, dump them in a plain text HTTP response and
// return from the handler.
if len(fieldErrors) > 0 {
    fmt.Fprint(w, fieldErrors)
    return
}

id, err := app.snippets.Insert(title, content, expires)
if err != nil {
    app.serverError(w, r, err)
    return
}

http.Redirect(w, r, fmt.Sprintf("/snippet/view/%d", id), http.StatusSeeOther)
}
```

**注意：** 在检查 `title` 字段长度时，我们使用的是 `utf8.RuneCountInString()` 函数，而不是 Go 的 `len()` 函数。这将统计 title 中 *Unicode 代码点* 的数量，而不是字节数。为了说明区别，字符串 "Zoë" 包含 3 个 Unicode 代码点，但由于带变音符号的 ë 字符，占用 4 个字节。

好了，让我们试一下！重启应用程序，尝试提交带有过长的代码片段标题和空白内容字段的表单，大致如下...

## Snippetbox

首页 创建代码片段

标题：

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec malesuada pretium orci

内容：

- 删除时间：一年 一周 一天

发布代码片段

你应该会看到类似下面的适当验证失败消息转储：

map[content:This field cannot be blank title:This field cannot be more than 100 characters long]

提示：你可以在这篇博文中找到大量处理和验证不同类型输入的代码模式。

