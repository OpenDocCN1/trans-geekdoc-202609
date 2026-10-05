# 3.2. POPULAR ROUTERS

fast, it also supports named URL parameters and routing based on the HTTP request method used. We will learn more about this in a future chapter.

Ultimately I opted not to use useRouter for this book for two reasons. The first is that the library requires you to use http handler functions that take in a third argument if you want to access any path parameters. There isn't anything wrong with this approach, but I was concerned that it might lead to some confusion with new programmers and opted instead to use the router we are going to cover next - gorilla/mux.Router.

# 3.2.3 github.com/gorilla/mux.Router

Finally, we are going to check out github.com/gorilla/mux.Router. This router supports everything that we will need throughout this book (and much more), and it allows us to work with regular old http handler functions.

On top of that, gorilla/mux is a part of the Gorilla Toolkit, a popular set of packages for building web applications. That in itself isn't a reason to use it, but since we will also be using a few other packages from the Gorilla Toolkit is an added bonus that we are also using their router.

# 3.2.4 What about <some other router>

There are several other great routers out there that I don't mention here and don't use in this book. Many of them are great, and might even be better than gorilla/mux, at the time of writing this gorilla/mux was the best choice available to me. Not only is it one of the most popular routers in Go, it has been around for a very long time with a strong track record of stability.