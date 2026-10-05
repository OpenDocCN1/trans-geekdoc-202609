# 16.7. SETTING UP A SERVER

```
www.lenslocked.com {
  gzip
  proxy / localhost:3000 {
    transparent
  }
}
```

In this Caddyfile we define our domain and then define how Caddy would hardly any incoming web requests to that domain. In our case we are asking to gzip (compress) data before sending it back to end users to lower bandwidth required, and we are proxying all requests to localhost:3000.

Proxying web request basically means our Caddy server will take any incoming web requests and forward them to our web application that will be running on the same server (localhost) on port 3000. By doing this, we could potentially have four or five servers all running on different ports, and have Caddy decide which server user is trying to access by looking at the domain and proxying the request to the proper localhost:port combination.

The transparent portion of the proxy is used to add a few headers to the request before sending it to localhost:3000, such as adding the user's IP address to the X-Real-IP header and a few others. We won't be using the header, but in our experience they can be useful long term.

Our Caddyfile without a domain is basically the same, but we can't isolate it to a single domain.

```
:80 {
  gzip
  proxy / localhost:3000 {
    transparent
  }
}
```

We won't push this to our server just yet, but will handle it in the next section when we create our deploy script.