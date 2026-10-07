# Code Listing 29: router.go

```
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

```
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
```