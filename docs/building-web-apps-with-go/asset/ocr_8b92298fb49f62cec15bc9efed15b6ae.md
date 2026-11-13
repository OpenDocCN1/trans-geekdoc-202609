# Unit Testing

Unit testing allows us to test a `http.HandlerFunc` directly without running any middleware, routers, or any other type of code that might otherwise wrap the function.

```
package main

import (
	"fmt"
	"net/http"
)

func HelloWorld(res http.ResponseWriter, req *http.Request) {
	fmt.Fprint(res, "Hello World")
}

func main() {
	http.HandleFunc("/", HelloWorld)
	http.ListenAndServe(":3000", nil)
}

```

This is the test file. It should be placed in the same directory as your application and name `main_test.go` .