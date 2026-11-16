```
File: cmd/web/handlers.go

package main

import (
	"fmt"
	"html/template" // New import
	"log" // New import
	"net/http"
	"strconv"
)

func home(w http.ResponseWriter, r *http.Request) {
	w.Header().Add("Server", "Go")

	// Use the template.ParseFiles() function to read the template file into a
	// template set. If there's an error, we log the detailed error message, use
	// the http.Error() function to send an Internal Server Error response to the
	// user, and then return from the handler so no subsequent code is executed.
	ts, err := template.ParseFiles("./ui/html/pages/home.tpl")
	if err != nil {
		log.Print(err.Error())
		http.Error(w, "Internal Server Error", http.StatusInternalServerError)
		return
	}

	// Then we use the Execute() method on the template set to write the
	// template content as the response body. The last parameter to Execute()
	// represents any dynamic data that we want to pass in, which for now we'll
	// leave as nil.
	err = ts.Execute(w, nil)
	if err != nil {
		log.Print(err.Error())
		http.Error(w, "Internal Server Error", http.StatusInternalServerError)
	}
}
...
```

There are a couple of important things about this code to point out:

+   - The file path that you pass to the template.ParseFiles() function must either be relative to your current working directory, or an absolute path. In the code above I've made the path relative to the root of the project directory.

+   - If either the template.ParseFiles() or ts.Execute() functions return an error, we log the detailed error message and then use the http.Error() function to send a response to the user. http.Error() is a lightweight helper function which sends a plain text error message and a specific HTTP status code to the user (in our code we send the message "Internal Server Error" and the status code 500, represented by the constant http.StatusInternalServerError). Effectively, this means that if there is an error, the user will see the message Internal Server Error in their browser, but the detailed error message will be recorded in the application log messages.