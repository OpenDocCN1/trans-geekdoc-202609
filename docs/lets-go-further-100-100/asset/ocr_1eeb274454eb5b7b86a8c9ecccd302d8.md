`GET /v1/healthcheck` endpoint. You should now get back a response which looks like this:

```
$ curl -i localhost:4000/v1/healthcheck
HTTP/1.1 200 OK
Content-Type: application/json
Date: Tue, 06 Apr 2021 08:38:12 GMT
Content-Length: 73

{"status": "available", "environment": "development", "version": "1.0.0"}
```

You might also like to try visiting `localhost:4000/v1/healthcheck` in your browser.

If you’re running one of the newer versions of Firefox, you’ll find that it knows the response contains JSON (due to the `Content-Type` header) and it will present the response using the inbuilt JSON viewer. Like so: