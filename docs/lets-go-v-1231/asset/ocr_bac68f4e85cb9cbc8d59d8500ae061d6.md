# Configuring HTTPS settings

Go has good default settings for its HTTPS server, but it’s possible to optimize and customize how the server behaves.

One change, which is almost always a good idea to make, is to restrict the *elliptic curves* that can potentially be used during the TLS handshake. Go supports a few elliptic curves, but as of Go 1.23 only `tls.CurveP256` and `tls.X25519` have assembly implementations. The others are very CPU intensive, so omitting them helps ensure that our server will remain performant under heavy loads.

To make this tweak, we can create a `tls.Config` struct containing our non-default TLS settings, and add it to our `http.Server` struct before we start the server.

I’ll demonstrate: