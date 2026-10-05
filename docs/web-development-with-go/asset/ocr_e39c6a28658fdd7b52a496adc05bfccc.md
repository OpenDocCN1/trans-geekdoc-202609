# 14.8. EDITING GALERIES

```
vd.Alert = &views.Alert{
  Level: views.AlertLvlSuccess,
  Message: "Gallery updated successfully!",n}
g.EditView.Render(w, vd)

```

We don't have a way to actually update our gallery using the GalleryService yet, so we will code that in the next section then come to finish our update handler. In the meantime, we are rendering the edit page again with the submitted data and an alert message pretending that the gallery was successfully updated.

Let's tell our router about the new route so we can verify this is all working.

```
$ atom main.go
```

Add the following route into the main function near the existing gallery routes.

```
r.HandleFunc("/galleries/{id:[0-9]+}/update",
requireUserMw.ApplyFn(galleriesC.Update)).Methods("POST")
```

Restart your server and by submitting the edit gallery form. You will now have the updated information in the form and an alert message saying the gallery was updated, but if you reload the page you will see an alert that the update didn't actually happen. In the next section we will cover how to implement that portion of the code.

# Source code

The links below have the completed source code and a diff of all the code changed in this section.