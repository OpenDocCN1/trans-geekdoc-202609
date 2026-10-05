```
if err != nil {
    return err
}
// Create a destination file
dat, err := os.Create(filepath.Join(path, filename))
if err != nil {
    return err
}
deffer dst.Close()
// Copy reader data to the destination file
err = io.Copy(dst, r)
if err != nil {
    return err
}
return nil
```

Now that we have a working Create method, we are going to want to want the image service accessible inside the Galleries controller so we can use it to create images instead of the existing code.

```
$ atom controllers/galleries.go
```

We'll start with the NewGalleries function and the Galleries type. We need to add an image service field to each of these.

```
func NewGalleries(gs models.GalleryService,
    models.ImageService, r *mux.Router) *Galleries {
    return &Galleries{
        New:      views.NewView("bootstrap", "galleries/new"),
        ShowView: views.NewView("bootstrap", "galleries/show"),
        EditView: views.NewView("bootstrap", "galleries/edit"),
        AdapterView: views.NewView("bootstrap", "galleries/index"),
        gs:       gs,
        is:       is,
        r:        r,
    }
}
ntype Galleries struct {
    New      *views.View
    ShowView *views.View
```