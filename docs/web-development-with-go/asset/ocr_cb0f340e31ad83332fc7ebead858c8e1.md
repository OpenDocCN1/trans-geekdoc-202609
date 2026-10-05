```
$ atom models/images.go
```

We are going to add a Delete method to our ImageService. Our Delete method will accept an image as its only argument, and this is meant to define the image being deleted. The method will return an error if something goes wrong.

```
type ImageService interface {
  Create(galleryID uint, r io.Reader, filename string) error
  ByGalleryID(galleryID uint) ([]Image, error)
  Delete(i *Image) error
}
```

Now we are going to implement this method using the Remove function² from the os package. This function can be used to remove a specific file or directory. That means all we need to do is call the Remove function with the relative path of our image.

```
func (is *imageService) Delete(i *Image) error {
  return os.Remove(i.RelativePath())
}
```

After that we need to introduce a controller to handle any incoming image deletion requests. Open up the galleries controller.

```
$ atom controllers/galleries.go
```

We are going to name this method ImageDelete, and it will start off very similar to our ImageUpload method - we will look up the gallery and verify the user has permission to edit it before moving to any new code.

> ²⁰https://golang.org/pkg/os/#Remove