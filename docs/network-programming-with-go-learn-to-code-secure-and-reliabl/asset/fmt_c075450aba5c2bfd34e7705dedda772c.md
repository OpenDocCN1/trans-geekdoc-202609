
The third test case 3 a sends a HEAD request to the HTTP server. The

handler returned by the handlers.DefaultHandler function, which you’ll

explore shortly, does not handle the HEAD method. Therefore, it returns a

405 Method Not Allowed status code and an empty response body.

Listing 9-3 continues the code in Listing 9-2 and runs through each

test case.

\--snip--

for i, c := range testCases {

r, err := 1http.NewRequest(c.method, path, c.body)

if err != nil {

t.Errorf("%d: %v", i, err)

continue

}

resp, err := 2client.Do(r)

if err != nil {

t.Errorf("%d: %v", i, err)

continue

}

if resp.StatusCode != c.code {

t.Errorf("%d: unexpected status code: %q", i, resp.Status)

}

b, err := 3ioutil.ReadAll(resp.Body)

if err != nil {

t.Errorf("%d: %v", i, err)

continue

}

\_ = 4resp.Body.Close()

if c.response != string(b) {

t.Errorf("%d: expected %q; actual %q", i, c.response, b)

}

}

**190** Chapter 9

 if err := 5srv.Close(); err != nil {

t.Fatal(err)

}

}

*Listing 9-3: Sending test requests to the HTTP server (server_test .go)* First, you create a new request, passing the parameters from the test

case 1. Next, you pass the request to the client’s Do method 2, which

returns the server’s response. You then check the status code and read in

the entire response body 3. You should be in the habit of consistently clos-

ing the response body if the client did not return an error 4, even if the

response body is empty or you ignore it entirely. Failure to do so may pre-

vent the client from reusing the underlying TCP connection.

Once all tests complete, you call the server’s Close method 5. This

causes its Serve method in Listing 9-1 to return, stopping the server. The

Close method abruptly closes client connections. You’ll see an example of

the HTTP server’s graceful shutdown support when we discuss HTTP/2

pushes later in this chapter.

Go’s HTTP server supports a few other features, which we’ll explore in

the following sections. It can proactively serve, or push, resources to clients.

It also offers graceful shutdown support. Abruptly shutting down your web

server may leave some clients in an awkward state if they were waiting for

a response when you stopped the server, because those clients will never

receive a response. Graceful shutdowns allow for all pending responses to

reach each client before the server is stopped.

***Clients Don’t Respect Your Time***

Just as I recommended setting the client’s time-out values, I recommend

that you manage the various server time-out values, for the simple reason

that clients won’t otherwise respect your server’s time. A client can take its

sweet time sending a request to your server. Meanwhile, your server uses

resources waiting to receive the request in its entirety. Likewise, your server

is at the client’s mercy when it sends the response because it can send data

only as fast as the client reads it (or can send only as much as there is TCP

buffer space available). Avoid letting the client dictate the duration of a

request-response life cycle.

Listing 9-1 includes a server instance with two of its time-out values

specified: the length of time clients can remain idle between requests and

how long the server should wait to read a request header:

srv := &http.Server{

Addr: "127.0.0.1:8081",

Handler: mux,

IdleTimeout: 5 \* time.Minute,

ReadHeaderTimeout: time.Minute,

}

Building HTTP Services **191**

Although several time-out fields on the http.Server are available to you, I recommend setting only the IdleTimeout and ReadHeaderTimeout fields. The

IdleTimeout field dictates how long the server will keep its side of the TCP

socket open while waiting for the next client request when the communica-

tion uses keepalives. The ReadHeaderTimeout value determines how long the

server will wait to finish reading the request headers. Keep in mind that this

duration has no bearing on the time it takes to read the request body.

If you want to enforce a time limit for reading an incoming request

across all handlers, you could manage the request deadline by using the

ReadTimeout field. If the client hasn’t sent the complete request (the headers

and body) by the time the ReadTimeout duration elapses, the server ends the

TCP connection. Likewise, you could give the client a finite duration in

which to send the request and read the response by using the WriteTimeout

field. The ReadTimeout and WriteTimeout values apply to all requests and

responses because they dictate the ReadDeadline and WriteDeadline values

of the TCP socket, as discussed i[n Chapter 4.](#index_split_001.html#p95)

These blanket time-out values may be inappropriate for handlers that

expect clients to send large files in a request body or handlers that indefinitely stream data to the client. In these two examples, the request or response may

abruptly time out even if everything went ahead as expected. Instead, a good

practice is to rely on the ReadHeaderTimeout value. You can separately man-

age the time it takes to read the request body and send the response using

middleware or handlers. This gives you the greatest control over request and

response durations per resource. You’ll learn how to manage the request-

response duration by using middleware in [“Middleware” on page 202.](#index_split_004.html#p224)

***Adding TLS Support***

HTTP traffic is plaintext by default, but web clients and servers can

use HTTP over an encrypted TLS connection, a combination known

as *HTTPS*. Go’s HTTP server enables HTTP/2 support over TLS connec-

tions only, but enabling TLS is a simple matter. You need to modify only

two lines from Listing 9-1’s server implementation: the port number and

the Serve method:

srv := &http.Server{

Addr: 1"127.0.0.1:8443",

Handler: mux,

IdleTimeout: 5 \* time.Minute,

ReadHeaderTimeout: time.Minute,

}

l, err := net.Listen("tcp", srv.Addr)

if err != nil {

t.Fatal(err)

}

go func() {

2 err := srv.ServeTLS(l, "cert.pem", "key.pem")

if err != http.ErrServerClosed {

**192** Chapter 9

 t.Error(err)

}

}()

Technically, you don’t need to change the port number 1, but the con-

vention is to serve HTTPS over port 443, or an augmentation of port 443,

like 8443. Using the server’s ServeTLS method, you instruct the server to use

TLS over HTTP 2. The ServeTLS method requires the path to both a certifi-

cate and a corresponding private key. I recommend you check out the mkcert

project at *https://github.com/FiloSottile/mkcert/* to get a key pair. You can use mkcert to create locally trusted key pairs for development purposes only. For

production use, you should consider using and supporting Let’s Encrypt at

*https://letsencrypt.org/*.

**Handlers**

When a client sends a request to an HTTP server, the server needs to figure

out what to do with it. The server may need to retrieve various resources

or perform an action, depending on what the client requests. A common

design pattern is to specify bits of code to handle these requests, known as

*handlers*. You may have a handler that knows how to retrieve an image and

another handler that knows how to retrieve information from a database.

We’ll discuss how the server figures out which handler is most apt for each

request i[n “Multiplexers” on page 207](#index_split_004.html#p229).

In Go, handlers are objects that implement the http.Handler interface.

They read client requests and write responses. The http.Handler interface

consists of a single method to receive both the response and the request:

type Handler interface {

ServeHTTP(http.ResponseWriter, \*http.Request)

}

Any object that implements the http.Handler interface may handle client

requests, as far as the Go HTTP server is concerned. We often define han-

dlers as functions, as in this common pattern:

handler := http.HandlerFunc(

func(w http.ResponseWriter, r \*http.Request) {

\_, \_ = w.Write(\[\]byte("Hello, world!"))

},
)
