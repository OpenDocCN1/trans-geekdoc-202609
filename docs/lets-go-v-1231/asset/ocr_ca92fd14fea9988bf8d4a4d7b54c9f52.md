```
logger.Error(err.Error())
os.Exit(1)
}
...
```

**Note:** The scs.New() function returns a pointer to a SessionManager struct which holds the configuration settings for your sessions. In the code above we've set the Store and Lifetime fields of this struct, but there's a range of other fields that you can and should configure depending on your application's needs.

For the sessions to work, we also need to wrap our application routes with the middleware provided by the SessionManager.LoadAndSave() method. This middleware automatically loads and saves session data with every HTTP request and response.

It's important to note that we don't need this middleware to act on *all* our application routes. Specifically, we don't need it on the GET /static/ route, because all this does is serve static files and there is no need for any stateful behavior.

So, because of that, it doesn't make sense to add the session middleware to our existing standard middleware chain.

Instead, let's create a new dynamic middleware chain containing the middleware appropriate for our dynamic application routes only.

Open the routes.go file and update it like so: