```
"log"
"net/http"
"os"
"time"
)

func makeAuth(token string, next http.HandlerFunc) http.HandlerFunc {
    return func(w http.ResponseWriter, r *http.Request) {
        if b := r.Header.Get("Authorization"); len(b) == 0 || b != "Bearer: "+token {
            http.Error(w, "Not authorized", http.StatusUnauthorized)
        } else {
            next(w, r)
        }
    }
}

func main() {
    token := os.Getenv("TOKEN")
    next := func(w http.ResponseWriter, r *http.Request) {
        w.Write([]byte("Authorized"))
    }

    http.HandleFunc("/customer/", makeAuth(token, next))

    tcpPort := 8080
    s := &http.Server{
        Addr:           fmt.Sprintf(":%d", tcpPort),
        ReadTimeout:    time.Second * 10,
        WriteTimeout:   time.Second * 10,
        MaxHeaderBytes: http.DefaultMaxHeaderBytes,
    }
    log.Printf("Listening on: %d", tcpPort)
    log.Fatal(s.ListenAndServe())
}
```

Note that the makeAuth function adds an if guard around the HTTP authorization header, and if not found or not having the matching token, then the “next” HTTP call won’t be made. In this way, you can chain as many HTTP middleware as you like, for authorization then logging, and whatever else you need.

Try it out:

```
# Terminal 1
go run main.go

# Terminal 2

curl http://127.0.0.1:8080/customer/alex -H "Authorization: Bearer: test"
Authorized

curl http://127.0.0.1:8080/customer/alex
Not authorized
```