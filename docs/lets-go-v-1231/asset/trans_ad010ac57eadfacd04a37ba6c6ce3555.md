

```
File: cmd/web/helpers.go

package main

import (
	"bytes" // New import
	"fmt"
	"net/http"
)

...

func (app *application) render(w http.ResponseWriter, r *http.Request, status int, page string, data templateData) {
	ts, ok := app.templateCache[page]
	if !ok {
		err := fmt.Errorf("the template %s does not exist", page)
		app.serverError(w, r, err)
		return
	}

	// Initialize a new buffer.
	buf := new(bytes.Buffer)

	// Write the template to the buffer, instead of straight to the
	// http.ResponseWriter. If there's an error, call our serverError() helper
	// and then return.
	err := ts.ExecuteTemplate(buf, "base", data)
	if err != nil {
		app.serverError(w, r, err)
		return
	}

	// If the template is written to the buffer without any errors, we are safe
	// to go ahead and write the HTTP status code to http.ResponseWriter.
	w.WriteHeader(status)

	// Write the contents of the buffer to the http.ResponseWriter. Note: this
	// is another time where we pass our http.ResponseWriter to a function that
	// takes an io.Writer.
	buf.WriteTo(w)
}
```

重启应用程序，尝试再次发出相同的请求。你现在应该能看到正确的错误消息和 500 Internal Server Error 响应。

```
$ curl -i http://localhost:4000/snippet/view/1
HTTP/1.1 500 Internal Server Error
Content-Type: text/plain; charset=utf-8
X-Content-Type-Options: nosniff
Date: Wed, 18 Mar 2024 11:29:23 GMT
Content-Length: 22

Internal Server Error
```

太棒了。现在看起来好多了。

在进入下一章之前，请返回 view.tmpl 文件并删除故意引入的错误：

```
File: ui/html/pages/view.tmpl

{{define "title"}}Snippet #{{.Snippet.ID}}{{end}}

{{define "main"}}
{{with .Snippet}}
<div class='snippet'>
    <div class='metadata'>
        <strong>{{.Title}}</strong>
        <span>#{{.ID}}</span>
    </div>
    <pre><code>{{.Content}}</code></pre>
    <div class='metadata'>
        <time>Created: {{.Created}}</time>
        <time>Expires: {{.Expires}}</time>
    </div>
</div>
{{end}}
{{end}}
```

## 常见动态数据

在某些 Web 应用程序中，你可能希望在多个（甚至每一个）网页中包含相同的动态数据。例如，你可能希望在所有带有表单的页面中包含当前用户的名称和头像，或者 CSRF 令牌。

在我们的例子中，先从简单的开始，假设我们希望在每个页面的页脚中包含当前年份。

为此，我们首先要在 templateData 结构体中添加一个新的 CurrentYear 字段，如下所示：

```
File: cmd/web/templates.go

package main

...

// Add a CurrentYear field to the templateData struct.
type templateData struct {
	CurrentYear int
	Snippet       models.Snippet
	Snippets      []models.Snippet
}

...
```

下一步是向我们的应用程序添加一个 newTemplateData() 辅助方法，该方法将返回一个用当前年份初始化的 templateData 结构体。

我来演示一下：

```
File: cmd/web/helpers.go

package main

import (
	"bytes"
	"fmt"
	"net/http"
	"time" // New import
)

...

// Create an newTemplateData() helper, which returns a templateData struct
// initialized with the current year. Note that we're not using the *http.Request
// parameter here at the moment, but we will do later in the book.
func (app *application) newTemplateData(r *http.Request) templateData {
	return templateData{
		CurrentYear: time.Now().Year(),
	}
}

...
```

然后让我们更新 `home` 和 `snippetView` 处理程序，以使用 `newTemplateData()` 辅助方法，如下所示：

