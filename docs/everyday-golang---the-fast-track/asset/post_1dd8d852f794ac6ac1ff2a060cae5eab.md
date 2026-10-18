
## Chapter 11

### Embed data in your application

It can be useful to ship additional resources other than code with your applications. A common method for doing this is embedding files or data.

In the “Store data with a database” chapter we created a todo app, which needed a schema to be created manually to define a table. But what if our application could create the table at start-up, if it didn’t exist already?

Fortunately from Go 1.16 onwards, the embed package made this simple. Before that many third-party libraries were required.

The Go docs show three ways we could achieve this:

```go
import _ "embed"

//go:embed schema.sql
var tableCreate string
print(tableCreate)
```

At build time, the contents of schema.sql will be built into the application, and made available through the tableCreate string. This is very similar to the technique we saw for injecting a version into an application.

If you had an image, then you would want to encode the bytes as a binary []byte slice.

```go
import _ "embed"

//go:embed logo.png
var logo []byte
fmt.Printf("Total bytes: %d\n", len(logo))
```

Once in memory, the logo can then be served to a client via a HTTP connection, modified, or written to disk for instance.

Using the embed.FS interface means that unlike in the previous example, the data is not kept in memory in a variable, and can be loaded on demand. This approach would be useful for large files.

```go
import "embed"

//go:embed ubuntu-20-cloudinit.iso
var f embed.FS
data, _ := f.ReadFile("ubuntu-20-cloudinit.iso")
fmt.Printf("Total bytes: %d\n", len(data))
```

Go is a perfectly good systems programming language, and you’ll find many packages for managing filesystems and networks. You could potentially ship something like an ISO image inside your application that can be written out to a disk at any time.

The fourth option we’ll look at is what I would use if I wanted to ship something like a React.js front-end along with a HTTP server or API written in Go.

```go
import "embed"

// frontend holds our static web server content.
//go:embed image/* template/*
//go:embed public/index.html
//go:embed css/*
var frontend embed.FS
```

Now you can simply link the embed.FS to a custom HTTP middleware or handler and serve the files to users from a specific route or path. You’ll learn more about HTTP servers later in the book, however this is the example given in the Go documentation:

```go
http.Handle("/public/",
	http.StripPrefix("/public/",
		http.FileServer(http.FS(frontend))))
```

Your API could be bound to the path /api/v1/ and then any static content you have embedded would be served from /public/.

## Chapter 12

### Create dynamic content with templates

Templates are used to replace tokens or expressions in a file or block of text (template) with inputs provided at runtime.

They look similar to expressions found in front-end templating technology like Embedded Ruby (ERb), for this reason they may seem intuitive to you already.

A template can be as simple as a single line of text, or a multi-line block. The template could be read from disk, over the Internet, or kept within a const in memory.

Here's an example based upon the Golang docs:

```
Dear {{.Name}},

{{if .Attended}}
It was a pleasure to see you at the wedding.
{{- else}}
It is a shame you couldn't make it to the wedding.
{{- end}}

Best wishes,
Alex
```

First, we need to load the template into memory, then construct a typed struct or an inline struct to pass in the values to be placed within the file, then we execute it to get the result. .Name will be replaced directly, but .Attended is going to cause one of the two following sentences to be added into the letter.

```go
package main

import (
    "bytes"
    "fmt"
    "text/template"
)

const letter = `Dear {{.Name}},
{{if .Attended}}
It was a pleasure to see you at the wedding.
{{- else}}
It is a shame you couldn't make it to the wedding.
{{- end}}
Best wishes,
Alex`

func main() {
```

```go
people := []struct {
    Name     string
    Attended bool
}{
    {
        Name:     "Alex",
        Attended: true,
    },
    {
        Name:     "Mick",
        Attended: false,
    },
}

t := template.Must(template.New("letter").Parse(letter))

for _, person := range people {
    buffer := bytes.Buffer{}
    err := t.Execute(&buffer, person)
    if err != nil {
        panic(err)
    }
    fmt.Printf("Letter for %s:\n\n%s\n", person.Name, buffer.String())
}
```

Running the example we see the following output:

```
$ go run main.go
Letter for Alex:

Dear Alex,

It was a pleasure to see you at the wedding.
Best wishes,
Alex

Letter for Mick:

Dear Mick,

It is a shame you couldn't make it to the wedding.
Best wishes,
Alex
```

Whenever I want to add a HTML front-end to an application, I’ll turn to Go templates and embed the HTML template files along with the code.

### Advanced templates: ranges and custom functions

I use templates with my Sponsors’ Portal in order to list and print out all the previous editions of my newsletter.

Here is a snippet of the code that prints out the list:

![](img/0b5c3b498f62579835cf1d543b46de92_96_0.png)

Figure 12.1: A list of previous newsletter emails

```
<div class="card">
  <h5 class="card-header">Insiders Updates</h5>
  <div class="card-body">
    <h5 class="card-title">Click on an update below, or use your browser to search for topics.</h5>
    <ul>
      <!-- Be a good person, and do not scrape this HTML -->
      {{ range $in, $el:= .Updates }}
        {{ if ($.Updates.YearBreak $in) }}
        </ul>
        <p><b>{{ $el.Date.Year }}</b></p>
        <ul>
        {{ end }}
        <li id="{{ $el.ID }}"><a href="{{ $.Path "/update" }}?id={{ $el.ID }}">{{ $el.Description }}</a></li>
      {{ end }}
    </ul>
  </div>
</div>
```

In the example I used the range keyword to iterate around the Updates slice, which contains a number of Update structs.

Things then get slightly more involved because I wanted to break the list according to the year of the post, so that they would be broken up into blocks or groups.

On the line {{ if ($.Updates.YearBreak $in) }} you can see that I call a function to determine when to break the line. The simplest way to add custom functions to templates is to add functions to the type being accessed in the template.

```go
// Update represents an InsidersUpdate stored as a Gist
type Update struct {
    ID          string    `json:"id,omitempty"`
    Description string    `json:"description,omitempty"`
    Date        time.Time `json:"date,omitempty"`
    MarkdownURL string    `json:"markdownUrl,omitempty"`
    HTMLURL     string    `json:"htmlUrl,omitempty"`
}

type Updates []Update

// YearBreak returns whether the previous item was in
// another year
func (u Updates) YearBreak(i int) bool {
    if i == 0 {
        return true
    }

    return u[i-1].Date.Year() != u[i].Date.Year()
}
```

By checking the index of the current item, and the previous one, we can determine whether we are at a breakpoint in the list of years and emails.

### Real-world templates - arkade

A final example I'll share is the arkade project, where templates were useful for determining which version of a CLI to download.

If there was a convention that all maintainers and vendors used for CLI naming then we would only need one template for all downloads, however that's anything but the case.

You may be wondering why these templates are compiled into the Go binary? The Tool struct could be Marshaled into a JSON file for dynamic updates, but having everything in one place, and being able to unit test quickly seems to be working for us.

```
tools = append(tools,
Tool{
Owner:      "inlets",
Repo:       "inlets-pro",
Name:       "inlets-pro",
Description: "Cloud Native Tunnel for HTTP and TCP traffic.",
BinaryTemplate: `{{ if HasPrefix .OS "ming" -}}
{{.Name}}.exe
{{- else if eq .OS "darwin" -}}
{{.Name}}-darwin
{{- else if eq .Arch "armv6l" -}}
{{.Name}}-armhf
{{- else if eq .Arch "armv7l" -}}
{{.Name}}-armhf
{{- else if eq .Arch "aarch64" -}}
```
