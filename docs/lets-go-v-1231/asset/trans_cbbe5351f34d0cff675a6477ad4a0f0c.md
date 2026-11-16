

## 显示错误并重新填充字段

现在 snippetCreate 处理程序正在验证数据，下一步是优雅地管理这些验证错误。

如果存在任何验证错误，我们希望重新显示 HTML 表单，突出显示验证失败的字段，并自动重新填充之前提交的任何数据（这样用户就不需要再次输入了）。

要做到这一点，让我们先向 templateData 结构体添加一个新的 Form 字段：

File: cmd/web/templates.go

```go
package main

import (
	"html/template"
	"path/filepath"
	"time"

	"snippetbox.alexedwards.net/internal/models"
)

// Add a Form field with the type "any".
type templateData struct {
	CurrentYear int
	Snippet     models.Snippet
	Snippets    []models.Snippet
	Form        any
}

...
```

我们将使用此 Form 字段在重新显示表单时将验证错误和之前提交的数据传回模板。

接下来，让我们回到 cmd/web/handlers.go 文件，定义一个新的 snippetCreateForm 结构体来保存表单数据和任何验证错误，并更新 snippetCreatePost 处理程序以使用它。

如下所示：

File: cmd/web/handlers.go

```go
package main

...

// Define a snippetCreateForm struct to represent the form data and validation
// errors for the form fields. Note that all the struct fields are deliberately
// exported (i.e. start with a capital letter). This is because struct fields
// must be exported in order to be read by the html/template package when
// rendering the template.
type snippetCreateForm struct {
	Title   string
	Content string
	Expires int
	FieldErrors map[string]string
}

func (app *application) snippetCreatePost(w http.ResponseWriter, r *http.Request) {
	err := r.ParseForm()
	if err != nil {
		app.clientError(w, http.StatusBadRequest)
		return
	}

	// Get the expires value from the form as normal.
	expires, err := strconv.Atoi(r.PostForm.Get("expires"))
	if err != nil {
		app.clientError(w, http.StatusBadRequest)
		return
	}

	// Create an instance of the snippetCreateForm struct containing the values
	// from the form and an empty map for any validation errors.
	form := snippetCreateForm{
		Title:   r.PostForm.Get("title"),
		Content: r.PostForm.Get("content"),
		Expires: expires,
		FieldErrors: map[string]string{},
	}

	// Update the validation checks so that they operate on the snippetCreateForm
	// instance.
	if strings.TrimSpace(form.Title) == "" {
		form.FieldErrors["title"] = "This field cannot be blank"
	} else if utf8.RuneCountInString(form.Title) > 100 {
		form.FieldErrors["title"] = "This field cannot be more than 100 characters long"
	}

	if strings.TrimSpace(form.Content) == "" {
		form.FieldErrors["content"] = "This field cannot be blank"
	}

	if form.Expires != 1 && form.Expires != 7 && form.Expires != 365 {
		form.FieldErrors["expires"] = "This field must equal 1, 7 or 365"
	}

	// If there are any validation errors, then re-display the create.tmpl template,
	// passing in the snippetCreateForm instance as dynamic data in the Form
	// field. Note that we use the HTTP status code 422 Unprocessable Entity
	// when sending the response to indicate that there was a validation error.
	if len(form.FieldErrors) > 0 {
		data := app.newTemplateData(r)
		data.Form = form
		app.render(w, r, http.StatusUnprocessableEntity, "create.tmpl", data)
		return
	}

	// We also need to update this line to pass the data from the
	// snippetCreateForm instance to our Insert() method.
	id, err := app.snippets.Insert(form.Title, form.Content, form.Expires)
	if err != nil {
		app.serverError(w, r, err)
		return
	}

	http.Redirect(w, r, fmt.Sprintf("/snippet/view/%d", id), http.StatusSeeOther)
}
```

好的，现在当存在任何验证错误时，我们会通过模板数据的 Form 字段，以 snippetCreateForm 结构体的形式将之前的数据和验证错误传入 create.tmpl 模板并重新显示它。

如果愿意，你现在应该能够运行应用程序，代码应该可以无任何错误地编译。

## 更新 HTML 模板

