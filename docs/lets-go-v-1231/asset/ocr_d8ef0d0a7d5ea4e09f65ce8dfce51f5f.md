live exclusively under the `cmd` and `internal` directories, leaving the project root free to hold non-Go assets like UI files, makefiles and module definitions (including our `go.mod` file).

+   2. It scales really nicely if you want to add another executable application to your project. For example, you might want to add a CLI (Command Line Interface) to automate some administrative tasks in the future. With this structure, you could create this CLI application under `cmd/cli` and it will be able to import and reuse all the code you’ve written under the `internal` directory.

# # Refactoring your existing code

Let’s quickly port the code we’ve already written to this new structure.

```
File: cmd/web/main.go

package main

import (
	"log"
	"net/http"
)

func main() {
	mux := http.NewServeMux()
	mux.HandleFunc("GET /{$}", home)
	mux.HandleFunc("GET /snippet/view/{id}", snippetView)
	mux.HandleFunc("GET /snippet/create", snippetCreate)
	mux.HandleFunc("POST /snippet/create", snippetCreatePost)

	log.Print("starting server on :4000")

	err := http.ListenAndServe(":4000", mux)
	log.Fatal(err)
}
```