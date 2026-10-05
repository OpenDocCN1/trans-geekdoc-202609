```
func Copy(dst Writer, src Reader) (written int64, err error)
```

The source is of the type Reader¹⁴, which is any type with a Read method that matches the following definition:

```
type Reader interface {
Read(p []byte) (n int, err error)
}
```

That means we can define our Create method for the image service using the io.Reader interface. We will be doing this inside of a new source file we will be creating for our image-specific code. It will be inside the models package.

```
$ atom models/images.go
```

```
package models

// We will need some of these imports later
import (
  "fmt"
  "io"
  "os"
  "path/filepath"
)

t ImageService interface {
  Create(galleryID uint, r io.Reader, filename string) error
}
```

While we could make our second argument, the io.Reader, more specific but that generally isn't a great idea. Our Create method doesn't need anything more than a data type with the Read method in order to create a new image, so by using a more specific data type in our Create method we would be writing code that works in fewer use cases with no real benefit.

> ¹⁴https://golang.org/pkg/io/#Reader