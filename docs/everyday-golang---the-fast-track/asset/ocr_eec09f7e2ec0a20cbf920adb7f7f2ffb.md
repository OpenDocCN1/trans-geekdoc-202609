# Chapter 12

# Create dynamic content with templates

Templates are used to replace tokens or expressions in a file or block of text (template) with inputs provided at runtime.

They look similar to expressions found in front-end templating technology like Embedded Ruby (ERb), for this reason they may seem inituitive to you already.

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

```
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
```