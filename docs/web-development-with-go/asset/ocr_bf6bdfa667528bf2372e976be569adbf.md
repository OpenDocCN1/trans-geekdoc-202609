# CHAPTER 6. CREATING OUR FIRST VIEWS

# Listing 6.23: Creating a navbar.

```
{{define "navbar"}}
<nav class="navbar navbar-default">
<div class="container-fluid">
  <div class="navbar-header">
    <button type="button" class="navbar-toggle collapsed"
      data-toggle="collapse" data-target="#navbar"
      aria-expanded="false" aria-controls="navbar">
      <span class="sr-only">Toggle navigation</span>
      <span class="icon-bar"></span>
      <span class="icon-bar"></span>
      <span class="icon-bar"></span>
    </button>
  </div>
  <a class="navbar-brand" href="#">LensLocked.com</a></a>
  <ul id="navbar" class="navbar-collapse collapse">
    <li><a href="/">Home</a></li>
    <li><a href="/contact">Contact</a></li>
  </ul>
</div>
</nav>
{{/end}}
```

Just like our footer and bootstrap layout, our views need to know about this
template before they can use it. Open up view.go and add the template to the
files being appended to our files slice. This is shown in Listing 6.24.

```
$ atom views/views.go
```

# Listing 6.24: Parsing navbar.gohtml.

```
func NewView(layout string, files ...string) *View {
	files = append(files,
	"views/layouts/footer.gohtml",
	"views/layouts/navbar.gohtml",
	"views/layouts/bootstrap.gohtml")
	} //...
```