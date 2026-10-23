If you issue a batch of six requests in quick succession again, you should now find that only the first two succeed:

```
$ for i in {1..6}; do curl  http://localhost:4000/v1/healthcheck; done
{
  "status": "available",
  "system_info": {
    "environment": "development",
    "version": "1.0.0"
  }
}
{
  "status": "available",
  "system_info": {
    "environment": "development",
    "version": "1.0.0"
  }
}
{
  "error": "rate limit exceeded"
}
{
  "error": "rate limit exceeded"
}
{
  "error": "rate limit exceeded"
}
{
  "error": "rate limit exceeded"
}
```

Similarly, you can try disabling the rate limiter altogether with the `limiter-enabled=false` flag like so: