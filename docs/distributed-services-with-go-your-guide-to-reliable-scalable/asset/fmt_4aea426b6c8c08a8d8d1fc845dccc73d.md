
进入`/path/to/xxx`目录，找到`xxx.json`。

在表达式`cvar = avar + bvar`中，加法运算符（`+`）将`avar`与`bvar`相加，得到它们的和`cvar`

在`List.of(arg0, arg1, arg2)`中，`List`接口的工厂方法`of()`接受一系列的元素，返回包含它们的只读列表。

之后我们这样调用`cmd`命令：`cmd arg0 arg1 arg2`。

```
if (condVar > someVal) {console.log("xxx")}
```

| ​  || ​**import**​ ( |

| ​  || *"encoding/json"*​ |

| ​  || *"net/http"*​ |

| ​  || *"github.com/gorilla/mux"*​ |

| ​  || ) |

| ​  ||  |

| ​  || ​**func**​ NewHTTPServer(addr ​**string**​) \*http.Server { |

| ​  || httpsrv := newHTTPServer() |

| ​  || r := mux.NewRouter() |

| ​  || r.HandleFunc(​*"/"*​, httpsrv.handleProduce).Methods(​*"POST"*​) |

| ​  || r.HandleFunc(​*"/"*​, httpsrv.handleConsume).Methods(​*"GET"*​) |

| ​  || ​**return**​ &http.Server{ |

| ​  || Addr: addr, |

| ​  || Handler: r, |

| ​  || } |

| ​  || } |

| ​  ||  |

| ​  || ​**type**​ httpServer ​**struct**​ { |

| --- | --- |

| ​  || Log \*Log |

| ​  || } |

| ​  ||  |

| ​  || ​**func**​ newHTTPServer() \*httpServer { |

| ​  || ​**return**​ &httpServer{ |

| ​  || Log: NewLog(), |

| ​  || } |

| ​  || } |

| ​  ||  |

