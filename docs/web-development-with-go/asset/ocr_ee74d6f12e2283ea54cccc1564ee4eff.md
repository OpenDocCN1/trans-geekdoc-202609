# CHAPTER 17. FILLING IN THE GAPS

Note: This last bit of code is an example of how you might redirect a user with an alert after they sign up for a new account.

# Rendering persisted alerts

Without informing our views of persisted alerts they wouldn't serve any purpose. We need to update the Render method of the View type to inform it of the alerts and have it check for any persisted alerts. It will also be responsible for clearing any alerts after rendering so a user doesn’t see the same alert several times in a row.

```
$ atom views/view.go
```

Find the Render method and update it with the following code.

```
func (v *View) Render(w http.ResponseWriter, r *http.Request, data interface{}) {
	w.Header().Set("Content-Type", "text/html")
	var vd
	switch d := data.(type) {
	// ... this is unchanged
	// Lookup the alert and assign it if one is persisted
	if alert := getAlert(r); alert != nil {
	vd.Alert = alert
	clearAlert(w)
	}
	vd.User = context.User(r.Context())
	// ... everything below this point is unchanged
}
```

Note: All we are adding here is the "if alert := getAlert(r)..." block which is 4 lines long. Everything else in the Render method remains unchanged.

We now have all the tools necessary to redirect users with an alert message.