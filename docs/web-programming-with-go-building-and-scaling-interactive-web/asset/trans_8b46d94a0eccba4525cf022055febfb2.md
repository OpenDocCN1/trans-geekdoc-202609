

# 处理表单和用户输入

Web 应用程序接收和处理用户输入的能力是其交互性的基础。为了促进这种交互，表单充当了桥梁，使用户能够提交数据。这些数据可用于各种目的，包括注册帐户、提供反馈或下订单。预计表单将在 GitforGits 书店捕获用户偏好、订单和评论的过程中发挥重要作用。

## 奠定基础

Web 表单主要使用 HTML `<form>` 元素创建。在此元素中，各种输入元素，例如文本字段（`<input>`）、复选框、单选按钮和下拉列表，用于捕获数据。当表单提交时，这些字段中输入的数据将发送到服务器。

考虑书店的用户注册表单。此类表单将捕获用户名、电子邮件、密码以及可能的用户偏好等基本详细信息。以下是它可能的样子：

```html
<form action="/register" method="post">
    <label for="username">Username:</label>
    <input type="text" id="username" name="username">
    <label for="email">Email:</label>
    <input type="email" id="email" name="email">
    <label for="password">Password:</label>
    <input type="password" id="password" name="password">
    <input type="submit" value="Register">
</form>
```

## 下拉列表、单选按钮和复选框

除了简单的文本输入外，表单还可以包含允许用户进行选择的元素。假设 GitforGits 书店提供一项功能，让用户设置他们感兴趣的类型偏好。下拉列表、单选按钮和复选框将是合适的选择。

```html
<label for="favGenre">Favorite Genre:</label>
<select id="favGenre" name="favGenre">
    <option value="fiction">Fiction</option>
    <option value="non-fiction">Non-Fiction</option>
    <option value="sci-fi">Science Fiction</option>
</select>
<label>Preferred Authors:</label>
<input type="checkbox" id="author1" name="author1" value="Author One">
<label for="author1">Author One</label>
<input type="checkbox" id="author2" name="author2" value="Author Two">
<label for="author2">Author Two</label>
```

## 验证

确保用户提供有效输入至关重要。HTML5 提供了内置验证功能，例如必填字段和模式匹配。例如，电子邮件输入类型将检查有效的电子邮件格式。添加 `required` 属性将确保字段不为空。

```html
<input type="email" id="email" name="email" required>
```

## 处理表单数据

一旦表单提交，服务器需要处理输入数据。使用 Go，`net/http` 包使这项任务变得简单。`Request` 对象包含表单数据，可以轻松解析和处理。

现在，一旦注册表单提交，服务器可以使用以下方式提取表单数据：

```go
username := r.FormValue("username")
email := r.FormValue("email")
password := r.FormValue("password")
```

向 GitforGits 书店添加表单增强了其交互性和以用户为中心的方法。可以保证，用户始终会感到被倾听，他们的偏好将得到尊重，并且他们的数据将是安全的，这要归功于通过表单发起的对话，并由 Go 的处理能力支持。

# 模板缓存

## 概述

想象一下，你去 GitforGits，发现每翻一页，商店的布局就完全重新排列一次。你觉得恼火，不是吗？现代 Web 应用程序中也会发生类似的现象，因为模板是针对每个用户请求从头开始解析和加载的。这不仅会浪费计算资源，还会导致滞后，从而降低用户体验质量。就本学习而言，模板缓存可比作在实体店中建立稳定的平面布局，它保证了统一性，并方便每位客户快速导航。

模板缓存的简单解释是，它涉及将预解析的模板存储在内存中。这使得它们可以随时用于后续请求，而无需重新解析，而重新解析是一种开销。这种机制显著提高了服务器的响应时间，并保证最终用户能够及时收到内容。

## Go 的模板包

Go 的 `html/template` 包擅长解析和存储模板。通常，在渲染响应时，人们可能会使用 `template.ParseFiles()` 或 `template.ParseGlob()` 即时解析。虽然有效，但如果对每个请求都重复此操作，则计算密集。与其在处理程序函数中解析模板，不如在应用程序启动时执行解析。这样做，会创建一个已解析模板的缓存，将其保存在内存中，并随时可供使用。

```go
var templateCache = template.New("").Delims("{{", "}}")
func LoadTemplates() {
    templates, err := templateCache.ParseGlob("./templates/*.gohtml")
    if err != nil {
        log.Fatal(err)
    }
    templateCache = templates
}
```

在此代码片段中，`LoadTemplates` 函数将已解析的模板填充到全局 `templateCache` 中。通过在应用程序启动时调用此函数，已解析的模板将在整个应用程序生命周期内随时可用。

## 部署缓存的模板

有了缓存，渲染响应就变成了一个精简的过程。假设用户访问 GitforGits 上的图书列表：

```go
func BookListHandler(w http.ResponseWriter, r *http.Request) {
    books := fetchBooks()
    err := templateCache.ExecuteTemplate(w, "booklist.gohtml", books)
    if err != nil {
        http.Error(w, "Internal Server Error", http.StatusInternalServerError)
    }
}
```

在 `BookListHandler` 中，处理程序不是重新解析模板，而是直接调用 `templateCache`，使用预解析的 `"booklist.gohtml"` 模板快速处理请求。

模板缓存的结果是多方面的：

* 通过消除解析开销，响应时间得到显著提升。
* 减少冗余操作可确保高效的 CPU 利用率。
* 使用集中式缓存可防止因在应用程序的各个部分解析模板而可能出现的不一致性。

但是，虽然缓存增强了生产性能，但在开发阶段，它可能会掩盖对模板所做的更改，因为缓存保留了最初解析的版本。开发人员必须刷新缓存才能查看更新。

