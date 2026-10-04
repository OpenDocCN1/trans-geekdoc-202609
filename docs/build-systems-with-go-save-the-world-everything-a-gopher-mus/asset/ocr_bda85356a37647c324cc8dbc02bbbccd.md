```
counter, err := r.Cookie("counter")
if err != nil {
	w.WriteHeader(http.StatusStatusInternal)
	return
}

value, err := strconv.Atoi(counter.Value)
if err != nil {
	w.WriteHeader(http.StatusStatusInternal)
	return
}

value = value + 1
newCookie := http.Cookie{
	Name: "counter",
	Value: strconv.Itoa(value),
}
http.SetCookie(w, &newCookie)
w.WriteHeader(http.StatusOK)
	return
}

func main() {
	http.HandleFunc("/cookie", cookieSetter)
	go http.ListenAndServe(":8090", nil)

	url := "http://localhost:8090/cookie"
	req, err := http.NewRequest("GET", url, nil)
tif err != nil {
	panic(err)
}

	client := http.Client()
	c := http.Cookie{
	Name: "counter", Value: "1", Domain: "127.0.0.1",
	Path: "/", Expires: time.Now().AddDate(1, 0, 0),
}
	req.AddCookie(&c)

	resp, err := client.Do(req)
tif err != nil {
	panic(err)
}
	fmt.Println("<-", req.Header)
	fmt.Println("->", resp.Header)
}

// map[Cookie[counter=1]]
// - map[Content-Length:[0]] Date:[Tue, 19 Jan 2021 20:12:59 GMT]
Set-Cookie:[Cookie[counter=2]]
```