```
File: cmd/web/handlers.go

package main

...

func (app *application) home(w http.ResponseWriter, r *http.Request) {
	w.Header().Add("Server", "Go")

	snippets, err := app.snippets.Latest()
	if err != nil {
		app.serverError(w, r, err)
		return
	}

	// Call the newTemplateData() helper to get a templateData struct containing
	// the 'default' data (which for now is just the current year), and add the
	// snippets slice to it.
	data := app.newTemplateData(r)
	data.Snippets = snippets

	// Pass the data to the render() helper as normal.
	app.render(w, r, http.StatusOK, "home.tmpl", data)
}

func (app *application) snippetView(w http.ResponseWriter, r *http.Request) {
	id, err := strconv.Atoi(r.PathValue("id"))
	if err != nil || id < 1 {
		http.NotFound(w, r)
		return
	}

	snippet, err := app.snippets.Get(id)
	if err != nil {
		if errors.Is(err, models.ErrNoRecord) {
			http.NotFound(w, r)
		} else {
			app.serverError(w, r, err)
		}
		return
	}

	// And do the same thing again here...
	data := app.newTemplateData(r)
	data.Snippet = snippet

	app.render(w, r, http.StatusOK, "view.tmpl", data)
}

...
```

然后我们需要做的最后一件事是更新 ui/html/base.tmpl 文件，在页脚中显示年份，如下所示：

```
File: ui/html/base.tmpl

{{define "base"}}
<!doctype html>
<html lang='en'>
<head>
    <meta charset='utf-8'>
    <title>{{template "title" .}} - Snippetbox</title>
    <link rel='stylesheet' href='/static/css/main.css'>
    <link rel='shortcut icon' href='/static/img/favicon.ico' type='image/x-icon'>
    <link rel='stylesheet' href='https://fonts.googleapis.com/css?family=Ubuntu+Mono:400,700'>
</head>
<body>
    <header>
        <h1><a href='/'/>Snippetbox</a></h1>
    </header>
    {{template "nav" .}}
    <main>
        {{template "main" .}}
    </main>
    <footer>
        <!-- Update the footer to include the current year -->
        Powered by <a href='https://golang.org/'>Go</a> in {{.CurrentYear}}
    </footer>
    <script src='/static/js/main.js' type='text/javascript'></script>
</body>
</html>
{{end}}
```

如果你重启应用程序并访问 http://localhost:4000 的主页，现在应该能在页脚中看到当前年份。如下所示：

![](img/c3e650db0d8dfdecc0f8e34a67719f65_167_0.png)

## 自定义模板函数

在本节关于模板和动态数据的最后部分，我想解释如何创建可在 Go 模板中使用的自定义函数。

为说明这一点，让我们创建一个自定义 humanDate() 函数，它以友好的人性化格式输出日期时间，例如 1 Jan 2024 at 10:47 或 18 Mar 2024 at 15:04，而不是像我们目前这样以 YYYY-MM-DD HH:MM:SS +0000 UTC 的默认格式输出日期。

做这件事主要有两个步骤：

- 1. 我们需要创建一个包含自定义 humanDate() 函数的 template.FuncMap 对象。
- 2. 我们需要在解析模板之前使用 template.Funcs() 方法注册此对象。

请将以下代码添加到你的 templates.go 文件中：

```
File: cmd/web/templates.go

package main

import (
	"html/template"
	"path/filepath"
	"time" // New import

	"snippetbox.alexedwards.net/internal/models"
)

...

// Create a humanDate function which returns a nicely formatted string
// representation of a time.Time object.
func humanDate(t time.Time) string {
	return t.Format("02 Jan 2006 at 15:04")
}

// Initialize a template.FuncMap object and store it in a global variable. This is
// essentially a string-keyed map which acts as a lookup between the names of our
// custom template functions and the functions themselves.
var functions = template.FuncMap{
	"humanDate": humanDate,
}

func newTemplateCache() (map[string]*template.Template, error) {
	cache := map[string]*template.Template{}

	pages, err := filepath.Glob("./ui/html/pages/*.tmpl")
	if err != nil {
		return nil, err
	}

	for _, page := range pages {
		name := filepath.Base(page)

		// The template.FuncMap must be registered with the template set before you
		// call the ParseFiles() method. This means we have to use template.New() to
		// create an empty template set, use the Funcs() method to register the
		// template.FuncMap, and then parse the file as normal.
		ts, err := template.New(name).Funcs(functions).ParseFiles("./ui/html/base.tmpl")
		if err != nil {
			return nil, err
		}

		ts, err = ts.ParseGlob("./ui/html/partials/*.tmpl")
		if err != nil {
			return nil, err
		}

		ts, err = ts.ParseFiles(page)
		if err != nil {
			return nil, err
		}

		cache[name] = ts
	}

	return cache, nil
}
```

