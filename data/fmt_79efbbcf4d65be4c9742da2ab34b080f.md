
创建错误后，我们就可以开始编写验证。如果密码没有变化，它应该是空字符串。否则，我们需要验证密码长度。我们不需要担心创建用户时密码是否必填，因为稍后我们会编写该验证。

```go
func (uv *validator) passwordMinLength(user *User) error {
  if user.Password == "" {
    return nil
  }
  if len(user.Password) < 8 {
    return ErrPasswordTooShort
  }
  return nil
}
```

我们需要将此添加到 `Update` 和 `Create` 方法中以便于使用，但这是我们执行顺序很重要的验证之一。我们必须在哈希处理密码之前运行此验证，否则密码将被设置为空字符串，导致我们在查看哈希值时无法确定密码的原始长度。

## 12.8. 验证与规范化密码

```go
func (uv *UserValidator) Create(user *User) error {
  err = runUserValFns(user,
  uv.passwordMinLength,
  uv.bcryptPassword,
  uv.setRememberIfUnset,
  uv.hmacEmail,
  uv.normalizeEmail,
  uv.requireEmail,
  uv.emailFormat,
  uv.emailIsAvail)
  // ... 此处保持不变
}
```

```go
func (uv *UserValidator) Update(user *User) error {
  err = runUserValFns(user,
  uv.passwordMinLength,
  uv.bcryptPassword,
  uv.hmacEmail,
  uv.normalizeEmail,
  uv.requireEmail,
  uv.emailFormat,
  uv.emailFormat)
}
```

### 源代码

下面的链接包含了完成后的源码以及本节所有更改代码的差异。

- 已完成 - book.usegolang.com/12.7
- 更改 - book.usegolang.com/12.7-diff

## 12.9. 验证与归一化 Token

现在我们需要开始在用户模型的验证函数中利用这些功能，但在此之前，我们需要额外定义几个错误。我们需要一个当 `remember token` 使用的字节数不足时的错误，还需要一个当 `remember token` 或 `remember token hash` 未设置且为必填项时的错误。我们将这些错误添加到用户模型中。

```
$ atom models/users.go
```

```go
var (
// ErrRememberRequired 当尝试创建或更新用户
// 但未提供用户 remember token 的哈希值时返回
ErrRememberRequired = errors.New("models: remember token " + 
"is required")
// ErrRememberTooShort 当 remember token 长度
// 少于 32 字节时返回
ErrRememberTooShort = errors.New("models: remember token " + 
"must be at least 32 bytes")
)
```

在错误变量和 `NBytes` 函数准备就绪后，我们可以就可以创建验证函数了。我们可以从检查生成 `remember token` 的字节数的函数开始。

由于 `remember token` 并不总是更新的，我们首先需要检查是否提供了 `remember token`。如果没有提供，我们可以假设用户继续使用现有的 `remember token`，并相信如果它真的是错误，其他验证会捕获到它。

假设 `remember token` 正在更改，我们将检查字节数，如果少于 32，则返回错误；否则返回 `nil`。

```go
func (uv *Validator) rememberMinBytes(user *User) error {
	if user.Remember == "" {
		return nil
	}
	n, err := rand.NBytes(user.Remember)
	if err != nil {
		return err
	}
	if n < 32 {
		return ErrRememberTooShort
	}
	return nil
}
```

注意：我们可以写得类似于我们的 `idGreaterThan` 验证器，但我们可能不会频繁更改这个值，因此发现硬编码它效果足够了。

我们稍后会将此添加到 `Update` 和 `Create` 方法中，但首先让我们也写一个函数，确保在更新和创建用户时我们的 `remember hash` 始终被设置。

```go
func (uv *Validator) rememberHashRequired(user *User) error {
	if user.RememberHash == "" {
		return ErrRememberRequired
	}
	return nil
}
```

现在我们可以更新 `Create` 和 `Update` 方法来使用我们的两个新验证器了。确保在对 `remember token` 进行哈希之前调用 `rememberMinBytes` 函数，然后在对 `remember token` 进行哈希的之后调用 `rememberHashRequired` 函数。

```go
func (uv *Validator) Create(user *User) error {
	err := runValErrs(user,
		uv.passwordRequired,
		uv.passwordMinLength,
		uv.bcryptPassword,
		uv.passwordHashRequired,
		uv.setRememberIfUnset,
		uv.rememberMinBytes,
		uv.hashMember,
		uv.rememberHashRequired,
		uv.normalizeEmail,
		uv.requireEmail,
		uv.emailFormat,
		uv.emailIsAvail)
// ... 此部分保持不变
}
```

