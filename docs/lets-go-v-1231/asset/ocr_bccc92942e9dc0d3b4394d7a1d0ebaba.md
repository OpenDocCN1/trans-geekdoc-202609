into Go HTTP server. They will cause your application to exit and bring down the server.

So, if you are spinning up additional goroutines from within your web application and there is any chance of a panic, you must make sure that you recover any panics from within those too. For example:

```
func (app *application) myHandler(w http.ResponseWriter, r *http.Request) {
...

	// Spin up a new goroutine to do some background processing.
	go func() {
		defer func() {
			if err := recover(); err != nil {
				app.logger.Error(fmt.Sprint(err))
			}
		}()

		doSomeBackgroundProcessing()
	}()
}

w.Write([]byte("OK"))
}
```