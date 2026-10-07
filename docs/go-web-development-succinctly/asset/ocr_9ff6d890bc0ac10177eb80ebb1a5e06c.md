# Modularity

Web applications, like many other modern applications, usually grow to include a lot of code. Keeping this code organized and efficient, so that it's easy to understand and maintain, is a challenge for today's developers. This is especially the case when several developers are working on the same application and each developer formats their code differently.

Go away many of these problems by imposing a specific method of structuring and formatting code. Functions, variables, constants, and type declarations are all expected to be in predictable places, and Go require all of them to be coded in a specific way.

If Go sound draconian in this regard, consider this—what you lose in freedom of expression you gain in predictability; everything is what you expect it to be and formatted identically throughout.

Go makes it easy for you to satisfy your code formatting rules by providing you with the fmt package that you can build into your workflow to automatically Goify your code.

# Compilation

Unlike many recent web server-side languages, the Go programming language is compiled. This means that a problem such as a runtime error might be difficult to track down is caught in the compilation step. Go's static typing system also helps you discover errors during development that might otherwise escape into production.

# The net/http package

Go's net/http package is excellent and makes starting a web server having full control of accepting requests and delivering responses very easy. Routing is handled by a multiplexer. You can either adopt the one in the standard library or select from several third-party options. In this book, we'll start by using Go's DefaultServeMux, then we'll consider a very capable alternative: gorilla/mux.

# Setting up your development environment

I won't delve deeply into setup here because I'm going to assume that you have some experience using Go. However

The steps involved in setting up your environment consists of:

+   * Installing the Go tools.
* Creating a workspace and setting the GOPATH environment variable.

# Installing the Go tools

The exact steps you will need to follow depend on which platform you are using. Go binaries are available for Windows, Mac OS X, and "nix platforms.