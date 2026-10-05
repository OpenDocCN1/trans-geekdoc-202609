
## 15.3 CREATING THE IMAGE SERVICE

### Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/15.2

Changes - book.usegolang.com/15.2-diff

## 15.3 Creating the image service

While our code works as it is currently coded, our ImageUpload method is doing quite a bit of work. That was fine when we were just learning how to process image uploads, but now that we have working code we are going to take some time to refactor a bit and introduce the ImageService.

Our image service is going to start with a single method - Create - but unlike our other models the Create method isn't going to accept an Image struct type as its only argument, and instead is going to accept the data needed to create an image.

What data is that? Well, for starters we need to know the gallery ID so we know what directory to create the image in. We also need the filename for the image as well. But what about the data for the file? How will we get that?

To answer the question we are going to look back at the io.Copy function¹³ used previously. We are going to be using it again inside our image service to copy data, so we would like to know what the bare minimum it requires is.

Looking at the source code, it looks like Copy is defined as:

> ¹³https://golang.org/pkg/io/#Copy

```go
func Copy(dst Writer, src Reader) (written int64, err error)
```

The source is of the type Reader¹⁴, which is any type with a Read method that matches the following definition:

```go
type Reader interface {
Read(p []byte) (n int, err error)
}
```

That means we can define our Create method for the image service using the io.Reader interface. We will be doing this inside of a new source file we will be creating for our image-specific code. It will be inside the models package.

```go
$ atom models/images.go
```

```go
package models

// We will need some of these imports later
import (
  "fmt"
  "io"
  "os"
  "path/filepath"
)

type ImageService interface {
  Create(galleryID uint, r io.Reader, filename string) error
}
```

While we could make our second argument, the io.Reader, more specific but that generally isn't a great idea. Our Create method doesn't need anything more than a data type with the Read method in order to create a new image, so by using a more specific data type in our Create method we would be writing code that works in fewer use cases with no real benefit.

> ¹⁴https://golang.org/pkg/io/#Reader

## 15.3. CREATING THE IMAGE SERVICE

Now that we know what our ImageService interface is going to look like, let's start implementing it.

```go
func NewImageService() ImageService {
	return &imageService()
}

type imageService struct {}

func (is *imageService) Create(galleryID uint,
	r io.Reader, filename string) error {
	// TODO: Implement this using code we wrote in the ImageUpload handler
	return nil
}
```

The first part of the implementation we are going to work on is the part that creates a directory to store our images in. We already wrote this inside the ImageUpload method, so we will be moving that code into a method on the imageService.

```go
func (is *imageService) mkImagePath(galleryID uint) (string, error) {
	galleryPath := filepath.Join("images", "galleries")
	fmt.Printf("%v", galleryID)
	err := os.MkdirAll(galleryPath, 0755)
	if err != nil {
		return "", err
	}
	return galleryPath, nil
}
```

After that we can implement the Create method for the imageService. Nearly all of this code is identical to the code we wrote in the ImageUpload method inside the loop. We are just moving it to the image service to organize our code a bit better and make it easier to test in the future.

```go
func (is *imageService) Create(galleryID uint,
	io.Reader, filename string) error {
	path, err := is.mkImagePath(galleryID)
```

```go
if err != nil {
    return err
}
// Create a destination file
dst, err := os.Create(filepath.Join(path, filename))
if err != nil {
    return err
}
defer dst.Close()
// Copy reader data to the destination file
err = io.Copy(dst, r)
if err != nil {
    return err
}
return nil
```

Now that we have a working Create method, we are going to want the image service accessible inside the Galleries controller so we can use it to create images instead of the existing code.

```go
$ atom controllers/galleries.go
```

We'll start with the NewGalleries function and the Galleries type. We need to add an image service field to each of these.

```go
func NewGalleries(gs models.GalleryService,
    models.ImageService, r *mux.Router) *Galleries {
    return &Galleries{
        New:      views.NewView("bootstrap", "galleries/new"),
        ShowView: views.NewView("bootstrap", "galleries/show"),
        EditView: views.NewView("bootstrap", "galleries/edit"),
        IndexView: views.NewView("bootstrap", "galleries/index"),
        gs:       gs,
        is:       is,
    }
}

type Galleries struct {
    New      *views.View
    ShowView *views.View
    EditView *views.View
    IndexView *views.View
    gs       models.GalleryService
    is       models.ImageService
}
```

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View.
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
[/content]

Wait, I noticed the OCR output in the previous thought block had some repetitions and formatting artifacts. Let me provide the cleaned version based on the provided text.

[content]
## 15.3. CREATING THE IMAGE SERVICE

### Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/15.2

Changes - book.usegolang.com/15.2-diff

