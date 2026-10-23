```
File: remote/production/Caddyfile

http://45.55.49.87 {
    reverse_proxy localhost:4000
}
```

As you can probably guess by looking at it, this rule tells Caddy that we want it to listen for HTTP requests to 45.55.49.87 and then act a reverse proxy, forwarding the request to port 4000 on the local machine (where our API is listening).

> **Hint:** Caddyfiles have *a lot* of available settings and we’ll demonstrate some of the more common ones as we progress through this chapter. But if you plan on using Caddy in your own production projects, then I recommend reading through the official Caddyfile documentation, which is excellent.

The next thing we need to do is upload this Caddyfile to our droplet and reload Caddy for the changes to take effect.

To manage this, let’s update our makefile to include a new `production/configure/caddyfile` rule. This will follow the same basic pattern that we used in the previous chapter for uploading our `api.service` file, but instead we’ll copy our Caddyfile to `/etc/caddy/Caddyfile` on the server.

Like so: