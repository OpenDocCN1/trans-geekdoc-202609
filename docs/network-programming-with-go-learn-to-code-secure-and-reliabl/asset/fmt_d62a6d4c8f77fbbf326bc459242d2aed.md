
prefix matches. In other words, the multiplexer will look for the longest reg-
istered pattern that comes at the beginning of the request’s URL path. For
example, */hello/there/* is a prefix of */hello/there/you* but not of */hello/you*.

Go’s multiplexer can also redirect a URL path that doesn’t end in a for-
ward slash, such as */hello/there*. In those cases, the http.ServeMux first attempts to find a matching absolute path. If that fails, the multiplexer appends a
forward slash, making the path */hello/there/*, for example, and responds to the client with it. This new path becomes a permanent redirect. You’ll see
an example of this in Listing 9-16.

Now that you’ve defined routes for the multiplexer, it’s ready to use.

But there’s one issue with the handlers: none of them drain and close the
request body. This isn’t a big concern in a test like this, but you should stick
to best practices, nonetheless. If you don’t do so in a real scenario, you may
cause increased overhead and potential memory leaks. Here, you use middle-
ware 1 to drain and close the request body. In the drainAndClose middleware,
you call the next handler first 2 and then drain and close the request body.

There is no harm in draining and closing a previously drained and closed
request body.

Listing 9-16 tests a series of requests against Listing 9-15’s multiplexer.

*\--snip--*

testCases := \[\]struct {
{
path string
response string
code int
}
{
1 {"http://test/", "", http.StatusNoContent},
{"http://test/hello", "Hello friend.", http.StatusOK},
{"http://test/hello/there/", "Why, hello there.", http.StatusOK},
2 {"http://test/hello/there",
**208** Chapter 9
"<a href=\\"/hello/there/\\">Moved Permanently</a>.\\n\\n", http.StatusMovedPermanently},
3 {"http://test/hello/there/you", "Why, hello there.", http.StatusOK},
4 {"http://test/hello/and/goodbye", "", http.StatusNoContent},
{"http://test/something/else/entirely", "", http.StatusNoContent},
{"http://test/hello/you", "", http.StatusNoContent},
}

for i, c := range testCases {
{
r := httptest.NewRequest(http.MethodGet, c.path, nil)
w := httptest.NewRecorder()
mux.ServeHTTP(w, r)
resp := w.Result()
if actual := resp.StatusCode; c.code != actual {
t.Errorf("%d: expected code %d; actual %d", i, c.code, actual)
}
b, err := 5ioutil.ReadAll(resp.Body)
if err != nil {
t.Fatal(err)
}
\_ = 6resp.Body.Close()
if actual := string(b); c.response != actual {
t.Errorf("%d: expected response %q; actual %q", i,
c.response, actual)
}
}
}

}

*Listing 9-16: Running through a series of test cases and verifying the response status code*
*and body (* mux_test .go *).*

The first three test cases 1, including the request for the */hello/there/*

path, match exact patterns registered with the multiplexer. But the fourth

test case 2 is different. It doesn’t have an exact match. When the multi-
plexer appends a forward slash to it, however, it discovers that it exactly

matches a registered pattern. Therefore, the multiplexer responds with a

301 Moved Permanently status and a link to the new path in the response

body. The fifth test case 3 matches the */hello/there/* subtree and receives the Why, hello there. response. The last three test cases 4 match the default

path of */* and receive the 204 No Content status.

Just as the test relies on middleware to drain and close the request

body, it drains 5 and closes 6 the response body.

**HTTP/2 Server Pushes**

The Go HTTP server can push resources to clients over HTTP/2, a fea-
ture that has the potential to improve efficiency. For example, a client

may request the home page from a web server, but the client won’t know it

needs the associated style sheet and images to properly render the home

Building HTTP Services **209**

![Image 2](index-232_1.png)

page until it receives the HTML in the response. An HTTP/2 server can

