```
}
```

Let's try it out with a HTTP get and a HTTP post using curl:

```
# Terminal 1
$ go run main.go
2021/06/08 11:11:30 Listening on port: 8080

# Terminal 2
$ curl -i http://127.0.0.1:8080/info

2021/06/08 11:11:37 ====================================================
2021/06/08 11:11:37 Query-string:
2021/06/08 11:11:37 Path: /info
2021/06/08 11:11:37 Method: GET
2021/06/08 11:11:37 Path: localhost:8080
2021/06/08 11:11:37 Header User-Agent=[curl/7.68.0]
2021/06/08 11:11:37 Header Accept=[*/*]
2021/06/08 11:11:37 Body:
2021/06/08 11:11:37 ====================================================
```

Note the User-Agent sent by curl, and the lack of a HTTP body. We also get the path, which was used by the internal route handling to run the function we defined.

```
# Terminal 2
$ curl -i -H "Content-type: application/json" \
-d '{"mode": "green"}' http://localhost:8080/info?insert=true

2021/06/08 11:13:28 ====================================================
2021/06/08 11:13:28 Query-string: insert=true
2021/06/08 11:13:28 Path: /info
2021/06/08 11:13:28 Method: POST
2021/06/08 11:13:28 Path: localhost:8080
2021/06/08 11:13:28 Header Content-Length=[17]
2021/06/08 11:13:28 Header User-Agent=[curl/7.68.0]
2021/06/08 11:13:28 Header Accept=[*/*]
2021/06/08 11:13:28 Header Content-Type=[application/json]
2021/06/08 11:13:28 Body: {"mode": "green"}
2021/06/08 11:13:28 ====================================================
```

Here we have passed JSON, so can see a content-type and body defined along with the POST method.

# Advanced route handling

You can add logic to a HTTP handler to only respond to certain HTTP methods, or to take different actions according to the path, however there are also a number of libraries available that can reduce code duplication.

Gorilla's mux is one of the most popular and is used in OpenFaaS and the inlets project.

In this example, the function path can take a name as an argument which will be parsed and made available without any user action. The Regular Expression allows alpha-numerics plus dashes and requires at least one character.

```
r.HandleFunc("/function/{name:[-a-zA-Z_0-9-]+}", functionProxy)
```

Within the handler, the mux.Vars() helper function is used to query the name: