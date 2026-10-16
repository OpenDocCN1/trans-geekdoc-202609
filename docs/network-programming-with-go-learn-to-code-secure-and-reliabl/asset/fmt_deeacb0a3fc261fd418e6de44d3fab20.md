
ture. If you’re following along, you’re currently in the `caddy` directory, which has a caddy binary built from the code in Listing 10-8. Create two subdirectories, `files` and `backend`:

$ `mkdir files backend`

You can retrieve the contents of the `files` subdirectory from `https://github.com/awoodbeck/gnp/tree/master/ch10/files/`. The `backend` subdirectory will store a simple backend service created in the next section.

***Creating a Simple Backend Web Service***

You need a backend web service for Caddy to reverse-proxy requests to, as illus-

trated in Figure 10-1. This service will respond to all requests with an HTML document that includes the static files Caddy serves on the service’s behalf.

Listing 10-9 is the initial code for the backend web service.

```go
package main

import (
	"flag"
	"fmt"
	"log"
	"net/http://
	"net/http"
	"os"
	"os/signal"
	"time")
	
var addr = flag.String("listen", "localhost:8080", "listen address") func main() {
	flag.Parse()

	c := make(chan os.Signal, 1)
	signal.Notify(c, os.Interrupt)

	err := run(*addr, c)

	if err != nil {
		log.Fatal(err)
	}

	log.Println("Server stopped")
}

func run(addr string, c chan os.Signal) error {
	mux := http.NewServeMux()

	mux.Handle("/", http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
		clientAddr := r.Header.Get("X-Forwarded-For")
		log.Printf("%s -> %s -> %s", clientAddr, r.RemoteAddr, r.URL)
		_, _ = w.Write(index)
	}),

	)

	srv := &http.Server{
		Addr:         addr,
		Handler:      mux,
		IdleTimeout: time.Minute,
		ReadHeaderTimeout: 30 * time.Second,
	}

	go func() {
		for {
			if <-c == os.Interrupt {
				srv.Close()
				return
			}
		}
	}()

	fmt.Printf("Listening on %s ...\\n", srv.Addr)
	err := srv.ListenAndServe()
	if err == http.ErrServerClosed {
		err = nil
	}
	return err
}
```

*Listing 10-10: The main logic of the backend service (* backend/main .go *)* The web service receives all requests from Caddy, no matter which client originated the request. Likewise, it sends all responses back to Caddy,

which then routes the response to the right client. Conveniently, Caddy adds

an X-Forwarded-For header 1 to each request with the originating client’s IP

address. Although you don’t do anything other than log this information,

your backend service could use this IP address to differentiate between cli-

ent requests. The service could deny requests based on client IP address, for

example.

The handler writes a slice of bytes 2 to the response that has HTML

defined in Listing 10-11.

```go
var index = []byte(`<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Caddy Backend Test</title>
<link href="/style.css" rel="stylesheet">
</head>
<body>
<p><img src="/hiking.svg" alt="hiking gopher"></p>
</body>
</html>`)
```

*Listing 10-11: The index HTML served by the backend service (* backend/main .go *)* The /style.css 1 and /hiking.svg 2 resources do not include a full

URL (such as *http://localhost:2020/style.css*) because the backend web service does not know anything about Caddy or how clients access Caddy. When

you exclude the scheme, hostname, and port number in the resource

address, the client’s web browser should encounter /style.css in the HTML

and prepend the scheme, hostname, and port number it used for the initial

request before sending the request to Caddy. For that all to work, you need

to configure Caddy in the next section to send some requests to the backend

web service and serve static files for the rest of the requests.

***Setting Up Caddy’s Configuration***

As mentioned earlier in the chapter, Caddy uses JSON as its native configu-

ration format. You could certainly write your configuration in JSON, but

you’ve already written a perfectly good configuration adapter that allows

you to use TOML, so you’ll implement that instead.

**234** Chapter 10

You want to configure Caddy to reverse-proxy requests to your backend web service and serve static files from the *files* subdirectory. You’ll need two routes: one to the backend web service and one for static files.

Let’s start by defining your server configuration in a file named *caddy.toml*

(Listing 10-12).

```toml
1 [apps.http.servers.test_server]
listen = [
'localhost:2020',
]
```

*Listing 10-12: Caddy test server configuration (* caddy .toml *)*

Your TOML adapter directly converts TOML to JSON. Therefore, you

need to make sure you’re using the same namespaces Caddy expects. The

namespace for your server is apps.http.servers.test_server 1. (For simplicity,

you’ll refer to this namespace simply as test_server from here on out.)

It listens for incoming connections on port 2020 of localhost.

***Adding a Reverse-Proxy to Your Service***

Caddy includes a powerful reverse-proxy handler that makes quick work of

sending incoming requests to your backend web service. Just as in the server

implementation in the preceding chapter, Caddy matches an incoming

request to a route and then passes the request onto the associated handler.

Listing 10-13 adds a route and a reverse-proxy handler to the *caddy.toml* file.

```toml
1 [[apps.http.servers.test_server.routes]]
2 [[apps.http.servers.test_server.routes.match]]
path = [
'/backend',
'/backend/*',
]
3 [[apps.http.servers.test_server.routes.handle]]
handler = 'reverse_proxy'
5 [[apps.http.servers.test_server.routes.handle.upstreams]]
dial = 'localhost:8080'
```

*Listing 10-13: Adding a reverse proxy to the backend service (* caddy .toml *)* The test_server configuration includes a routes array 1, and each route

in the array has zero or more matchers 2. A *matcher* is a special module that allows you to specify matching criteria for incoming requests, like the http

.ServeMux.Handle method’s pattern matching discussed in the preceding

chapter. Caddy includes matcher modules that allow you to consider each

part of a request.

For this route, you add a single matcher that matches any request for the

absolute path */backend* or any path starting with */backend/* 3. The *\** character is a wildcard that tells Caddy you want to match on the */backend/* prefix. For example, a request for the resource */backend/this/is/a/test* will also match.

Caddy: A Contemporary Web Server **235**

The route may have one or more handlers 4. Here, you tell Caddy you want to send all matching requests to the reverse-proxy handler. The reverse-proxy handler needs to know where to send the requests. You specify an

upstream entry 5 with its dial property set to the backend server’s socket

address 6.

***Serving Static Files***

You relied on the http.FileServer to serve static files for you in the preceding

chapter. Caddy exposes similar functionality with its file_server handler.

Listing 10-14 adds a second route to your *caddy.toml* file for serving static files.

```toml
1 [[apps.http.servers.test_server.routes]]
2 [[apps.http.servers.test_server.routes.handle]]
handler = 'restrict_prefix'
prefix = '.'
3 [[apps.http.servers.test_server.routes.handle]]
handler = 'file_server'
root = './files'
index_names = [
'index.html',
]
```

*Listing 10-14: Adding a default route to serve static files (* caddy .toml *)* Unlike the route you added in Listing 10-13, this route 1 does not

include any matchers. As such, Caddy would send every request to this

route’s handler if the request didn’t match previous routes. In other words,

this route is your default route, and so its position in the file matters. If
