
web browsers support HTTP/1.1 at a minimum, so you’re unlikely to use HTTP/1.0 at all.

Table 8-1 demonstrates the retrieval of an HTML document and the subsequent GET calls of all resources specified in that document.

**Table 8-1:** Retrieving Additional Resources After Requesting the Index HTML Document **Status**

**Method Domain**

**Resource**

**Type**

**Bytes transferred Duration of transfer**

200

GET

`/`

HTML

1 .83KB

49 ms

200

GET

`main.min.css`

CSS

1 .30KB

20 ms

200

GET

`code.css`

CSS

0 .99KB

20 ms

304

GET

`avatar.jpeg`

JPEG

0 bytes

0 ms

404

GET

`favicon.ico`

IMG

0 bytes

0 ms

**172** Chapter 8

The initial GET request for `https://woodbeck.net/` successfully retrieved the HTML document specified by the default resource. This HTML document included links to additional resources necessary to properly render the page, so the web browser requested those too. Since this transfer used HTTP/1.1, the web browser used the same TCP connection to retrieve the remaining resources. The web server instructed the web browser to use its cached copy of `avatar.jpeg`, since that resource hadn’t changed since the last time the web browser received it. The web server was unable to find the `favicon.ico` file, so it returned a 404 status code to the web browser.

The latest version of HTTP, HTTP/2, aims to further reduce latency. In addition to reusing the same TCP connection for subsequent requests, the HTTP/2 server can proactively push resources to the client. If the conversation in Table 8-1 occurred over HTTP/2, it may have transpired like this. The client requested the default resource. The server responded with the default resource. But since the server knew that the default resource had dependent resources, it *pushed* those resources to the client without the client’s needing to make separate requests for each resource.

The Go HTTP client and server transparently support HTTP/1.0, HTTP/1.1, and HTTP/2, meaning that you can write your code to retrieve and serve resources while letting code in Go’s net/http package negotiate the optimal HTTP version. However, while the Go HTTP/2 server implementation can push resources to clients, the Go HTTP/2 client implementation cannot yet consume those server pushes.

**Retrieving Web Resources in Go**

Just like your web browser, Go can communicate with web servers by using the net/http package’s HTTP client. Unlike your web browser, Go won’t directly render an HTML page to your screen. Instead, you could use Go to scrape data from websites (such as financial stock details), submit form data, or interact with APIs that use HTTP for their application protocol, to name a few examples.

Despite the simplicity of making HTTP requests in Go, you’ll have to handle some client-side pitfalls. You’ll learn about these pitfalls shortly.

First, let’s look at a simple example request.

***Using Go’s Default HTTP Client***

The net/http package includes a default client that allows you to make one-off HTTP requests. For example, you can use the http.Get function to send a GET request to a given URL.

Listing 8-2 demonstrates one way you can retrieve the current time from a trusted authority— `time.gov`’s web server—and compare it with the local time on your computer. This will give you a rough idea of how far ahead or behind the local time is on your computer. You certainly wouldn’t want to rely on this method for any sort of forensics, but the example serves to demonstrate the Go HTTP client workflow by using a HEAD request and response.

Writing HTTP Clients **173**

package main

import (

"net/http"

"testing"

"time"

)

func TestHeadTime(t *testing.T) {

resp, err := 1http.Head("https://www.time.gov/")

if err != nil {

t.Fatal(err)

}

\_ = 2resp.Body.Close() // Always close this without exception.

now := time.Now().Round(time.Second)

date := 3resp.Header.Get("Date")

if date == "" {

t.Fatal("no Date header received from time.gov")

}

dt, err := time.Parse(time.RFC1123, date)

if err != nil {

t.Fatal(err)

}

t.Logf("time.gov: %s (skew %s)", dt, now.Sub(dt))

}

*Listing 8-2: Retrieving a timestamp from* time .gov *(* time_test .go *)* The net/http package includes a few helper functions to make GET, HEAD,

or POST requests. Here, we use the http.Get function 1 to *https://www.time.gov/*

to retrieve the default resource. Go’s HTTP client automatically upgrades to

HTTPS for you because that’s the protocol indicated by the URL’s scheme.

Although you don’t read the contents of the response body, you must close it 2. The next section covers why you need to close the response body in

every case.

Now that you have a response, you retrieve the Date header 3, which

indicates the time at which the server created the response. You can then

use this value to calculate the clock skew of your computer. Granted, you

lose accuracy because of latency between the server’s generating the header

and your code’s processing it, as well as the lack of nanosecond resolution

of the Date header itself.

***Closing the Response Body***

As mentioned earlier, HTTP/1.1 allows the client to maintain a TCP connection with a server for multiple HTTP requests (we call this *keepalive* *support*). Even so, the client cannot reuse a TCP session when unread bytes from the previous response remain on the wire. Go’s HTTP client automatically drains the response body when you close it. This allows your code to reuse the underlying TCP session if you are diligent about closing

every response body.

Let’s revisit the response from Listing 8-1 to see how Go parses the

response (Listing 8-3).

1  HTTP/1.1 200 OK

Accept-Ranges: none

Vary: Accept-Encoding

Content-Type: text/plain

Date: Mon, 02 Jan 2006 15:04:05 MST

Expires: Mon, 02 Jan 2006 15:04:05 MST

Cache-Control: private, max-age=0

Last-Modified: Mon, 02 Jan 2006 15:04:05 MST

X-Content-Type-Options: nosniff

Server: sffe

X-XSS-Protection: 0

Transfer-Encoding: chunked

2  User-agent: \*

Disallow: /search

Allow: /search/about

Allow: /search/static

Allow: /search/howsearchworks

*\--snip--*

*Listing 8-3: Parsing the HTTP response*

Go’s HTTP client reads the response status and headers 1 from the

network socket, and this data immediately becomes available to your code as

part of the response object. The client doesn’t automatically read the response

body, however 2. The body remains unconsumed until your code explicitly

reads it or until you close it and Go implicitly drains any unread bytes.

The Go HTTP client’s implicit draining of the response body on closing

could potentially bite you. For example, let’s assume you send a GET request

for a file and receive a response from the server. You read the response’s

Content-Length header and realize the file is much larger than you antici-

pated. If you close the response body without reading any of its bytes, Go

will download the entire file from the server as it drains the body regardless.

A better alternative would be to send a HEAD request to retrieve the Content-

Length header. This way, no unread bytes exist in the response body, so closing

the response body will not incur any additional overhead while draining it.

You properly closed the response body in Listing 8-2, so the Go HTTP client

could reuse the TCP session if you made additional calls in the future.

On the rare occasion that you make an HTTP request and want to

explicitly drain the response body, the most efficient way is to use the

io.Copy function:

\_, \_ = io.Copy(ioutil.Discard, response.Body)

\_ = response.Close()

Writing HTTP Clients **175**

The io.Copy function drains the response.Body by reading all bytes from it and writing those bytes to ioutil.Discard. As its name indicates, ioutil.Discard

is a special io.Writer that discards all bytes written to it.