| ​  || ​**type**​ ProduceRequest ​**struct**​ { |

| ​  || Record Record ​*\`json:"record"\`*​ |

| ​  || } |

| ​  ||  |

| ​  || ​**type**​ ProduceResponse ​**struct**​ { |

| ​  || Offset ​**uint64**​ ​*\`json:"offset"\`*​ |

| ​  || } |

| ​  ||  |

| ​  || ​**type**​ ConsumeRequest ​**struct**​ { |

| ​  || Offset ​**uint64**​ ​*\`json:"offset"\`*​ |

| ​  || } |

| ​  ||  |

| ​  || ​**type**​ ConsumeResponse ​**struct**​ { |

| ​  || Record Record ​*\`json:"record"\`*​ |

| ​  || } |

We now have a server referencing a log for the server to defer to in its handlers. A produce request contains the record that the caller of our API wants appended to the log, and a produce response tells the caller what offset the log stored the records under. A consume request specifies which records the caller of our API wants to read and the consume response to send back those records to the caller. Not bad for just 28 lines of code, huh?

Next, we need to implement the server’s handlers. Add the following snippet below your types from the previous code snippet:

[LetsGo/internal/server/http.go](http://media.pragprog.com/titles/tjgo/code/LetsGo/internal/server/http.go) 

| ​  || ​**func**​ (s \*httpServer) handleProduce(w http.ResponseWriter, r \*http.Request) { |

| --- | --- |

| ​  || ​**var**​ req ProduceRequest |

| ​  || err := json.NewDecoder(r.Body).Decode(&req) |

| ​  || ​**if**​ err != nil { |

| ​  || http.Error(w, err.Error(), http.StatusBadRequest) |

| ​  || ​**return**​ |

| ​  || } |

| ​  || off, err := s.Log.Append(req.Record) |

| ​  || ​**if**​ err != nil { |

| ​  || http.Error(w, err.Error(), http.StatusInternalServerError) |

| ​  || ​**return**​ |

| ​  || } |

| ​  || res := ProduceResponse{Offset: off} |

| ​  || err = json.NewEncoder(w).Encode(res) |

| ​  || ​**if**​ err != nil { |

| ​  || http.Error(w, err.Error(), http.StatusInternalServerError) |

| ​  || ​**return**​ |

| ​  || } |

| ​  || } |

The produce handler implements the three steps we discussed before: unmarshaling the request into a struct, using that struct to produce to the log and getting the offset that the log stored the record under, and marshaling and writing the result to the response. Our consume handler looks almost identical. Add the following snippet below your produce handler:

[LetsGo/internal/server/http.go](http://media.pragprog.com/titles/tjgo/code/LetsGo/internal/server/http.go) 

| ​  || ​**func**​ (s \*httpServer) handleConsume(w http.ResponseWriter, r \*http.Request) { |

| --- | --- |

| ​  || ​**var**​ req ConsumeRequest |

| ​  || err := json.NewDecoder(r.Body).Decode(&req) |

| ​  || ​**if**​ err != nil { |

| ​  || http.Error(w, err.Error(), http.StatusBadRequest) |

| ​  || ​**return**​ |

| ​  || } |

| ​  || record, err := s.Log.Read(req.Offset) |

| ​  || ​**if**​ err == ErrOffsetNotFound { |

| ​  || http.Error(w, err.Error(), http.StatusNotFound) |

| ​  || ​**return**​ |

| ​  || } |

| ​  || ​**if**​ err != nil { |

| ​  || http.Error(w, err.Error(), http.StatusInternalServerError) |

| ​  || ​**return**​ |

| ​  || } |

| ​  || res := ConsumeResponse{Record: record} |

| ​  || err = json.NewEncoder(w).Encode(res) |

| ​  || ​**if**​ err != nil { |

| ​  || http.Error(w, err.Error(), http.StatusInternalServerError) |

| ​  || ​**return**​ |

| ​  || } |

| ​  || } |

The consume handler is like the produce handler but calls Read(offset uint64) to get the record stored in the log. This handler contains more error checking so we can provide an accurate status code to the client if the server can’t handle the request, like if the client requested a record that doesn’t exist.

That’s all the code needed for our server. Now let’s write some code to turn your server library into a program we can execute.

## Run Your Server

The last code you need to write is a main package with a main function to start your server. In the root directory of your project, create a cmd/server directory tree, and in the server directory create a file named main.go with this code:

[LetsGo/cmd/server/main.go](http://media.pragprog.com/titles/tjgo/code/LetsGo/cmd/server/main.go) 

| ​  || ​**package**​ main |

| --- | --- |

| ​  ||  |

| ​  || ​**import**​ ( |

| ​  || ​*"log"*​ |

| ​  ||  |

| ​  || ​*"github.com/travisjeffery/proglog/internal/server"*​ |

| ​  || ) |

| ​  ||  |

| ​  || ​**func**​ main() { |

| ​  || srv := server.NewHTTPServer(​*":8080"*​) |

| ​  || log.Fatal(srv.ListenAndServe()) |

| ​  || } |

Our main function just needs to create and start the server, passing in the address to listen on (localhost:8080) and telling the server to listen for and handle requests by calling ListenAndServe. Wrapping our server with the \*net/http.Server in NewHTTPServer saved us from writing a bunch of code here—and anywhere else we’d create an HTTP server.

It’s time to test our slick new service.

## Test Your API

You now have a functioning JSON/HTTP commit log service you can run and test by hitting the endpoints with curl. Run the following snippet to start the server:

| ​  || $ go run main.go |

| --- | --- |

Open another tab in your terminal and run the following commands to add some records to your log:

| ​  || $ curl -X POST localhost:8080 -d \\ |

| --- | --- |

| ​  || '{"record": {"value": "TGV0J3MgR28gIzEK"}}' |

| ​  || $ curl -X POST localhost:8080 -d \\ |

| --- | --- |

| ​  || '{"record": {"value": "TGV0J3MgR28gIzIK"}}' |

| ​  || $ curl -X POST localhost:8080 -d \\ |

| --- | --- |

| ​  || '{"record": {"value": "TGV0J3MgR28gIzMK"}}' |

Go’s encoding/json package encodes \[\]byte as a base64-encoding string. The record’s value is a \[\]byte, so that’s why our requests have the base64 encoded forms of Let’s Go #1–3. You can read the records back by running the following commands and verifying that you get the associated records back from the server:

| ​  || $ curl -X GET localhost:8080 -d '{"offset": 0}' |

| --- | --- |

| ​  || $ curl -X GET localhost:8080 -d '{"offset": 1}' |

| ​  || $ curl -X GET localhost:8080 -d '{"offset": 2}' |

Congratulations—you have built a simple JSON/HTTP service and confirmed it works!

## What You Learned
