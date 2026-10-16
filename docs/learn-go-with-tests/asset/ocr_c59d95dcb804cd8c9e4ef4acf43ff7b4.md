# Edit our existing template to import a top and bottom template

```
```
{{template "top" .}}
<h1>{{.Title}}</h1>
<p>{{.Description}}</p>
Tags: <ul>{{range .Tags}}<li>{{.}}</li>{{end}}</ul>
{{template "bottom" .}}
```
```

Then create top.gohtml with the following

```
```
{{define "top"}}
<!DOCTYPE html>
<html lang="en">
<head>
<title>My amazing blog!</title>
<meta charset="UTF-8"/>
<meta name="description" content="Wow, like and subscribe, it
</head>
<body>
<nav role="navigation">
<div>
<h1>Budding Gopher's blog</h1>
<ul>
<li><a href="/">home</a></li>
<li><a href="about">about</a></li>
<li><a href="archive">archive</a></li>
</ul>
</div>
</nav>
<main>
{{ .end }}
</main>
</body>
</html>
```
```

And bottom.gohtml

```
```
{{define "bottom"}}
</main>
</footer>
<ul>
<li><a href="https://twitter.com/quii">Twitter</a></li>
</ul>
</footer>
</body>
</html>
```
```