```go
func (uv *Validator) Update(user *User) error {
	err := runUserValFns(user,
		uv.passwordMinLength,
		uv.bcryptPassword,
		uv.passwordHashRequired,
		uv.rememberBytes,
		uv.hashMember,
		uv.rememberHashRequired,
		uv.normalizeEmail,
		uv.requireEmail,
		uv.emailFormat,
		uv.emailIsAvail)
// ... 此部分保持不变
}
```

到此为止，用户资源的验证编写已经完成。我们以后可能会发现需要创建更多，但目前这足够了。

在此阶段，建议像以前一样，在 `main.go` 中使用 `DestructiveReset` 函数重置数据库，然后重启服务器。你的数据中很可能存储了在 我们制作这些验证之前创建的无效数据，这可能会导致问题。在开发期间，从头开始是一个更安全的选择。

之后请进入下一章，我们将学习如何在 UI 中渲染美观的错误信息。这将比用户在尝试用无效邮箱地址注册时看到一个只带有单个错误信息的白页面要给我们的用户提供好得多的体验。

### 源代码

下面的链接包含了完整的源代码以及本节中所有更改代码的差异（diff）。

- 完成版 - book.usegolang.com/12.9
- 更改版 - book.usegolang.com/12.9-diff

## 第 13 章

## 向终端用户显示错误

我们的应用程序一直在稳步改进，但仍然有一个方面我们做得不足；我们没有花时间编写任何合理的错误处理。

在本章中，我们将关注如何改进错误处理。我们将通过学习 Bootstrap 警告（Alerts）开始，它们是显示错误信息非常有用的设计元素。在我们在应用程序中显示它们之前，我们需要先在空白页面上显示它们。

> http://getbootstrap.com/docs/3.3/alerts

## 13.1. 在 UI 中显示警告

在进入具体的错误之前，我们首先要看的是用于渲染错误信息的 HTML。我们将使用 Bootstrap 框架来实现这一点，特别是可关闭组件。

**Box 13.1. 查看 Bootstrap 文档**

当你有空时，花点时间查看一下 Bootstrap 文档。查看可用的组件，并对所有内容有一个大致的了解。你不需要背诵文档，但对于正在工作的内容，有一个大致的思路很有帮助。当你开始构建 Web 应用程序时，特别是早期版本和原型时，最有效的路径通常是使用现有的 Bootstrap。

警告有四种类型：success、info、warning 和 danger。它们在 UI 中唯一的区别是颜色，默认设置是绿色的，info 是蓝色的，warning 是黄色，danger 是红色，但这些颜色都可以通过 Bootstrap 自定义。

> ^2 https://getbootstrap.com/docs/3.3/alerts#dismissible
> ^3 https://bootstrap.com

## 13.1. 在 UI 中渲染警告

通常用于错误信息。这就是为什么这种类型的警告是红色的。

让我们为警告创建一个 HTML 模板。这应该感觉很熟悉，因为我们过去添加过其他模板。我们将这些代码添加到 layouts 目录下的新文件中，所以我们可以从创建源文件开始。

```
$ atom views/layouts/alert.gohtml
```

一旦我们打开了源文件，下一步是定义警告模板。这样我们就可以在需要显示错误信息的其他视图中调用它。

```html
{{define "alert"}}
<div class="alert alert-danger alert-dismissible"
role="alert">
<button type="button" class="close" data-dismiss="alert"
aria-label="Close">
<span aria-hidden="true">&times;</span>
</button>
<strong>Danger!</strong>出问题了！哦不！
</</div>
{{end}}
```

我们的 `alert.gohtml` 源文件现在只是定义了一个模板，所以如果我们想渲染它，就需要调用该模板。目前最简单的方法是将其添加到我们的布局文件中。

```
$ atom views/layouts/bootstrap.gohtml
```

我们现在不会进行任何错误检查，而是总是渲染警告。这从长远来看不可行，但可以让我们感受到警告在应用程序中的外观，并验证我们的代码是否运行正常。

在你的 Bootstrap 模板 HTML 中查找 `container-fluid` div，并使用下面的代码进行更新。

```
<div class="container-fluid">
  {{template "alert"}}
  {{template "yield" .}}
  {{template "footer"}}
</div>
```

重启服务器，并访问应用程序中的一个页面。我们现在应该能在页面顶部看到一个类似于图 13.1 的红色警报。

