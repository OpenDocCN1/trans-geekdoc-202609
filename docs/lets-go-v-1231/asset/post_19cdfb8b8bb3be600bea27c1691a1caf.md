
## Prerequisites

## Background knowledge

This book is designed for people who are new to Go, but you’ll probably find it more enjoyable if you have a general understanding of Go’s syntax first. If you find yourself struggling with the syntax, the Little Book of Go by Karl Seguin is a fantastic tutorial, or if you want something more interactive I recommend running through the Tour of Go.

I’ve also assumed that you’ve got a (very) basic understanding of HTML/CSS and SQL, and some familiarity with using your terminal (or command line for Windows users). If you’ve built a web application in any other language before — whether it’s Ruby, Python, PHP or C# — then this book should be a good fit for you.

## Go 1.23

The information in this book is correct for the latest major release of Go (version 1.23), and you should install this if you’d like to code-along with the application build.

If you’ve already got Go installed, you can check the version number from your terminal by using the go version command. The output should look similar to this:

```
$ go version
go version go1.23.0 linux/amd64
```

If you need to upgrade your version of Go — or install Go from scratch — then please go ahead and do that now. Detailed instructions for different operating systems can be found here:

- Removing an old version of Go
- Installing Go on Mac OS X
- Installing Go on Windows
- Installing Go on Linux

## Other software

There are a few other bits of software that you should make sure are available on your computer if you want to follow along fully. They are:

- The curl tool for working with HTTP requests and responses from your terminal. On MacOS and Linux machines it should be pre-installed or available in your software repositories. Otherwise, you can download the latest version from here.
- A web browser with good developer tools. I'll be using Firefox in this book, but Chromium, Chrome or Microsoft Edge will work too.
- Your favorite text editor 🙂

## Foundations

Alright, let’s get started! In this first section of the book we’re going to lay the groundwork for our project and explain the main principles that you need to know for the rest of the application build.

You’ll learn how to:

- Set up a project directory which follows the Go conventions.
- Start a web server and listen for incoming HTTP requests.
- Route requests to different handlers based on the request path and method.
- Use wildcard segments in your routing patterns.
- Send different HTTP responses, headers and status codes to users.
- Structure your project in a sensible and scalable way.
- Render HTML pages and use template inheritance to keep your HTML markup free of duplicate boilerplate code.
- Serve static files like images, CSS and JavaScript from your application.

## Project setup and creating a module

Before we write any code, you’ll need to create a `snippetbox` directory on your computer to act as the top-level ‘home’ for this project. All the Go code we write throughout the book will live in here, along with other project-specific assets like HTML templates and CSS files.

So, if you’re following along, open your terminal and create a new project directory called `snippetbox` anywhere on your computer. I’m going to locate my project directory under `$HOME/code`, but you can choose a different location if you wish.

```
$ mkdir -p $HOME/code/snippetbox
```

## Creating a module

The next thing you need to do is decide on a module path for your project.

If you’re not already familiar with Go modules, you can think of a module path as basically being a canonical name or identifier for your project.

You can pick **almost any string** as your module path, but the important thing to focus on is *uniqueness*. To avoid potential import conflicts with other people’s projects or the standard library in the future, you want to pick a module path that is globally unique and unlikely to be used by anything else. In the Go community, a common convention is to base your module paths on a URL that you own.

In my case, a clear, succinct and *unlikely-to-be-used-by-anything-else* module path for this project would be `snippetbox.alexedwards.net`, and I’ll use this throughout the rest of the book. If possible, you should swap this for something that’s unique to you instead.

Once you’ve decided on a unique module path, the next thing you need to do is turn your project directory into a module.

Make sure that you’re in the root of your project directory and then run the `go mod init` command — passing in your chosen module path as a parameter like so:

```
$ cd $HOME/code/snippetbox
$ go mod init snippetbox.alexedwards.net
go: creating new go.mod: module snippetbox.alexedwards.net
```

