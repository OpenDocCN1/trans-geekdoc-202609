
```go
func PostsCreateHandler(rw http.ResponseWriter, r *http.Request, p httprouter.Params) {
	fmt.Fprintln(rw, "posts create")
}

func PostShowHandler(rw http.ResponseWriter, r *http.Request, p httprouter.Params) {
	id := p.ByName("id")
	fmt.Fprintln(rw, "showing post", id)
}

func PostUpdateHandler(rw http.ResponseWriter, r *http.Request, p httprouter.Params) {
	fmt.Fprintln(rw, "post update")
}

func PostDeleteHandler(rw http.ResponseWriter, r *http.Request, p httprouter.Params) {
	fmt.Fprintln(rw, "post delete")
}

func PostEditHandler(rw http.ResponseWriter, r *http.Request, p httprouter.Params) {
	fmt.Fprintln(rw, "post edit")
}
```

### Exercises

- 1. Explore the documentation for `github.com/julienschmidt/httprouter`.
- 2. Find out how well `github.com/julienschmidt/httprouter` plays nicely with existing `http.Handler` like `http.FileServer`
- 3. `httprouter` has a very simple interface. Explore what kind of abstractions can be built on top of this fast router to make building things like RESTful routing easier.

## Middleware

If you have some code that needs to be run for every request, regardless of the route that it will eventually end up invoking, you need some way to stack `http.Handlers` on top of each other and run them in sequence. This problem is solved elegantly through middleware packages. Negroni is a popular middleware package that makes building and stacking middleware very easy while keeping the composable nature of the Go web ecosystem intact.

Negroni comes with some default middleware such as Logging, Error Recovery, and Static file serving. So out of the box Negroni will provide you with a lot of value without a lot of overhead.

The example below shows how to use a Negroni stack with the built in middleware and how to create your own custom middleware.

```go
package main

import (
	"log"
	"net/http"

	"github.com/codegangsta/negroni"
)

func main() {
	// Middleware stack
	n := negroni.New(
		negroni.NewRecovery(),
		negroni.HandlerFunc(MyMiddleware),
		negroni.NewLogger(),
		negroni.NewStatic(http.Dir("public")),
	)

	n.Run(":8080")
}

func MyMiddleware(rw http.ResponseWriter, r *http.Request, next http.HandlerFunc) {
	log.Println("Logging on the way there...")

	if r.URL.Query().Get("password") == "secret123" {
		next(rw, r)
	} else {
		http.Error(rw, "Not Authorized", 401)
	}

	log.Println("Logging on the way back...")
}
```

### Exercises

- 1. Think of some cool middleware ideas and try to implement them using Negroni.
- 2. Explore how Negroni can be composed with github.com/gorilla/mux using the http.Handler interface.
- 3. Play with creating Negroni stacks for certain groups of routes instead of the entire application.

## Rendering

Rendering is the process of taking data from your application or database and presenting it
for the client. The client can be a browser that renders HTML, or it can be another
application that consumes JSON as its serialization format. In this chapter we will learn how
to render both of these formats using the methods that Go provides for us in the standard
library.

### JSON

JSON is quickly becoming the ubiquitous serialization format for web APIs, so it may be the most relevant when learning how to build web apps using Go. Fortunately, Go makes it simple to work with JSON -- it is extremely easy to turn existing Go structs into JSON using the `encoding/json` package from the standard library.

```go
package main

import (
	"encoding/json"
	"net/http"
)

type Book struct {
	Title string `json:"title"`
	Author string `json:"author"`
}

func main() {
	http.HandleFunc("/", ShowBooks)
	http.ListenAndServe(":8080", nil)
}

func ShowBooks(w http.ResponseWriter, r *http.Request) {
	book := Book{"Building Web Apps with Go", "Jeremy Saenz"}

	js, err := json.Marshal(book)
	if err != nil {
		http.Error(w, err.Error(), http.StatusInternalServerError)
		return
	}

	w.Header().Set("Content-Type", "application/json")
	w.Write(js)
}
```

### Exercises

