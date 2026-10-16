
ting its InsecureSkipVerify field to true 3. I don’t recommend you entertain

enabling InsecureSkipVerify for anything other than debugging. Shipping

code with this enabled is a code smell in my opinion. You’ll learn a bet-

ter alternative later in this chapter when we discuss a concept known as

*certificate pinning*. As the field name implies, enabling it makes your client inherently insecure and susceptible to man-in-the-middle attacks, since it

now blindly trusts any certificate a server offers up. If you make the same

call with your newly naive client, you’ll see that it happily negotiates TLS

with the server.

***TLS over TCP***

TLS is stateful; a client and a server negotiate session parameters during the

initial handshake only, and once they’ve agreed, they exchange encrypted

TLS records for the duration of the session. Since TCP is also stateful, it’s the ideal transport layer protocol with which to implement TLS, because you can

leverage TCP’s reliability guarantees to maintain your TLS sessions.

Securing Communications with TLS **247**

Let’s take the application protocol out of the picture for a moment and learn how to establish a TLS connection over TCP. Listing 11-3 demonstrates

how to use the crypto/tls package to initiate a TLS connection with a few

lines of code.

*\--snip--*

func TestClientTLSGoogle(t \*testing.T) {

conn, err := 1tls.DialWithDialer(

&net.Dialer{Timeout: 30 \* time.Second},

"tcp",

"www.google.com:443",

&tls.Config{

CurvePreferences: \[\]tls.CurveID{tls.CurveP256},

MinVersion: tls.VersionTLS12,

},

)

if err != nil {

t.Fatal(err)

}

state := 2conn.ConnectionState()

t.Logf("TLS 1.%d", state.Version-tls.VersionTLS10)

t.Log(tls.CipherSuiteName(state.CipherSuite))

t.Log(state.VerifiedChains\[0\]\[0\].Issuer.Organization\[0\])

\_ = conn.Close()

}

*Listing 11-3: Starting a TLS connection with* www .google .com *(* tls\_client\_test .go *)* The tls.DialWithDialer function 1 accepts a \*net.Dialer, a network, an

address, and a \*tls.Config. Here, you give your dialer a time-out of 30 sec-

onds and specify recommended TLS settings. If successful, you can inspect

the connection’s state 2 to glean details about your TLS connection.

Listing 11-4 shows the output of Listing 11-3’s test.

$ **go test -race -run TestClientTLSGoogle -v ./...**

\=== RUN TestClientTLSGoogle

TestClientTLSGoogle: tls\_client\_test.go:89: TLS 1.3

TestClientTLSGoogle: tls\_client\_test.go:90: TLS\_AES\_128\_GCM\_SHA256

TestClientTLSGoogle: tls\_client\_test.go:91: Google Trust Services

\--- PASS: TestClientTLSGoogle (0.31s)

PASS

*Listing 11-4: Running the TestClientTLSGoogle test*

Your TLS client is using the TLS\_AES\_128\_GCM\_SHA256 cipher suite

over TLS version 1.3. Notice that tls.DialWithDialer did not object to the

server’s certificate. The underlying TLS client used the operating system’s

trusted certificate storage and confirmed that *www.google.com*’s certificate is signed by a trusted CA—Google Trust Services, in this example.

**248** Chapter 11

 ***Server-side TLS***

The server-side code isn’t much different from what you’ve learned thus

far. The main difference is that the server needs to present a certificate to the client as part of the handshake process. You can create one with the *generate\_*

*cert.go* file found in Go’s *src/crypto/tls* subdirectory. For production use, you’re better off using certificates from Let’s Encrypt or another certificate authority.