下一步我们需要做的是更新 create.tmpl 模板，以显示验证错误并重新填充任何之前的数据。

重新填充表单数据相当简单——我们应该能够使用 {{.Form.Title}} 和 {{.Form.Content}} 之类的标签在模板中渲染它们，就像我们之前在书中显示代码片段数据时那样。

对于验证错误，我们的 FieldErrors 字段的底层类型是 map[string]string，它使用表单字段名称作为键。对于映射，可以通过简单地链接键名来访问给定键的值。例如，要在模板中渲染 title 字段的验证错误，可以使用标签 {{.Form.FieldErrors.title}}。

> 注意：与结构体字段不同，映射键名不必大写才能从模板中访问它们。

有了这一点，让我们更新 create.tmpl 文件以重新填充数据，并在字段存在时显示每个字段的错误消息。

File: ui/html/pages/create.tmpl

```html
{{define "title"}}Create a New Snippet{{end}}

{{define "main"}}
<form action='/snippet/create' method='POST'>
<div>
<label>Title:</label>
<!-- Use the 'with' action to render the value of .Form.FieldErrors.title
if it is not empty. -->
{{with .Form.FieldErrors.title}}
<label class="error">{{.}}</label>
{{end}}
<!-- Re-populate the title data by setting the 'value' attribute. -->
<input type='text' name='title' value='{{.Form.Title}}'>
</div>
<div>
<label>Content:</label>
<!-- Likewise render the value of .Form.FieldErrors.content if it is
empty. -->
{{with .Form.FieldErrors.content}}
<label class="error">{{.}}</label>
{{end}}
<!-- Re-populate the content data as the inner HTML of the textarea. -->
<textarea name='content'>{{.Form.Content}}</textarea>
</div>
<div>
<label>Expires in:</label>
<!-- And render the value of .Form.FieldErrors.expires if it is not empty. -->
{{with .Form.FieldErrors.expires}}
<label class="error">{{.}}</label>
{{end}}
<!-- Here we use the 'if' action to check if the value of the re-populated
expires field equals 365. If it does, then we render the 'checked'
attribute so that the radio input is re-selected. -->
<input type='radio' name='expires' value='365' {{if (eq .Form.Expires 365)}}checked{{end}}> One Year
<!-- And we do the same for the other possible values too... -->
<input type='radio' name='expires' value='7' {{if (eq .Form.Expires 7)}}checked{{end}}> One Week
<input type='radio' name='expires' value='1' {{if (eq .Form.Expires 1)}}checked{{end}}> One Day
</div>
<div>
<input type='submit' value='Publish snippet'>
</div>
</form>
{{end}}
```

希望这些标记和我们对 Go 模板动作的使用通常是清晰的——它只是使用我们之前在书中见过和讨论过的技术。

我们还需要做最后一件事。如果现在尝试运行应用程序，当我们首次访问 http://localhost:4000/snippet/create 处的表单时，会出现 500 Internal Server Error。这是因为我们的 snippetCreate 处理程序当前未为 templateData.Form 字段设置值，这意味着当 Go 尝试评估类似 {{with .Form.FieldErrors.title}} 的模板标签时，会因为 Form 为 nil 而导致错误。

让我们通过更新 snippetCreate 处理程序来修复它，使其初始化一个新的 snippetCreateForm 实例并将其传递给模板，如下所示：

File: cmd/web/handlers.go

```go
package main

...

func (app *application) snippetCreate(w http.ResponseWriter, r *http.Request) {
    data := app.newTemplateData(r)

    // Initialize a new snippetCreateForm instance and pass it to the template.
    // Notice how this is also a great opportunity to set any default or
    // 'initial' values for the form --- here we set the initial value for the
    // snippet expiry to 365 days.
    data.Form = snippetCreateForm{
        Expires: 365,
    }

    app.render(w, r, http.StatusOK, "create.tmpl", data)
}

...
```

现在完成了，请重新启动应用程序并在浏览器中访问 http://localhost:4000/snippet/create。您应该会发现页面正确渲染且没有任何错误。

然后尝试添加一些内容并更改默认过期时间，但保持标题字段为空，如下所示：

