# 14.8. EDITING GALLERIES

tions already created; the first will verify that the UserID field is set correctly, and the second will verify that a title is provided for the gallery.

```
func (gv *galleryValidatos) Update(gallery *Gallery) error {
terr = runGalleryValns(gallery,
gv.userIDRequired,
gv.titleRequired)
if err != nil {
	return err
}
return gv.GalleryDB.Update(gallery)
}
```

With our Update method added to the GalleryService (via the embedded GalleryDB) we can go back to the galleries controller and use this new method in our Update action.

```
$ atom controllers/galleries.go
```

We will only be altering the last portion of the Update method where we placed a TODO before, the first half of the method is left blank for brevity.

```
func (g *Galleries) Update(w http.ResponseWriter, r *http.Request) {
// ... this first half remains unchanged

gallery.Title = form.Title
er = g.gs.Update(gallery)
// If there is an error alert it will be an error. Otherwise
// we will still render an alert, but instead it will be
// a success message.
if err != nil {
	dv.SetAlert(err)
} else {
dv.Alert = views.Alert{
	Level: views.AlertLvSuccess,
	Message: "Gallery successfully updated!",
}

// Error or not, we are going to render the EditView with
// our updated information.
g.EditView.Render(w, vd)
}
```