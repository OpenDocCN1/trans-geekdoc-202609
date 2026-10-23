```
$ curl localhost:4000/v1/movies/1 & curl localhost:4000/v1/movies/1 &
[1] 33221
[2] 33222
$ {
  "error": "the server encountered a problem and could not process your request"
}
{
  "error": "the server encountered a problem and could not process your request"
}
```

When you now head back to your original terminal, you should see two different error messages:

```
$ go run ./cmd/api -db-max-open-conns=1
2021/04/08 14:21:36 database connection pool established
2021/04/08 14:21:36 starting development server on :4000
2021/04/08 14:21:50 context deadline exceeded
2021/04/08 14:21:50 pq: canceling statement due to user request
```

Here the `pq: canceling statement due to user request` error message relates to the running SQL query being terminated, whereas the `context deadline exceeded` message relates to the queued SQL query being canceled before a free database connection even became available.

In a similar vein, it’s also possible that the timeout deadline will be hit later on when the data returned from the query is being processed