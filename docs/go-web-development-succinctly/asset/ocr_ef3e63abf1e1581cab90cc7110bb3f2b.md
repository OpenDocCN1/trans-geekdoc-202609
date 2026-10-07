func CityAdd(w http.ResponseWriter, r *http.Request) {
    var city City

```
// Read the body of the request.
body, err := ioutil.ReadAllAll(io.LimitReader(r.Body, 1048576))
if err != nil {
    panic(err)
}
if err := r.Body.Close(); err != nil {
    panic(err)
}

// Convert the JSON in the request to a Go type.
if err := json.Unmarshal(body, &city); err != nil {
    w.Header().Set("Content-Type", "application/json")
    w.WriteHeader(422) // can't process!
    if err := json.NewEncoder(w).Encode(err); err != nil {
        panic(err)
    }
}

// Write to the database.
addResult := dbCityAdd(city)

// Format the response.
w.Header().Set("Content-Type", "application/json")
w.WriteHeader(http.StatusCreated)
w.Write(addResult)
```

Notice how we're setting a 1MB limit on the amount of data we'll accept from the client. The last thing we want is some malicious user serving us a terabyte of data and crashing our server!

> > Tip: Always limit the amount of data you will allow a client to send to your application.

When we have the JSON in a Go struct, we can prepare a statement in SQL, then execute it with the new city record we want to. The benefit of preparing a statement in this way, using db.Prepare, is that it protects against SQL injection if the same malicious user tries to sabotage us using another favorite hacker's technique.