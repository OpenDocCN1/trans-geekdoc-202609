```
port := os.Getenv("PORT")
if port == "" {
    port = "8080"
}
```

Lastly, we want to bind to that port in our `http.ListenAndServe` call:

```
http.ListenAndServe(":"+port, nil)
```

The final code should look like this:

```
package main

import (
    "net/http"
    "os"

    "github.com/russross/blackfriday"
)

func main() {
    port := os.Getenv("PORT")
    if port == "" {
        port = "8080"
    }

    http.HandleFunc("/markdown", GenerateMarkdown)
    http.Handle("/", http.FileServer(http.Dir("public")))
    http.ListenAndServe(":"+port, nil)
}

func GenerateMarkdown(rw http.ResponseWriter, r *http.Request) {
    markdown := blackfriday.MarkdownCommon([]byte(r.FormValue("body")))
    rw.Write(markdown)
}
```

# # Configuration

We need a couple small configuration files to tell Heroku how it should run our application. The first one is the `Procfile`, which allows us to define which processes should be run for our application. By default, Go will name the executable after the containing directory of your main package. For instance, if my web application lived in `GOPATH/github.com/codegangsta/bwag/deployment`, my `Procfile` will look like this: