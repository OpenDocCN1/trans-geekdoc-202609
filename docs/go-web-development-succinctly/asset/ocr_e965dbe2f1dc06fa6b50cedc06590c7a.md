# Chapter 2 Serving and Routing

Go's net package facilitates all network communications in Go programs, whether it's over HTTP, TCP/IP, WebSockets, or any other standard network protocol.

Of course, because this e-book addresses web development, we are primarily concerned with HTTP, which means the main package we are using is net/http.

In this chapter, we'll look at the basic requirements of any Go web application—serving and routing—and how you can use net/http and complementary packages to implement them.

# Go as a simple web server

Back in the old days, web servers did little more than serve files that resided in a directory that server. If that's all we want, now can do something very in Go using the net/http package in just a few lines of code.

> Code Listing 1: Go as a Web Server

```
package main

import (
    "net/http"
)

func main() {
    http.ListenAndServe(":8999", http.FileServer(http.Dir("/var/www\)))
}
```

It's very basic, but our program fulfills the core responsibilities of any web server—namely, listening to a request and serving a response. What's more, because it doesn't have to worry about all the other issues that a more traditional web server must, the program is lightning fast.

In this example, we call the http.ListenAndServe() function to serve all requests on port 8999 to an http.FileServer handler method, which in turn accepts the directory on the server that we want to serve files from. Easy!

If you run the program go run <program_name.go> and enter http://localhost:8999/ in your browser's address bar, followed by the name of a file that exists in /var/www on your server, you'll see that file's contents displayed—as in Figure 4.