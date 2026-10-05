# CHAPTER 7. CREATING A SIGN UP PAGE

dle. To test this, let's update all of our existing routes to only accept the GET method and verify that things are still working.

Open up main.go if you haven't already.

```
$ atom main.go
```

Then update the router code in the main function to match the code in Listing 7.18.

# Listing 7.18: Routing with methods

```
r := mux.NewRouter()
r.HandleFunc("/", home).Methods("GET")
r.HandleFunc("/contact", contact).Methods("GET")
r.HandleFunc("/signup", usersC.New).Methods("GET")
http.ListenAndServeAndServe(":3000", r)
```

Stop (ctrl + c) and restart your server to verify that things are working.

```
$ go run main.go
```

 appears to be working as we intended. Nice!

Next we want to add a new route that uses the /signup path again, but this time it will only accept the POST method and should route the request to the Create method we created on the users controller. By doing this we will be able to submit our sign up form to the /signup path and then we create action will be called to process the form.

# Box 7.8. Another exception to RESTful design