- 1. Read through the JSON API docs and find out how to rename and ignore fields for JSON serialization.
- 2. Instead of using the `json.Marshal` method, try using the `json.Encoder` API.
- 3. Figure out how to pretty print JSON with the `encoding/json` package.

### HTML Templates

Serving HTML is an important job for some web applications. Go has one of my favorite templating languages to date. Not for its features, but for its simplicity and out of the box security. Rendering HTML templates is almost as easy as rendering JSON using the `html/template` package from the standard library. Here is what the source code for rendering HTML templates looks like:

```go
package main

import (
	"html/template"
	"net/http"
	"path"
)

type Book struct {
	Title string
	Author string
}

func main() {
	http.HandleFunc("/", ShowBooks)
	http.ListenAndServe(":8080", nil)
}

func ShowBooks(w http.ResponseWriter, r *http.Request) {
	book := Book{"Building Web Apps with Go", "Jeremy Saenz"}

	fp := path.Join("templates", "index.html")
	tmpl, err := template.ParseFiles(fp)
	if err != nil {
		http.Error(w, err.Error(), http.StatusInternalServerError)
		return
	}

	if err := tmpl.Execute(w, book); err != nil {
		http.Error(w, err.Error(), http.StatusInternalServerError)
	}
}
```

This is the following template we will be using. It should be placed in a `templates/index.html` file in the directory your program is run from:

```html
<html>
<h1>{{ .Title }}</h1>
<h3>by {{ .Author }}</h3>
</html>
```

### Exercises

- 1. Look through the docs for `text/template` and `html/template` package. Play with the templating language a bit to get a feel for its goals, strengths, and weaknesses.

- 2. In the example we parse the files on every request, which can be a lot of performance overhead. Experiment with parsing the files at the beginning of your program and executing them in your `http.Handler` (hint: make use of the `Copy()` method on `html.Template` ).

- 3. Experiment with parsing and using multiple templates.

## Using the render package

If you want rendering JSON and HTML to be even simpler, there is the github.com/unrolled/render package. This package was inspired by the martini-contrib/render package and is my goto when it comes to rendering data for presentation in my web applications.

```go
package main

import (
	"net/http"

	"gopkg.in/unrolled/render.v1"
)

func main() {
	r := render.New(render.Options{})
	mux := http.NewServeMux()

	mux.HandleFunc("/", func(w http.ResponseWriter, req *http.Request) {
		w.Write([]byte("Welcome, visit sub pages now."))
	})

	mux.HandleFunc("/data", func(w http.ResponseWriter, req *http.Request) {
		r.Data(w, http.StatusOK, []byte("Some binary data here."))
	})

	mux.HandleFunc("/json", func(w http.ResponseWriter, req *http.Request) {
		r.JSON(w, http.StatusOK, map[string]string{"hello": "json"})
	})

	mux.HandleFunc("/html", func(w http.ResponseWriter, req *http.Request) {
		// Assumes you have a template in .templates called "example.tmpl"
		// $ mkdir -p templates & echo "<h1>Hello {{.}}</h1>" > templates/example.tmpl
		r.HTML(w, http.StatusOK, "example", nil)
	})

	http.ListenAndServe(":8080", mux)
}
```

### Exercises

- 1. Have fun playing with all of the options available when calling `render.New()`
- 2. Try using the `.yield` helper function (with the curly braces) and a layout with HTML templates.

## Testing

Testing is an important part of any application. There are two approaches we can take to testing Go web applications. The first approach is a unit-test style approach. The other is more of an end-to-end approach. In this chapter we'll cover both approaches.

### Unit Testing

Unit testing allows us to test a `http.HandlerFunc` directly without running any middleware, routers, or any other type of code that might otherwise wrap the function.

```go
package main

import (
	"fmt"
	"net/http"
)

func HelloWorld(res http.ResponseWriter, req *http.Request) {
	fmt.Fprint(res, "Hello World")
}

func main() {
	http.HandleFunc("/", HelloWorld)
	http.ListenAndServe(":3000", nil)
}

```

This is the test file. It should be placed in the same directory as your application and name `main_test.go`.
