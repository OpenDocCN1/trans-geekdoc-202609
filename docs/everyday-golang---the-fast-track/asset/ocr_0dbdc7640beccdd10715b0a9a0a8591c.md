```
```go
fmt.Println("Hello world")
}
```
```

Now you can build and run the code again, note that you can also change the output of the binary when compiled:

```
```bash
go build -o get-json
./get-json
```
```

Go offers a convention-based formatting of files, you can format a file and its indentation with:

```
```bash
gofmt -s -w main.go
```
```

The -w command writes the change to the file.

As we explored in an earlier chapter, Go applications can also be cross-compiled for other operating systems without any further changes, here’s how you can build the above code for Windows:

```
```bash
GOOS=windows go build -o get-json.exe
```
```

# Learn to parse JSON

Let’s go on to parse some JSON. in Go we can turn a JSON document into a struct which is useful for accessing the data in a structured way. If a document doesn’t fit into the structure it will throw an error.

Let’s take an API from the Open Notify group - it shows the number of people in space along with their names.

People in Space JSON

It looks a bit like this:

```
```json
{"people": [{"craft": "ISS", "name": "Sergey Rizhikov"}, {"craft": "ISS", "name": "Andrey Borisenko"}, {"craft": "ISS", "name": "Shane Kimbrough"}, {"craft": "ISS", "name": "Oleg Novitskiy"}, {"craft": "ISS", "name": "Thomas Pesquet"}, {"craft": "ISS", "name": "Peggy Whitson"}], "message": "success", "number": 6}
```
```

According to Wikipedia:

> > In computer science, marshalling or marshaling (US spelling) is the process of transforming the memory representation of an object into a data format suitable for storage or transmission. It is typically used when data must be moved between different parts of a computer program or from one program to another.

If you’re coming from Python, Ruby or Node, then the “Unmarshal” behaviour in Go is usually used whenever you would have parsed text to JSON.

Go takes a reference to a struct, and then tries to marshal the input into the datastructure. The opposite operation is “Marshal” which serializes and object into a text or binary representation.

We will be importing the fmt package for the Println function and the encoding/json package so that we can Unmarshal the JSON text into a struct.

Create main.go:

```
```go
package main

import (
    "encoding/json"
    "fmt"
)

type people struct {
    Number int `json:"number"`
```
```