80 because Caddy is already using this, so we’ll listen on the unrestricted port 4000 instead.

If you’ve been following along, port 4000 on your droplet should currently be blocked by the firewall rules, so we’ll need to relax this temporarily to allow incoming requests. Go ahead and do that like so:

```
greenlight@greenlight-production:~$ sudo ufw allow 4000/tcp
Rule added
Rule added (v6)
```

And then start the API with the following command:

```
greenlight@greenlight-production:~$ ./api -port=4000 -db-dsn=$GREENLIGHT_DB_DSN -env=production
{"level":"INFO","time":"2021-04-19T07:10:55Z","message":"database connection pool established"}
{"level":"INFO","time":"2021-04-19T07:10:55Z","message":"starting server","properties":{"addr":":4000","env":"production"}}
```

At this point you should be able to visit http://<your_droplet_ip>:4000/v1/healthcheck in your web browser and get a successful response from the healthcheck endpoint, similar to this: