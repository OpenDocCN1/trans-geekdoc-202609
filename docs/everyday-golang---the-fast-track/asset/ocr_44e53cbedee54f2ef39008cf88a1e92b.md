```
    "time"
)

type people struct {
    Number int `json:"number"`
}

func main() {

    url := "http://api.open-notify.org/astros.json"

    spaceClient := http.Client{
        Timeout: time.Second * 2, // Timeout after 2 seconds
    }

    req, err := http.NewRequest(http.MethodGet, url, nil)
    if err != nil {
        log.Fatal(err)
    }

    req.Header.Set("User-Agent", "spacecount-tutorial")

    res, err := spaceClient.Do(req)
    if err != nil {
        log.Fatal(err)
    }

    if res.Body != nil {
        defer res.Body.Close()
    }

    body, err := io.ReadAll(res.Body)
    if err != nil {
        log.Fatal(err)
    }

    p := people{}
    err = json.Unmarshal(body, &p)
    if err != nil {
        log.Fatal(err)
    }

    fmt.Println(p.Number)
}
```

If you're used to writing Node.js, then you will be used to most I/O operations returning a nullable error. The same is the case in Go and checking for errors here has made the code quite verbose. You may want to refactor elements of the code into separate methods - one to download and one unmarshal the JSON data.

It may not always make sense to attempt to parse the HTTP response, one case is if the HTTP code returned is a non-200 number. Here's how you can access the HTTP code from the response:

```
fmt.Printf("HTTP status: %s\n", res.Status)
```

If you are unsure whether the JSON schema is stable and expect it, at times, to return invalid JSON, then you could