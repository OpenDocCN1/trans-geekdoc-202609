# # Catching runtime errors

As soon as we begin adding dynamic behavior to our HTML templates there’s a risk of encountering runtime errors.

Let’s add a deliberate error to the view.tmpl template and see what happens:

```
File: ui/html/pages/view.tmpl

{{define "title"}}Snippet #({{.Snippet.ID}}}{{end}})

{{define "main"}}
{{with .Snippet}}
<div class="snippet">
<div class="metadata">
<strong>{{.Title}}</strong>
<span>#({{.ID}})</span>
</div>
{{len nil}} {{!-- Deliberate error --}}
<pre><code>{{.Content}}</code></pre>
<div class="metadata">
<time>Created: {{.Created}}</time>
<time>Expires: {{.Expires}}</time>
</div>
</div>
{{end}}
{{end}}
```

In this markup above we’ve added the line {{len nil}}, which should generate an error at runtime because in Go the value nil does not have a length.

Try running the application now. You’ll find that everything still compiles OK:

```
$ go run ./cmd/web
time=2024-03-18T11:29:23.000Z+00:00 level=INFO msg="starting server" addr=:4000
```

But if you use curl to make a request to http://localhost:4000/snippet/view/1 you’ll get a response which looks a bit like this.