At this point your project directory should look a bit like the screenshot below. Notice the go.mod file which has been created?

![](img/c3e650db0d8dfdecc0f8e34a67719f65_12_0.png)

At the moment there’s not much going on in this file, and if you open it up in your text editor it should look like this (but preferably with your own unique module path instead):

```
File: go.mod

module snippetbox.alexedwards.net

go 1.23.0
```

We’ll talk about modules in more detail later in the book, but for now it’s enough to know that when there is a valid go.mod file in the root of your project directory, your project is a module. Setting up your project as a module has a number of advantages — including making it much easier to manage third-party dependencies, avoid supply-chain attacks, and ensure reproducible builds of your application in the future.

## Hello world!

Before we continue, let’s quickly check that everything is set up correctly. Go ahead and create a new main.go in your project directory containing the following code:

```
$ touch main.go
```

```
File: main.go

package main

import "fmt"

func main() {
	fmt.Println("Hello world!")
}
```

Save this file, then use the go run . command in your terminal to compile and execute the code in the current directory. All being well, you will see the following output:

```
$ go run .
Hello world!
```

## Additional information

## Module paths for downloadable packages

If you're creating a project which can be downloaded and used by other people and programs, then it's good practice for your module path to equal the location that the code can be downloaded from.

For instance, if your package is hosted at https://github.com/foo/bar then the module path for the project should be github.com/foo/bar.

## Web application basics

Now that everything is set up correctly, let’s make the first iteration of our web application. We’ll begin with the three absolute essentials:

- The first thing we need is a handler. If you’ve previously built web applications using a MVC pattern, you can think of handlers as being a bit like controllers. They’re responsible for executing your application logic and for writing HTTP response headers and bodies.
- The second component is a router (or servemux in Go terminology). This stores a mapping between the URL routing patterns for your application and the corresponding handlers. Usually you have one servemux for your application containing all your routes.
- The last thing we need is a web server. One of the great things about Go is that you can establish a web server and listen for incoming requests as part of your application itself. You don’t need an external third-party server like Nginx, Apache or Caddy.

Let’s put these components together in the `main.go` file to make a working application.

```
File: main.go

package main

import (
	"log"
	"net/http"
)

// Define a home handler function which writes a byte slice containing
// "Hello from Snippetbox" as the response body.
func home(w http.ResponseWriter, r *http.Request) {
	w.Write([]byte("Hello from Snippetbox"))
}

func main() {
	// Use the http.NewServeMux() function to initialize a new servemux, then
	// register the home function as the handler for the "/" URL pattern.
	mux := http.NewServeMux()
	mux.HandleFunc("/", home)

	// Print a log message to say that the server is starting.
	log.Print("starting server on :4000")

	// Use the http.ListenAndServe() function to start a new web server. We pass in
	// two parameters: the TCP network address to listen on (in this case ":4000")
	// and the servemux we just created. If http.ListenAndServe() returns an error
	// we use the log.Fatal() function to log the error message and exit. Note
	// that any error returned by http.ListenAndServe() is always non-nil.
	err := http.ListenAndServe(":4000", mux)
	log.Fatal(err)
}
```

> Note: The `home` handler function is just a regular Go function with two parameters. The `http.ResponseWriter` parameter provides methods for assembling a HTTP response and sending it to the user, and the `*http.Request` parameter is a pointer to a struct which holds information about the current request (like the HTTP method and the URL being requested). We'll talk more about these parameters and demonstrate how to use them as we progress through the book.

When you run this code, it will start a web server listening on port 4000 of your local machine. Each time the server receives a new HTTP request it will pass the request on to the servemux and — in turn — the servemux will check the URL path and dispatch the request to the matching handler.

Let's give this a whirl. Save your `main.go` file and then try running it from your terminal using the `go run` command.

```
$ cd $HOME/code/snippetbox
$ go run .
2024/03/18 11:29:23 starting server on :4000
```
