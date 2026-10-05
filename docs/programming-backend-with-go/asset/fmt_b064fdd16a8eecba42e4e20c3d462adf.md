
# Handling Different HTTP Methods

Methods are commands that specify the action to be executed on a certain resource within the framework of Hypertext Transfer Protocol (`HTTP`) and web servers. To ensure that servers reply correctly according to the request's intent, each HTTP method has a predetermined role. To manage interactions like accessing book details, altering book information, or maintaining user sessions, `gitforgits.com` must comprehend and correctly implement these methods.

## HTTP Methods

We will go over the different HTTP methods and how they work with some examples:

### GET

The `GET` method requests a representation of the specified resource. It should only retrieve data and have no other effect.

```go
func getBookHandler(w http.ResponseWriter, r *http.Request) {
  fmt.Fprintf(w, "Retrieving book details.")
}
```

### POST

The `POST` method submits data to be processed to a specified resource, often causing a change in state or side effects on the server.

```go
func addBookHandler(w http.ResponseWriter, r *http.Request) {
  fmt.Fprintf(w, "Adding a new book to the store.")
}
```

### PUT

The `PUT` method replaces all current representations of the target resource with the request payload.

```go
func updateBookHandler(w http.ResponseWriter, r *http.Request) {
  fmt.Fprintf(w, "Updating an existing book's details.")
}
```

### DELETE

The `DELETE` method deletes the specified resource.

```go
func deleteBookHandler(w http.ResponseWriter, r *http.Request) {
  fmt.Fprintf(w, "Deleting a book from the store.")
}
```

### PATCH

The `PATCH` method is used to apply partial modifications to a resource.

```go
func patchBookHandler(w http.ResponseWriter, r *http.Request) {
  fmt.Fprintf(w, "Applying updates to a book's details.")
}
```

### HEAD

The `HEAD` method is identical to `GET` except that the server must not return a message-body in the response. It is used for obtaining metadata.

```go
func headBookHandler(w http.ResponseWriter, r *http.Request) {
  w.Header().Set("Content-Length", "0")
}
```

### OPTIONS

The `OPTIONS` method describes the communication options for the target resource.

```go
func optionsHandler(w http.ResponseWriter, r *http.Request) {
  w.Header().Set("Allow", "GET, POST, HEAD")
  fmt.Fprintf(w, "Provides options for the resource.")
}
```

### TRACE

The `TRACE` method performs a message loop-back test along the path to the target resource, providing a diagnostic tool.

```go
func traceHandler(w http.ResponseWriter, r *http.Request) {
  fmt.Fprintf(w, "TRACE not implemented.")
}
```

### CONNECT

The `CONNECT` method establishes a tunnel to the server identified by the target resource.

```go
func connectHandler(w http.ResponseWriter, r *http.Request) {
  fmt.Fprintf(w, "CONNECT not implemented.")
}
```

## Sample Program: Implementing Handlers

To see these handlers in action, you can set up a basic server using `http.ServeMux`, registering each handler to a specific path and method:

```go
func main() {
  mux := http.NewServeMux()
  mux.HandleFunc("/books", func(w http.ResponseWriter, r *http.Request) {
    switch r.Method {
      case "GET":
        getBookHandler(w, r)
      case "POST":
        addBookHandler(w, r)
      case "PUT":
        updateBookHandler(w, r)
      case "DELETE":
        deleteBookHandler(w, r)
      case "PATCH":
        patchBookHandler(w, r)
      case "HEAD":
        headBookHandler(w, r)
      case "OPTIONS":
        optionsHandler(w, r)
      case "TRACE":
        traceHandler(w, r)
      case "CONNECT":
        connectHandler(w, r)
      default:
        http.Error(w, "Unsupported HTTP method", http.StatusMethodNotAllowed)
    }
  })
  fmt.Println("Server starting on port 8080...")
  if err := http.ListenAndServe(":8080", mux); err != nil {
    fmt.Println("Error starting server: ", err)
  }
}
```

This setup allows you to test each HTTP method's implementation by sending requests to the `/books` endpoint with different methods. The server will respond according to the logic defined in the corresponding handler, demonstrating the practical application of each HTTP method within the scope of your backend server for `gitforgits.com`.

# Query Parameters and URL Fragments

The creation of dynamic and responsive web apps relies heavily on query parameters and fragments of URLs. They make it possible for servers to adapt their actions and content to the user's preferences by analyzing the data provided in the URL. This functionality is absolutely necessary for `gitforgits.com` because it allows users to do things like search, filter books, or jump to specific parts of a page.

## Importance of Query Parameters and URL Fragments

### Query Parameters

These are appended to the URL following a `?` and are used to store data that the client sends to the server. For example, in a URL like `http://gitforgits.com/books?genre=fiction`, the query parameter `genre=fiction` tells the server to filter the books displayed to those that match the genre 'fiction'. This makes the application interactive and capable of responding to user preferences without needing to hard code these preferences into the URL path.

### URL Fragments

Fragments follow a `#` in the URL and are generally used to direct the browser to a specific section of the page without reloading the web page. For example, `http://gitforgits.com/books#author-details` might direct the user to the 'Author Details' section of the 'Books' page. Unlike query parameters, fragments are typically not sent to the server with the HTTP request; they are handled client-side by the browser.

## Sample Program: Utilizing Query Parameters and URL Fragments

We will take a closer look at the Go backend for `gitforgits.com` and see how we can incorporate and use URL fragments and query parameters. We will concentrate on query parameters for server-side processing and touch on fragments briefly for client-side use.

### Handling Query Parameters

Using query parameters allows the backend of `gitforgits.com` to handle requests dynamically. Suppose you want to implement a feature that lets users search for books by title or filter books by genre. Given below is how you might set this up:

```go
package main
import (
  "fmt"
  "net/http"
)
func booksHandler(w http.ResponseWriter, r *http.Request) {
  // Parse query parameters
  title := r.URL.Query().Get("title")
  genre := r.URL.Query().Get("genre")
  response := "Books"
  if title != "" {
    response += fmt.Sprintf(" with title matching: %s", title)
  }
  if genre != "" {
    response += fmt.Sprintf(" in genre: %s", genre)
  }
  fmt.Fprintf(w, response)
}
func main() {
  http.HandleFunc("/books", booksHandler)
  fmt.Println("Server starting on port 8080...")
  http.ListenAndServe(":8080", nil)
}
```

In the above sample program, the server extracts the `title` and `genre` parameters from the URL. If these parameters exist, the server includes them in the response, allowing the user to see a filtered list of books based on their query.

### URL Fragments for Client-Side Handling

While Go does not directly handle URL fragments (since they are not sent to the server), it’s useful to know how they might be used in conjunction with server-side setups. For instance, after a server response is rendered on a webpage, JavaScript running on the client’s browser could take a fragment from the URL and use it to automatically scroll to a specific part of the page or to load additional data related to that fragment.

### Testing Implementation

To test the above Go server code, you can use a web browser or tools like `curl` to send requests:

```bash
curl "http://localhost:8080/books?title=Go%20Programming&genre=Non-fiction"
```

This request would make the Go server respond with "Books with title matching: Go Programming in genre: Non-fiction", demonstrating how the server dynamically generates responses based on URL query parameters.

Query parameters allow the server to tailor the data it sends back to the user, enabling functionalities such as search and filtering, which are essential for a data-rich application like an online bookstore. Meanwhile, URL fragments, though handled client-side, can enhance the user experience by guiding users directly to relevant sections of a webpage.
