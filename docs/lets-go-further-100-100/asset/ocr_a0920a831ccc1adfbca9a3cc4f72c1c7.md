```
app.serverErrorResponse(w, r, err)
}
}
```

Then start the API, and in another terminal window issue a request to the healthcheck endpoint followed by a SIGTERM signal.

```
$ curl localhost:4000/v1/healthcheck & pkill -SIGTERM api
```

In the logs for the server, you should immediately see a "shutting down server" message following the SIGTERM signal, similar to this:

```
$ go run ./cmd/api
{"level":"INFO","time":"2021-04-11T10:54:55Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-11T10:54:55Z","message":"starting server","properties":{"addr":":4000","env":"development"}}
{"level":"INFO","time":"2021-04-11T10:55:03Z","message":"shutting down server","properties":{"signal":"terminated"}}
```

Then after a 4 second delay for the in-flight request to complete, our healthcheckHandler should return the JSON response as normal and you should see that our API has logged a final "stopped server" message before exiting cleanly: