Any data that you pass as the final parameter to ts.ExecuteTemplate() is represented within your HTML templates by the . character (referred to as dot).

In this specific case, the underlying type of dot will be a models.Snippet struct. When the underlying type of dot is a struct, you can render (or yield) the value of any exported field in your templates by postfixing dot with the field name. So, because our models.Snippet struct has a Title field, we could yield the snippet title by writing {{.Title}} in our templates.

I'll demonstrate. Create a new file at ui/html/pages/view.tmpl and add the following markup:

```
$ touch ui/html/pages/view.tmpl
```

```
File: ui/html/pages/view.tmpl

{{define "title"}}Snippet #{{.ID}}{{end}}

{{define "main"}}
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
```

If you restart the application and visit http://localhost:4000/snippet/view/1 in your browser, you should find that the relevant snippet is fetched from the database, passed to the template, and the content is rendered correctly.