![](img/d6be51afcf11b16bf97245d05fb9e635_445_0.png)

图 13.1：我们的网站在顶部显示了 Bootstrap 警报

## 13.2. 渲染动态警报

### 源代码

下方链接包含了完整的源代码以及本节所有更改代码的差异（diff）。

已完成 - book.usegolang.com/13.1

差异 - book.usegolang.com/13.1-diff

## 13.2 渲染动态警报

如果警报只渲染静态数据，那么它们就毫无用处。我们需要能够在警报中插入特定的错误，使其变得有用。

在这一节中，我们将更新警报模板以使用动态数据。我们将从更新警报模板本身开始，因此从打开该源代码开始。

```
$ atom views/layouts/alert.gohtml
```

一旦打开了警报，我们将对其进行检查并决定哪些信息应该动态设置。第一个引人注目的是外部 div 的 "alert-danger" 类。该类决定了我们的警报将是危险（danger）、警告（warning）、信息（info）还是成功（success）警报，我们很有可能应用程序的某个时刻显示成功或信息消息，因此我们应该动态设置它。

鉴于该类决定了错误的严重程度，我倾向于将此变量命名为 `Level`。我们不需要动态设置整个 HTML 类；我们可以在字符串中间插入变量，它最终将创建一个单个 HTML 类。最终结果是用于我们起始 div 的以下这段代码。

## 第 13 章：向最终用户显示错误

```
<div class="alert alert-({.Level}) alert-dismissible" role="alert">
```

接下来的几行定义了一个 HTML 按钮，用于渲染警报右上角的 x，允许用户将其关闭。这些内容都不需要是动态的，所以我们可以跳过。

alert div 内部的最后一段 HTML 是我们在警报内部渲染的消息。这绝对是我们想要动态渲染的内容，因此我们将用 `Message` 变量替换整整行。生成的警报模板如下所示。

```
{{define "alert"}}
<div class="alert alert-({.Level}) alert-dismissible" role="alert">
<button type="button" class="close" data-dismiss="alert"
aria-label="Close">
<span aria-hidden="true">&times;</span>
</button>
{{.Message}}
</div>
{{end}}
```

为了正确渲染此警报，我们需要传递一个同时包含 `Level` 和 `Message` 字段的数据。我们最终会定义一些数据类型来帮助我们渲染视图，但现在，我们将创建一个临时类型，用于渲染我们的警报。我们需要在控制器内部执行此操作，因此我们将临时修改用户的控制器。

```
$ atom controllers/users.go
```

一旦打开了你的源文件，找到 `New` 方法。我们将编辑这个方法，以便我们可以在注册页面上测试我们的警报。

在 `New` 方法内部，我们将从创建一个同时具有 `Level` 和 `Message` 字段的数据类型开始。

## 13.2. 渲染动态警报

```
type Alert struct {
    Level string
    Message string
}
```

接下来，我们想要创建该类型的实例，用于渲染我们的警报。
我们将用一个成功警报而不是危险警报来测试。

```go
alert := Alert{
    Level: "success",
    Message: "Successfully rendered a dynamic alert!",
}
```

最后，我们在渲染视图时，需要将此警报作为数据传递给 `Render` 方法。将这一切整合在一起，你的 `New` 方法应该看起来像代码。

```go
func (u *Users) New(w http.ResponseWriter, r *http.Request) {
    type Alert struct {
        Level string
        Message string
    }
    alert := Alert{
        Level: "success",
        Message: "Successfully rendered a dynamic alert!",
    }
    if err := u.NewView.Render(w, alert); err != nil {
        panic(err)
    }
}
```

我们正要测试我们的警报，但我们需要更新在 Bootstrap 模板中进行的模板调用。

```
$ atom views/layouts/bootstrap.gohtml
```

## 第 13 章：向最终用户显示错误

当我们起初调用警报模板时，我们没有向它传递任何数据。这就是为什么原始调用在模板名称后没有列出任何参数。

```
{{template "alert"}}
```

我们想要传递此警报数据，因此我们将更新该行代码，在末尾包含一个点。该点表示我们正在传递由 Bootstrap 模板提供的所有数据，在这种情况下，恰好只有我们创建的 `Alert`。

```html
<div class="container-fluid">
<!-- 在下方 "alert" 之后添加点 -->
{{template "alert" .}}
{{template "yield" .}}
{{template "footer"}}
</div>
```
