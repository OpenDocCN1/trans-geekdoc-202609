# Global Rate Limiting

Let’s build things up slowly and start by creating a single *global rate limiter* for our application. This will consider *all the requests* that our API receives (rather than having separate rate limiters for every individual client).

Instead of writing our own rate-limiting logic from scratch, which would be quite complex and time-consuming, we can leverage the `x/time/rate` package to help us here. This provides a tried-and-tested implementation of a *token bucket* rate limiter.

If you’re following along, please go ahead and download the latest version of this package like so:

```
$ go get golang.org/x/time/rate@latest
go: downloading golang.org/x/time v0.0.0-20210220033141-f8bda1e9f3ba
go: added golang.org/x/time v0.0.0-20210220033141-f8bda1e9f3ba
```

Before we start writing any code, let’s take a moment to explain how token-bucket rate limiters work. The description from the official `x/time/rate` documentation says:

> A Limiter controls how frequently events are allowed to happen. It implements a “token bucket” of size b, initially full