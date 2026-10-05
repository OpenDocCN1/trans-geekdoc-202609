# 16.5. FIXING BUGS

621

Note: If you are following the screencasts we may already be doing this in that source code.

Open up your galleries controller source file.

```
$ atom controllers/galleries.go
```

Find the ImageUpload method and update the code at the end to instead redirect a user to the edit page after successfully uploading images.

```
func (g *Galleries) ImageUpload(w http.ResponseWriter,
    r *http.Request) {
    // ... this is unchanged
    
    // Remove the code used to create a success alert and
    // render the EditView and replace it with the following.
    url, err := g.r.Get(EditGallery).URL("id",
        fmt.Sprintf("%%v", gallery.ID))
    if err != nil {
        http.Redirect(w, r, "/galleries", http.StatusFound)
        return
    }
    http.Redirect(w, r, url.Path, http.StatusFound)
}
```

Another side of this change is that whenever a user submits the image upload their URL will get changed back to the edit gallery URL, making it easy to copy/paste a working link.

# Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/16.5.2

Changes - book.usegolang.com/16.5.2-diff