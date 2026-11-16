```
File: ui/html/pages/view.tmpl

{{define "title"}}Snippet #({{.Snippet.ID}}){{end}}

{{define "main"}}
    {{with .Snippet}}
    <div class='snippet'>
        <div class="metadata">
            <strong>{{.Title}}</strong>
            <span>#{.ID}}</span>
        </div>
        <pre><code>{{.Content}}</code></pre>
        <div class="metadata">
            <time>Created: {{.Created}}</time>
            <time>Expires: {{.Expires}}</time>
        </div>
    </div>
    {{end}}
{{end}}
```

So now, between {{with .Snippet}} and the corresponding {{end}} tag, the value of dot is set to .Snippet. Dot essentially becomes the models.Snippet struct instead of the parent templateData struct.

# Using the if and range actions

Let's also use the {{if}} and {{range}} actions in a concrete example and update our homepage to display a table of the latest snippets, a bit like this:

![](bbox=[0.115, 0.555, 0.885, 0.905])