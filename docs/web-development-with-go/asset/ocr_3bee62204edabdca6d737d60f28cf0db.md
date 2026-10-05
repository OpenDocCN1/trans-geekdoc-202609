# CHAPTER 7. CREATING A SIGN UP PAGE

```
r := mux.NewRouter()
r.Handle("/", staticC.HomeView).Methods("GET")
r.Handle("/contact", staticC.ContactView).Methods("GET")
r.HandleFunc("/signup", userC.New).Methods("GET")
r.HandleFunc("/signup", userC.Create).Methods("POST")
			http.ListenAndServe(":3000", r)
```

Lastly, since we don't plan on creating a Home or Contact method on the static controller, we can rename fields from HomeView and ContactView to just be Home and Contact. After doing this you will also need to update main.go.

# Listing 7.31: Renaming view fields in controllers/static.go

```
package controllers

import "lenslocked.com/views"

func NewStatic() *Static {
	return &Static{
		home: views.NewView(
			"bootstrap", "views/static/home.gohtml\),
			Contact: views.NewView(
				"bootstrap", "views/static/contact.gohtml\),
		}
}

type Static struct {
	home *views.View
	Contact *views.View
}
```

# Listing 7.32: Renaming handler fields in main.go

```
r.Handle("/", staticC.Home).Methods("GET")
r.Handle("/contact", staticC.Contact).Methods("GET")
```

Restart your application and verify that it is working. You should still be able to view the home and contact pages, but now they should be served via the