You can use the LEGO library ( *https://github.com/go-acme/lego/*) to add certificate management to your services. Generate a new cert and private key, like so:

$ **go run $GOROOT/src/crypto/tls/generate\_cert.go -host localhost -ecdsa-curve P256**

This command creates a certificate named *cert.pem* with the hostname

*localhost* and a private key named *key.pem*. The rest of the code in this section assumes that both files exist in the current directory.

Keeping with the tradition of earlier chapters, Listing 11-5 includes the

first bit of code for a TLS-only echo server.

package ch11

import (

"context"

"crypto/tls"

"fmt"

"net"

"time"

)

func NewTLSServer(ctx context.Context, address string,

maxIdle time.Duration, tlsConfig \*tls.Config) \*Server {

return &Server{

ctx: ctx,

ready: make(chan struct{}),

addr: address,

maxIdle: maxIdle,

tlsConfig: tlsConfig,

}

}

type Server struct {

ctx context.Context

ready chan struct{}

addr string

maxIdle time.Duration

tlsConfig \*tls.Config

}

func (s \*Server) 1Ready() {

if s.ready != nil {

<-s.ready

}

}

*Listing 11-5: Server struct type and constructor function (* tls\_echo .go *)* Securing Communications with TLS **249**

The Server struct has a few fields used to record its settings, its TLS

configuration, and a channel to signal when the server is ready for incoming

connections. You’ll write a test case and use the Ready method 1 a little later

in this section to block until the server is ready to accept connections.

The NewTLSServer function accepts a context for stopping the server, an

address, the maximum duration the server should allow connections to

idle, and a TLS configuration. Although controlling for idling clients isn’t

related to TLS, you’ll use the maximum idle duration to push the socket

deadline forward, as in [Chapter 3](#index_split_001.html#p67).

Servers you used in earlier chapters rely on the separate concepts of lis-

tening and serving. Often, you’ll invoke a helper function that will do both

for you, such as the net/http server’s ListenAndServe method. Listing 11-6

adds a similar method to the echo server.

*\--snip--*

func (s \*Server) ListenAndServeTLS(certFn, keyFn string) error {

if s.addr == "" {

s.addr = "localhost:443"

}

l, err := net.Listen("tcp", s.addr)

if err != nil {

return fmt.Errorf("binding to tcp %s: %w", s.addr, err)

}

if s.ctx != nil {

go func() {

<-s.ctx.Done()

\_ = l.Close()

}()

}

return s.ServeTLS(l, certFn, keyFn)

}

*Listing 11-6: Adding methods to listen and serve and signal the server’s readiness for connections (* tls\_echo .go *)*

The ListenAndServe method accepts full paths to a certificate and a

private key and returns an error. It creates a new net.Listener bound to

the server’s address and then spins off a goroutine to close the listener

when you cancel the context. Finally, the method passes the listener, the

certificate path, and the key path onto the server’s ServeTLS method.

Listing 11-7 rounds out the echo server’s implementation with its

ServeTLS method.

*\--snip--*

func (s Server) ServeTLS(l net.Listener, certFn, keyFn string) error {

if s.tlsConfig == nil {

s.tlsConfig = &tls.Config{

**250** Chapter 11

 CurvePreferences: \[\]tls.CurveID{tls.CurveP256}, MinVersion: tls.VersionTLS12,

1 PreferServerCipherSuites: true,

}

}

if len(s.tlsConfig.Certificates) == 0 &&

s.tlsConfig.GetCertificate == nil {

cert, err := 2tls.LoadX509KeyPair(certFn, keyFn)

if err != nil {

return fmt.Errorf("loading key pair: %v", err)

}

s.tlsConfig.Certificates = \[\]tls.Certificate{cert}

}

tlsListener := 3tls.NewListener(l, s.tlsConfig)

if s.ready != nil {

close(s.ready)

}

*Listing 11-7: Adding TLS support to a net.Listener (* tls\_echo .go *)*

The ServeTLS method first checks the server’s TLS configuration. If it’s

nil, it adds a default configuration with PreferServerCipherSuites set to true 1.

PreferServerCipherSuites is meaningful to the server only, and it makes the

server use its preferred cipher suite instead of deferring to the client’s

preference.

If the server’s TLS configuration does not have at least one certificate,

or if its GetCertificate method is nil, you create a new tls.Certificate by

reading in the certificate and private-key files from the filesystem 2.

At this point in the code, the server has a TLS configuration with at

least one certificate ready to present to clients. All that’s left is to add TLS
