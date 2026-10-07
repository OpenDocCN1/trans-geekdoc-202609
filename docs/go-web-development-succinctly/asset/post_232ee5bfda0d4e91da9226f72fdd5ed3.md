
# Code Listing 26: The CityDelete Function

```go
func CityDelete(w http.ResponseWriter, r *http.Request) {

    // Get URL parameter with the city ID to delete.
    vars := mux.Vars(r)
    cityID, _ := strconv.ParseInt(vars["id"], 10, 64)

    // Query the database.
    deleteResult := dbCityDelete(cityID)

    // Send the response.
    w.Header().Set("Content-Type", "application/json")
    w.WriteHeader(http.StatusOK)
    w.Write(deleteResult)
}
```

The corresponding dbCityDelete function takes that ID and prepares a DELETE statement with it. Database returns the number of rows affected, and we can use the same DBUpdate struct to present information to the user.

# Code Listing 27: The dbCityDelete function

```go
// Delete the city with the ID.
func dbCityDelete(id int64) []byte {
    var deleteResult DBUpdate

    // Create prepared statement.
    stmt, err := database.Prepare("DELETE FROM CITY WHERE ID=?")
    if err != nil {
        log.Fatal(err)
    }

    // Execute the prepared statement and retrieve the results.
    res, err := stmt.Exec(id)
    if err != nil {
        log.Fatal(err)
    }
    rowCnt, err := res.RowsAffected()
    if err != nil {
        log.Fatal(err)
    }

    // Populate DBUpdate struct with Last ID and num rows affected.
    deleteResult.Id = id
    deleteResult.Affected = rowCnt

    // Convert to JSON and return.
    deletedCity, err := json.Marshal(deleteResult)
    if err != nil {
        fmt.Printf("Error: %s", err)
    }
    return deletedCity
}
```

And that's really it!

# The complete application

Let's next examine a number of code listing examples that demonstrate the complete application as we separate the various concerns into these modules:

- main.go
- router.go
- routes.go
- handlers.go
- database.go
- city.go
- dbupdate.go

# Code Listing 28: main.go

```go
package main

import (
    "log"
    "net/http"
)

func main() {
    router := NewRouter()
    dbConnect()

    log.Fatal(http.ListenAndServe(":8999", router))
}
```

# Code Listing 29: router.go

```go
package main

import "github.com/gorilla/mux"

func NewRouter() *mux.Router {
    router := mux.NewRouter().StrictSlash(true)
    for _, route := range routes {
        router.
            Methods(route.Method).
            Path(route.Pattern).
            Name(route.Name).
            Handler(route.HandlerFunc)
    }
    return router
}
```

# Code Listing 30: routes.go

```go
package main

import "net/http"

type Route struct {
    Name string
    Method string
    Pattern string
    HandlerFunc http.HandlerFunc
}

type Routes []Route

var routes = Routes{
    Route{
        "HomePage",
        "GET",
        "/",
        HomePage,
    },
    Route{
        "CityList",
        "GET",
        "/city",
        CityList,
    },
    Route{
        "CityDisplay",
        "GET",
        "/city/{id}",
        CityDisplay,
    },
    Route{
        "CityAdd",
        "POST",
        "/cityadd",
        CityAdd,
    },
    Route{
        "CityDelete",
        "GET",
        "/citydel/{id}",
        CityDelete,
    }
}
```

# Code Listing 31: handlers.go

```go
package main

import (
    "encoding/json"
    "fmt"
    "io"
    "io/ioutil"
    "net/http"
    "strconv"

    "github.com/gorilla/mux"
)

func HomePage(w http.ResponseWriter, r *http.Request) {
    fmt.Fprintf(w, "Welcome to the City Database!")
}

func CityList(w http.ResponseWriter, r *http.Request) {
    // Query the database.
    jsonCities := dbCityList()
    
    // Format the response.
    w.Header().Set("Content-Type", "application/json")
    w.WriteHeader(http.StatusOK)
    w.Write(jsonCities)
}

func CityDisplay(w http.ResponseWriter, r *http.Request) {
    // Get URL parameter with the city ID to search for.
    vars := mux.Vars(r)
    cityID, _ := strconv.Atoi(vars["id"])

    // Query the database.
    jsonCity := dbCityDisplay(cityID)

    // Format the response.
    w.Header().Set("Content-Type", "application/json")
    w.WriteHeader(http.StatusOK)
    w.Write(jsonCity)
}

func CityAdd(w http.ResponseWriter, r *http.Request) {
    var city City

    // Read the body of the request.
    body, err := ioutil.ReadAll(io.LimitReader(r.Body, 1048576))
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
}

func CityDelete(w http.ResponseWriter, r *http.Request) {
    // Get URL parameter with the city ID to delete.
    vars := mux.Vars(r)
    cityID, _ := strconv.ParseInt(vars["id"], 10, 64)

    // Query the database.
    deleteResult := dbCityDelete(cityID)

    // Format the response.
    w.Header().Set("Content-Type", "application/json")
    w.WriteHeader(http.StatusOK)
    w.Write(deleteResult)
}
```
