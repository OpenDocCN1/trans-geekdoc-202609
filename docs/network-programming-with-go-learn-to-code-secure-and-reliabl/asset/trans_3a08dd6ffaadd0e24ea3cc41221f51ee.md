
as calling `dbHandler` and passing in a pointer to a SQL database object 3.

This approach can get a bit cumbersome if you have multiple handlers

that require access to the same database object or your design is evolving

and you’re likely to require access to additional objects in the future. A

more extensible approach is to use a struct whose fields represent objects

and data you want to access in your handler and to define your handlers

as struct methods (see Listing 9-9). Injecting dependencies involves adding

struct fields instead of modifying a bunch of closure definitions.

type Handlers struct {

db \*sql.DB

log \*log.Logger

}

func (h \*Handlers) Handler1() http.Handler {

return http.HandlerFunc(

func(w http.ResponseWriter, r \*http.Request) {

err := h.db.Ping()

if err != nil {

h.log.Printf("db ping: %v", err)

}

// do something with the database here

},

)

}

func (h \*Handlers) Handler2() http.Handler {

return http.HandlerFunc(

func(w http.ResponseWriter, r \*http.Request) {

// ...

},

)

}

*Listing 9-9: Injecting dependencies into multiple handlers defined as struct methods* You define a struct that contains pointers to a database object and a

logger 1. Any method you define on the handler now has access to these

objects 2. If your handlers require access to additional resources, you simply

add fields to the struct.

Listing 9-10 illustrates how to use the Handlers struct.

h := &Handlers{

db: 1db,

log: log.New(os.Stderr, "handlers: ", log.Lshortfile),

}

http.Handle("/one", h.Handler1())

http.Handle("/two", h.Handler2())

*Listing 9-10: Initializing the Handlers struct and using its handlers*

Building HTTP Services **201**

Assuming db 1 is a pointer to a sql.DB object, you initialize a Handlers object and use its methods with http.Handle, for example.

**Middleware**

Middleware comprises reusable functions that accept an http.Handler and

return an http.Handler:

func(http.Handler) http.Handler

You can use middleware to inspect the request and make decisions

based on its content before passing it along to the next handler. Or you

might use the request content to set headers in the response. For example,

the middleware could respond to the client with an error if the handler

requires authentication and an unauthenticated client sent the request.

Middleware can also collect metrics, log requests, or control access to

resources, to name a few uses. Best of all, you can reuse them on multiple

handlers. If you find yourself writing the same handler code over and

over, ask yourself if you can put the functionality into middleware and

reuse it across your handlers.

Listing 9-11 shows just a few uses of middleware, such as enforcing

which methods the handler allows, adding headers to the response, or

performing ancillary functions like logging.

func Middleware(next http.Handler) http.Handler {

return 1http.HandlerFunc(

2 func(w http.ResponseWriter, r \*http.Request) {

if r.Method == http.MethodTrace {

3http.Error(w, "Method not allowed",

http.StatusMethodNotAllowed)

}

4w.Header().Set("X-Content-Type-Options", "nosniff")

start := time.Now()

5next.ServeHTTP(w, r)

6log.Printf("Next handler duration %v", time.Now().Sub(start))

},

)

}

*Listing 9-11: Example middleware function*

The Middleware function uses a common pattern you first saw in

Listing 9-4: it defines a function that accepts an http.ResponseWriter and

a pointer to an http.Request 2 and wraps it with an http.HandlerFunc 1.

In most cases, middleware calls the given handler 5. But in some cases

that may not be proper, and the middleware should block the next handler

and respond to the client itself 3. Likewise, you may want to use middle-

ware to collect metrics, ensure specific headers are set on the response 4,

or write to a log file 6.

**202** Chapter 9

Listing 9-11 is a contrived example. I don’t recommend performing so many tasks in a single middleware function. Instead, it’s best to follow the

Unix philosophy and write minimalist middleware, with each function doing

one thing very well. Ideally, you would split the middleware in Listing 9-11

into three middleware functions to check the request method and respond

to the client 3, enforce response headers 4, and collect metrics 6.

The net/http package includes useful middleware to serve static files,

redirect requests, and manage request time-outs. Let’s dig into their source

code to see how you might use them. In addition to these standard library

functions, check out the middleware at *https://go.dev/*.

***Timing Out Slow Clients***

As I mentioned earlier, it’s important not to let clients dictate the duration

of a request-response life cycle. Malicious clients could use this leniency

to their ends and exhaust your server’s resources, effectively denying ser-

vice to legit clients. Yet at the same time, setting read and write time-outs

server-wide makes it hard for the server to stream data or use different

time-out durations for each handler.

Instead, you should manage time-outs in middleware or individual

handlers. The net/http package includes a middleware function that allows

you to control the duration of a request and response on a per-handler

basis. The http.TimeoutHandler accepts an http.Handler, a duration, and a

string to write to the response body. It sets an internal timer to the given

duration. If the http.Handler does not return before the timer expires, the

http.TimeoutHandler blocks the http.Handler and responds to the client with

a 503 Service Unavailable status.

Listing 9-12 uses the http.TimeoutHandler to wrap an http.Handler that

mimics a slow client.

package middleware

import (

"io/ioutil"

"net/http"

"net/http/httptest"

"testing"

"time"

)

func TestTimeoutMiddleware(t \*testing.T) {

handler := 1http.TimeoutHandler(

http.HandlerFunc(func(w http.ResponseWriter, r \*http.Request) {

w.WriteHeader(http.StatusNoContent)

2time.Sleep(time.Minute)

}),

time.Second,

"Timed out while reading response",

)

r := httptest.NewRequest(http.MethodGet, "http://test/", nil)

w := httptest.NewRecorder()

Building HTTP Services **203**

 handler.ServeHTTP(w, r)

resp := w.Result()

if resp.StatusCode != 3http.StatusServiceUnavailable {

t.Fatalf("unexpected status code: %q", resp.Status)

}

b, err := 4ioutil.ReadAll(resp.Body)

if err != nil {

t.Fatal(err)

}

\_ = resp.Body.Close()

5 if actual := string(b); actual != "Timed out while reading response" {

t.Logf("unexpected body: %q", actual)

}

}

*Listing 9-12: Giving clients a finite time to read the response (* middleware/timeout_test .go *)* Despite its name, http.TimeoutHandler is middleware that accepts an

http.Handler and returns an http.Handler 1. The wrapped http.Handler

purposefully sleeps for a minute 2 to simulate a client’s taking its time

to read the response, preventing the http.Handler from returning. When

the handler doesn’t return within one second, http.TimeoutHandler sets the

response status code to 503 Service Unavailable 3. The test reads the

entire response body 4, properly closes it, and makes sure the response

body has the string written by the middleware 5.

***Protecting Sensitive Files***

Middleware can also keep clients from accessing information you’d like to

keep private. For example, the http.FileServer function simplifies the pro-

cess of serving static files to clients, accepting an http.FileSystem interface,

and returning an http.Handler. The problem is, it won’t protect against serv-

ing up potentially sensitive files. Any file in the target directory is fair game.

By convention, many operating systems store configuration files or other

sensitive information in files and directories prefixed with a period and

then hide these dot-prefixed files and directories by default. (This is partic-

ularly true in Unix-compatible systems.) But the http.FileServer will gladly

