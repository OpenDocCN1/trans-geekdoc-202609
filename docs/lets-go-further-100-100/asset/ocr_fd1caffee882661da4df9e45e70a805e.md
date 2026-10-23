![](bbox=[0.125, 0.09, 0.875, 0.475])

Let’s try this out under load and use hey to make some requests to the POST /v1/tokens/authentication endpoint again.

First restart the API:

```
$ go run ./cmd/api -limiter-enabled=false
{"level":"INFO","time":"2021-04-18T09:18:36Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-18T09:18:36Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
```

And tThen use hey to generate the load like so: