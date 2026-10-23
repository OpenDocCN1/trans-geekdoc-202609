if you’re following along.

The first thing you’ll need to do is configure the DNS records for your domain name so that they contain an A record pointing to the IP address for your droplet. So in my case the DNS record would look like this:

```
A    greenlight.alexedwards.net    45.55.49.87
```

> Note: If you’re not sure how to alter your DNS records, your domain name registrar should provide guidance and documentation.

Once you’ve got the DNS record in place, the next task is to update the Caddyfile to use your domain name instead of your droplet’s IP address. Go ahead and swap this out like so (remember to replace greenlight.alexedwards.net with your own domain name):

```
File: remote/production/Caddyfile

http://greenlight.alexedwards.net {
  respond /debug/* "Not Permitted" 403
  reverse_proxy localhost:4000
}
```