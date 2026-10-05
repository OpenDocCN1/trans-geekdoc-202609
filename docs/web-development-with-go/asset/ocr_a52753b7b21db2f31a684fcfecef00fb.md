# CHAPTER 14. CREATING THE GALLERY RESOURCE

```
type GalleryDB interface {
    ByID(id uint) (*Gallery, error)
    Create(gallery *Gallery) error
}
```

Our BID method is to accept an unsigned integer for its id argument, and then will return either the gallery requested or an error. The errors possible are the same as the errors with the UserDB interface, but it is a good idea to document that here as well.

Next we need to implement this method on our galleryGorm type.

```
func (gg *galleryGorm) ByID(id uint) (*Gallery, error) {
    var gallery Gallery
    db := gg.Where("id = ?", id)
    err := first(db, &gallery)
    if err != nil {
        return nil, err
    }
    return &gallery, nil
}
```

As mentioned early, the ByID method is nearly identical to the one we implement for our userGorm type, but this uses a Gallery instead of a User variable. When we call the first method, which subsequently calls the First method provided by GORM, the type of this variable will be used to determine what table in our database we access. We don't see that code because it happens inside the gorm package, but that is how our code is deciding which database table to query.

The last thing we are going to do in this section is update our Show method on our galleries controller to look up a real gallery and render it.

```
$ atom controllers/galleries.go
```