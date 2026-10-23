![](bbox=[0.125, 0.095, 0.875, 0.485])

Lastly, head back to your SSH terminal window and press Ctrl+C to stop the API from running on your droplet. You should see it gracefully shutdown like so:

```
greenlight@greenlight-production:~$ /home/greenlight/api -port=4000 -db-dsn=$GREENLIGHT_DB_DSN -env=production
{"level":"INFO","time":"2021-04-19T07:10:55Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-19T07:10:55Z","message":"starting server","properties":{"addr":":4000","env":"production"}}
^C{"level":"INFO","time":"2021-04-19T07:13:23Z","message":"caught signal","properties":{"signal":"interrupt"}}
{"level":"INFO","time":"2021-04-19T07:13:23Z","message":"completing background tasks","properties":{"addr":":4000"}}
{"level":"INFO","time":"2021-04-19T07:13:23Z","message":"stopped server","properties":{"addr":":4000"}}
```