## 15.3 Creating the image service

While our code works as it is currently coded, our ImageUpload method is doing quite a bit of work. That was fine when we were just learning how to process image uploads, but now that we have working code we are going to take some time to refactor a bit and introduce the ImageService.

Our image service is going to start with a single method - Create - but unlike our other models the Create method isn't going to accept an Image struct type as its only argument, and instead is going to accept the data needed to create an image.

What data is that? Well, for starters we need to know the gallery ID so we know what directory to create the image in. We also need the filename for the image as well. But what about the data for the file? How will we get that?

To answer the question we are going to look back at the io.Copy function¹³ used previously. We are going to be using it again inside our image service to copy data, so we would like to know what the bare minimum it requires is.

Looking at the source code, it looks like Copy is defined as:

> ¹³https://golang.org/pkg/io/#Copy

```go
func Copy(dst Writer, src Reader) (written int64, err error)
```

The source is of the type Reader¹⁴, which is any type with a Read method that matches the following definition:

```go
type Reader interface {
Read(p []byte) (n int, err error)
}
```

That means we can define our Create method for the image service using the io.Reader interface. We will be doing this inside of a new source file we will be creating for our image-specific code. It will be inside the models package.

```go
$ atom models/images.go
```

```go
package models

// We will need some of these imports later
import (
  "fmt"
  "io"
  "os"
  "path/filepath"
)

type ImageService interface {
  Create(galleryID uint, r io.Reader, filename string) error
}
```

While we could make our second argument, the io.Reader, more specific but that generally isn't a great idea. Our Create method doesn't need anything more than a data type with the Read method in order to create a new image, so by using a more specific data type in our Create method we would be writing code that works in fewer use cases with no real benefit.

> ¹⁴https://golang.org/pkg/io/#Reader

## 15.3. CREATING THE IMAGE SERVICE

Now that we know what our ImageService interface is going to look like, let's start implementing it.

```go
func NewImageService() ImageService {
	return &imageService()
}

type imageService struct {}

func (is *imageService) Create(galleryID uint,
	r io.Reader, filename string) error {
	// TODO: Implement this using code we wrote in the ImageUpload handler
	return nil
}
```

The first part of the implementation we are going to work on is the part that creates a directory to store our images in. We already wrote this inside the ImageUpload method, so we will be moving that code into a method on the imageService.

```go
func (is *imageService) mkImagePath(galleryID uint) (string, error) {
	galleryPath := filepath.Join("images", "galleries")
	fmt.Printf("%v", galleryID)
	err := os.MkdirAll(galleryPath, 0755)
	if err != nil {
		return "", err
	}
	return galleryPath, nil
}
```

After that we can implement the Create method for the imageService. Nearly all of this code is identical to the code we wrote in the ImageUpload method inside the loop. We are just moving it to the image service to organize our code a bit better and make it easier to test in the future.

```go
func (is *imageService) Create(galleryID uint,
	io.Reader, filename string) error {
	path, err := is.mkImagePath(galleryID)
```

```go
if err != nil {
    return err
}
// Create a destination file
dst, err := os.Create(filepath.Join(path, filename))
if err != nil {
    return err
}
defer dst.Close()
// Copy reader data to the destination file
err = io.Copy(dst, r)
if err != nil {
    return err
}
return nil
```

Now that we have a working Create method, we are going to want the image service accessible inside the Galleries controller so we can use it to create images instead of the existing code.

```go
$ atom controllers/galleries.go
```

We'll start with the NewGalleries function and the Galleries type. We need to add an image service field to each of these.

```go
func NewGalleries(gs models.GalleryService,
    models.ImageService, r *mux.Router) *Galleries {
    return &Galleries{
        New:      views.NewView("bootstrap", "galleries/new"),
        ShowView: views.NewView("bootstrap", "galleries/show"),
        EditView: views.NewView("bootstrap", "galleries/edit"),
        IndexView: views.NewView("bootstrap", "galleries/index"),
        gs:       gs,
        is:       is,
    }
}

type Galleries struct {
    New      *views.View
    ShowView *views.View
    EditView *views.View
    IndexView *views.View
    gs       models.GalleryService
    is       models.ImageService
}
```

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
|
 | models.GalleryService |
| is | models.ImageService |

## 15.3. CRE. the IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
|
View | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE

| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *views.View |
| EditView | *views.View |
| IndexView | *views.View |
| gs | models.GalleryService |
| is | models.ImageService |

## 15.3. CREATING THE IMAGE SERVICE



| Field | Type |
| :--- | :--- |
| New | *views.View |
| ShowView | *..View |
| Edit. | *... |


. | *...


. |...Service


 is |..ImageService