proactively send the style sheet and images along with the HTML in the

response, saving the client from having to make subsequent calls for those

resources. But server pushes have the potential for abuse. This section

shows you how to use server pushes and then discusses cases when you

should avoid doing so.

***Pushing Resources to the Client***

Let’s retrieve the HTML page in Listing 9-17 over HTTP/1.1, then retrieve

the same page over HTTP/2 and compare the differences.

<!DOCTYPE html>

<html lang="en">

<head>

<meta charset="UTF-8">

<title>H2 Server Push</title>

1 <link href="/static/style.css" rel="stylesheet">

</head>

<body>

2 <img src="/static/hiking.svg" alt="hiking gopher">

</body>

</html>

*Listing 9-17: Simple index file having links to two resources (* files/index .html *)* This HTML file requires the browser to retrieve two more resources,

a style sheet 1 and an SVG image 2, to properly show the entire page.

Figure 9-2 shows Google Chrome’s request accounting for the HTML when

served using HTTP/1.1.

*Figure 9-2: Downloaded index page and associated resources over HTTP/1.1*

Aside from the *favicon.ico* file, which Chrome retrieves on its own, the

browser made three requests to retrieve all required resources—one for

the HTML file, one for the style sheet, and one for the SVG image. Any

web browser requesting the *index.html* file ( *localhost* in Figure 9-2) will also request the *style.css* and *hiking.svg* files to properly render the *index.html* file.

The web server could improve efficiency and proactively push these two

files to the web browser, since it knows the web browser will inevitably

request them. This proactive approach by the web server would save the

web browser from the overhead of having to make two more requests.

**210** Chapter 9

![Image 3](index-233_1.png)

Figure 9-3 shows the same retrieval using HTTP/2. In this case, the

server pushes the *style.css* and *hiking.svg* files.

*Figure 9-3: Downloaded index page with resources pushed by the server side*

The client receives all three resources after a single request to the server

for the *index.html* file. The Initiator column in Figure 9-3 shows that Chrome retrieved the resources from its dedicated push cache.

Let’s write a command line executable that can push resources to clients.

Listing 9-18 shows the first part of the program.

package main

import (

"context"

"flag"

"log"

"net/http"

"os"

"os/signal"

"path/filepath"

"time"

"github.com/awoodbeck/gnp/ch09/handlers"

"github.com/awoodbeck/gnp/ch09/middleware"

)

var (

addr = flag.String("listen", "127.0.0.1:8080", "listen address") 1 cert = flag.String("cert", "", "certificate") 2 pkey = flag.String("key", "", "private key") files = flag.String("files", "./files", "static file directory")

)

func main() {

flag.Parse()

err := 3run(\*addr, \*files, \*cert, \*pkey)

if err != nil {
log.Fatal(err)
}

log.Println("Server gracefully shutdown")

}

*Listing 9-18: Command line arguments for the HTTP/2 server (* server .go *)* Building HTTP Services **211**

The server needs the path to a certificate 1 and a corresponding private key 2 to enable TLS support and allow clients to negotiate HTTP/2

with the server. If either value is empty, the server will listen for plain HTTP

connections. Next, pass the command line flag values to a run function 3.

The run function, defined in Listing 9-19, has the bulk of your server’s

logic and ultimately runs the web server. Breaking this functionality into

a separate function eases unit testing later.

*\--snip--*

func run(addr, files, cert, pkey string) error {
mux := http.NewServeMux()

1 mux.Handle("/static/",

http.StripPrefix("/static/",

middleware.RestrictPrefix(

".", http.FileServer(http.Dir(files)),

),

),

)

2 mux.Handle("/",

handlers.Methods{
http.MethodGet: http.HandlerFunc(
func(w http.ResponseWriter, r \*http.Request) {
3 if pusher, ok := w.(http.Pusher); ok {
targets := \[\]string{
4"/static/style.css",
"/static/hiking.svg",
}
for \_, target := range targets {
