improve over time.

# 13.5 Generating Core Dumps

I can generate a core dump from a running Go program, which is useful if I feel the program is hung or not responding.

Listing 13.12

```
01 package main
02
03 import (
04     "encoding/json"
05     "log"
06     "net/http"
07 )
08
09 func main() {
10     http.HandleFunc("/sendjson", sendJSON)
11
12     log.Println("listener : Started : Listening on: " +
13     "http://localhost:8080")
14     http.ListenAndServe(":8080", nil)
15 }
16
17 // sendJSON returns a simple JSON document.
18 func sendJSON(rw http.ResponseWriter, r *http.Request) {
19     u := struct {
20         Name string
21         Email string
22     }{
23         Name: "bill",
24         Email: "bill@ardanlabs.com",
25     }
26     rw.Header().Set("Content-Type", "application/json")
27     rw.WriteHeader(200)
28     json.NewEncoder(rw).Encode(u)
29 }
```

Now I can build and run the program.

Listing 13.13

```
$ go build
$ ./example3
2021/05/17 14:09:05 listener : Started : Listening on: http://localhost:4000
```

Next, I can send a signal to quit the process.

Listing 13.14

```
$ ps
6575 tty002      0:00.01 ./example3
$ kill -3 6575
```

This will result in the Go program producing a core dump.