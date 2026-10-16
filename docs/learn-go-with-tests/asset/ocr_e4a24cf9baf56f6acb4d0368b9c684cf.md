memory because we still want the spaces displayed to the user in the anchors.

We have a few options. The first one we'll explore is passing a function in to our template.

# Passing functions into templates

```
```go
func (r *PostRenderer) RenderIndex(w io.Writer, posts []Post) er
    indexTemplate := `<ol>{{range .}}<li><a href="/post/{{sanitis

    templ, err := template.New("index").Funcs(template.FuncMap{
        "sanitiseTitle": func(title string) string {
            return strings.ToLower(strings.Replace(title, " ", ".
        },
    }).Parse(indexTemplate)
    if err != nil {
        return err
    }

    if err := templ.Execute(w, posts); err != nil {
        return err
    }

    return nil
}
```
```

*Before you parse a template* you can add a `template.FuncMap` into your template, which allows you to define functions that can be called within your template. In this case we've made a `sanitiseTitle` function which we then call inside our template with `{{sanitiseTitle .Title}}`.

This is a powerful feature, being able to send functions in to your template will allow you to do some very cool things, but, should you? Going back to the principles of Mustache and logic-less templates, why did they advocate for logic-less? **What is wrong with logic in templates?**